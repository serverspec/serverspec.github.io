---
layout: layout
title: home
---

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
Input target host name: www.example.jp

Select OS type of target host:

  1) Red Hat
  2) Debian
  3) Gentoo
  4) Solaris
  5) None

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

You should create ~/.ssh/config like this before running tests because serverspec tests servers through SSH access.

```
Host *.example.jp
   User root
   IdentityFile ~/.ssh/id_rsa
   StrictHostKeyChecking no
   UserKnownHostsFile /dev/null
```

Run tests.

```
$ rake spec
/usr/bin/ruby -S rspec spec/www.example.jp/httpd_spec.rb
......

Finished in 0.99715 seconds
6 examples, 0 failures
```
