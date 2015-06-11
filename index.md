---
layout: layout
title: Home
---
## About V2

**Serverspec/Specinfra v2 has been just released.** [See the document about v2](changes-of-v2.html).

## About

With Serverspec, you can write RSpec tests for checking your servers are configured correctly.

Serverspec tests your servers' **actual state** by **executing command locally, via SSH, via WinRM, via Docker API and so on**. So you don't need to install any agent softwares on your servers and can use any configuration management tools, [Puppet](https://puppetlabs.com/), [Ansible](http://www.ansible.com/), [CFEngine](http://cfengine.com/), [Itamae](http://itamae.kitchen) and so on.

**But the true aim of Serverspec is to help refactoring infrastructure code.**

----


## Installation

Add this line to your application's Gemfile:

    gem 'serverspec'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install serverspec

----

## Getting Started

```
$ serverspec-init
Select OS type:

  1) UN*X
  2) Windows

Select number: 1

Select a backend type:

  1) SSH
  2) Exec (local)

Select number: 1

Vagrant instance y/n: n
Input target host name: www.example.jp
 + spec/
 + spec/www.example.jp/
 + spec/www.example.jp/sample_spec.rb
 + spec/spec_helper.rb
 + Rakefile
 + .rspec
 ```

spec/www.example.jp/sample_spec.rb is a sample spec file and its content is like this.

```ruby
require 'spec_helper'

describe package('httpd'), :if => os[:family] == 'redhat' do
  it { should be_installed }
end

describe package('apache2'), :if => os[:family] == 'ubuntu' do
  it { should be_installed }
end

describe service('httpd'), :if => os[:family] == 'redhat' do
  it { should be_enabled }
  it { should be_running }
end

describe service('apache2'), :if => os[:family] == 'ubuntu' do
  it { should be_enabled }
  it { should be_running }
end

describe service('org.apache.httpd'), :if => os[:family] == 'darwin' do
  it { should be_enabled }
  it { should be_running }
end

describe port(80) do
  it { should be_listening }
end
```

You can write spec for testing servers like this.

Serverspec with SSH backend logs in to target servers as a user configured in ``~/.ssh/config`` or a current user. If you'd like to change the user, please edit the below line in ``spec/spec_helper.rb``.

```ruby
options[:user] ||= Etc.getlogin
```

Run tests.

```
$ rake spec
/usr/bin/ruby -S rspec spec/www.example.jp/sample_spec.rb

Package "httpd"
  should be installed

Service "httpd"
  should be enabled
  should be running

Port "80"
  should be listening

Finished in 0.21091 seconds (files took 6.37 seconds to load)
4 examples, 0 failures
```

## Remark

`serverspec` test suites are meant to be run against a single machine (or docker container). 

In other words, you should not try to issue a single `rspec` command that would harvest and run tests against multiple machines or containers. You need to issue one `rspec`command for each of them.
