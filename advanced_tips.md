---
layout: layout
title: Advanced Tips
---

## How to share serverspec tests among hosts

``serverspec-init`` generates template files like this.

```
|-- Rakefile
`-- spec
    |-- spec_helper.rb
    `-- www.example.jp
        `-- httpd_spec.rb
```

This directory structure forces you to write tests per host.

But you can write tests per role like this.

```
|-- Rakefile
`-- spec
    |-- app
    |   `-- ruby_spec.rb
    |-- base
    |   `-- users_and_groups_spec.rb
    |-- db
    |   `-- mysql_spec.rb
    |-- proxy
    |   `-- nginx_spec.rb
    `-- spec_helper.rb
```

You should write the relationship of hosts to roles in Rakefile like this.

```ruby
require 'rake'
require 'rspec/core/rake_task'
 
hosts = [
  {
    :name  => 'proxy001.example.jp',
    :roles => %w( base proxy ),
  },
  {
    :name  => 'proxy002.example.jp',
    :roles => %w( base proxy ),
  },
  {
    :name  => 'app001.example.jp',
    :roles => %w( base app ),
  },
  {
    :name  => 'app002.example.jp',
    :roles => %w( base app ),
  },
  {
    :name  => 'db001.example.jp',
    :roles => %w( base db ),
  },
  {
    :name  => 'db002.example.jp',
    :roles => %w( base db ),
  },
]
 
hosts = hosts.map do |host|
  {
    :name       => host[:name],
    :short_name => host[:name].split('.')[0],
    :roles      => host[:roles],
  }
end
 
desc "Run serverspec to all hosts"
task :serverspec => 'serverspec:all'
 
namespace :serverspec do
  task :all => hosts.map {|h| 'serverspec:' + h[:short_name] }
  hosts.each do |host|
    desc "Run serverspec to #{host[:name]}"
    RSpec::Core::RakeTask.new(host[:short_name].to_sym) do |t|
      ENV['TARGET_HOST'] = host[:name]
      t.pattern = 'spec/{' + host[:roles].join(',') + '}/*_spec.rb'
    end
  end
end
```

And you should change spec_helper.rb like this.

```ruby
require 'serverspec'
require 'net/ssh'
 
include Serverspec::Helper::Ssh
include Serverspec::Helper::DetectOS
 
RSpec.configure do |c|
  c.host  = ENV['TARGET_HOST']
  options = Net::SSH::Config.for(c.host)
  user    = options[:user] || Etc.getlogin
  c.ssh   = Net::SSH.start(c.host, user, options)
  c.os    = backend.check_os
end
```

----

## How to use host specific properties

Serverspec supports a simple mechanism to handle host specific properties.

This example assumes that host specific properties are in YAML file.

```yaml
db001.example.jp:
  :roles:
    - base
    - db
  :server_id: 101
db002.example.jp:
  :roles:
    - base
    - db
  :server_id: 102
```

You can write Rakefile for role separeted tests like this with the YAML file.

```ruby
require 'rake'
require 'rspec/core/rake_task'
require 'yaml'
 
properties = YAML.load_file('properties.yml')
 
desc "Run serverspec to all hosts"
task :serverspec => 'serverspec:all'
 
namespace :serverspec do
  task :all => properties.keys.map {|key| 'serverspec:' + key.split('.')[0] }
  properties.keys.each do |key|
    desc "Run serverspec to #{key}"
    RSpec::Core::RakeTask.new(key.split('.')[0].to_sym) do |t|
      ENV['TARGET_HOST'] = key
      t.pattern = 'spec/{' + properties[key][:roles].join(',') + '}/*_spec.rb'
    end
  end
end
```

You can write spec_helper.rb to set host specific properties with ``set_property``.

```ruby
require 'serverspec'
require 'pathname'
require 'net/ssh'
require 'yaml'
 
include Serverspec::Helper::Ssh
include Serverspec::Helper::DetectOS
include Serverspec::Helper::Properties
 
properties = YAML.load_file('properties.yml')
 
RSpec.configure do |c|
  c.host  = ENV['TARGET_HOST']
  set_property properties[c.host]
  options = Net::SSH::Config.for(c.host)
  user    = options[:user] || Etc.getlogin
  c.ssh   = Net::SSH.start(c.host, user, options)
  c.os    = backend.check_os
end
```

And you can use host specific properties with ``property`` like this.

```ruby
require 'spec_helper'
 
describe file('/etc/my.cnf') do
  it { should contain "server-id = #{property[:server_id]}" }
end
```


----

## PATH environment variable

You can add PATH environment variable in spec_helper.rb or other places like this.

```ruby
RSpec.configure do |c|
  c.path = '/sbin:/usr/sbin'
  ...
```

In this case, a command is expanded to ``PATH=/sbin:/usr/sbin command``.

----

## Block scoped PATH environment variable

**This feature is experimental.So this may be changed in the future.**

You can also set PATH environment variable only in a block scope like this.

```ruby
describe package('jekyll') do
  let(:path) { '/usr/local/rbenv/shims' }
  it { should be_installed.by('gem') }
end
```

----

## Block scoped pre_command parameter

**This feature is experimental.So this may be changed in the future.**

You can set pre_command parameter like this.

```ruby
describe service('httpd') do
  let(:pre_command) { 'source ~/.zshrc' }
  it { should be_running }
end
```

In this case, a command is expanded to ``source ~/.zshrc && service httpd status``.

----

## Parallel execution

If you have a lot of hosts, running tests on all of them can take some
time. To speed up tests, they can be executed in parallel using a
process pool. One way is to use [xpool][]. Here is a minimal
``Rakefile`` that will maintain a pool of 10 processes to run tests:

```ruby
require 'rake'
require 'rspec/core/rake_task'
require 'xpool'

$PARALLEL = 10                  # How many parallel tasks should we run?

class BackgroundServerspecTask

  def run(verbose, command)
    puts command if verbose
    status = system(command)
    # Error handling can be done here
  end

end

class ServerspecTask < RSpec::Core::RakeTask

  @@pool = XPool.new $PARALLEL

  def self.shutdown
    @@pool.shutdown
  end

  def run_task(verbose)
    command = spec_command
    @@pool.schedule BackgroundServerspecTask.new, verbose, command
  end

end

ServerspecTask.new(:spec) do |t|
  t.pattern = 'spec/*/*_spec.rb'
end

Kernel.at_exit do
  ServerspecTask.shutdown
end
```

[xpool]: https://github.com/robgleeson/xpool "xpool: lightweight process pool"

----

## How to control sudo

You can disable sudo completely like this.

```ruby
# In spec_helper.rb
RSpec.configure do |c|
  c.disable_sudo = true
  ...
```

----

Or you can disable sudo temporary like this.

```ruby
# In spec_helper.rb
RSpec.configure do |c|
  c.around :each, sudo: false do |example|
    c.disable_sudo = true
    example.run
    c.disable_sudo = false
  end
  ...
```

----

```ruby
# In xxxxx_spec.rb
describe command('whoami'), :sudo => false do
  it { should return_stdout 'vagrant' }
end

describe command('whoami') do
  it { should return_stdout 'root' }
end
```

----

Another way to disable sudo temporary.

```ruby
describe command('whoami') do
  let(:disable_sudo) { true }
  it { should return_stdout 'vagrant' }
end

describe command('whoami') do
  it { should return_stdout 'root' }
end
```