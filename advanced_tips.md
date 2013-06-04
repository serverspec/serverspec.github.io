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
  c.os    = backend(Serverspec::Commands::Base).check_os
end
```

----

## How to use host specific attributes

Serverspec supports a simple mechanism to handle host specific attributes.

This example assumes that host specific attributes are in YAML file.

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
 
attributes = YAML.load_file('attributes.yml')
 
desc "Run serverspec to all hosts"
task :serverspec => 'serverspec:all'
 
namespace :serverspec do
  task :all => attributes.keys.map {|key| 'serverspec:' + key.split('.')[0] }
  attributes.keys.each do |key|
    desc "Run serverspec to #{key}"
    RSpec::Core::RakeTask.new(key.split('.')[0].to_sym) do |t|
      ENV['TARGET_HOST'] = key
      t.pattern = 'spec/{' + attributes[key][:roles].join(',') + '}/*_spec.rb'
    end
  end
end
```

You can write spec_helper.rb to set host specific attributes with ``attr_set``.

```
require 'serverspec'
require 'pathname'
require 'net/ssh'
require 'yaml'
 
include Serverspec::Helper::Ssh
include Serverspec::Helper::DetectOS
include Serverspec::Helper::Attributes
 
attributes = YAML.load_file('attributes.yml')
 
RSpec.configure do |c|
  c.host  = ENV['TARGET_HOST']
  attr_set attributes[c.host]
  options = Net::SSH::Config.for(c.host)
  user    = options[:user] || Etc.getlogin
  c.ssh   = Net::SSH.start(c.host, user, options)
  c.os    = backend(Serverspec::Commands::Base).check_os
end
```

And you can use host specific attributes with ``attr`` like this.

```ruby
require 'spec_helper'
 
describe file('/etc/my.cnf') do
  it { should contain "server-id = #{attr[:server_id]}" }
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
