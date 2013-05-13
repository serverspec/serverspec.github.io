---
layout: layout
title: home
---

## About

With serverspec, you can write RSpec tests for checking your servers are provisioned correctly.

Serverspec tests your servers' **actual state**  through **SSH access**, so you don't need to install any agent softwares on your servers and can use any provisioning tools, [Puppet](https://puppetlabs.com/), [Chef](http://www.opscode.com/chef/), [CFEngine](http://cfengine.com/) and so on.

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
Select a backend type:

  1) SSH
  2) Exec (local)

Select number: 1

Input target host name: www.example.jp

Select OS type of target host:

  1) Auto Detect
  2) Red Hat
  3) Debian
  4) Gentoo
  5) Solaris

Select number: 1

 + spec/
 + spec/www.example.jp/
 + spec/www.example.jp/httpd_spec.rb
 + spec/spec_helper.rb
 + Rakefile
```


spec/www.example.jp/httpd_spec.rb is a sample spec file and its content is like this.

```ruby
require 'spec_helper'

describe 'httpd' do
  it { should be_installed }
  it { should be_enabled   }
  it { should be_running   }
end

describe 'port 80' do
  it { should be_listening }
end

describe '/etc/httpd/conf/httpd.conf' do
  it { should be_file }
  it { should contain "ServerName www.example.jp" }
end
```

You can write spec for testing servers like this.

Serverspec with SSH backend logs in to target servers as a user configured in ``~/.ssh/config`` or a current user.If you'd like to change the user, please edit the below line in ``spec/spec_helper.rb``.

```ruby
      user    = options[:user] || Etc.getlogin
```

Run tests.

```
$ rake spec
/usr/bin/ruby -S rspec spec/www.example.jp/httpd_spec.rb
......

Finished in 0.99715 seconds
6 examples, 0 failures
```
