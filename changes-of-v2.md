---
layout: layout
title: Changes of Version 2
---

This is the documentation of changes in Serverspec/Specinfra v2.

---

## Changes of version 2

### RSpec 3 support

Serverspec v2 supports RSpec 3 and does not support RSpec 2 any more.

---

### SpecInfra renamed to Specinfra

`SpecInfra`, the base library of Serverspec, has been renamed to `Specinfra`.

---
### Backward Compatibility

Almost of Serverspec test code you wrote for v1 should  work with v2, but some matchers don't work.

---

### Backward Incompatibility

#### Obsoleted matchers

##### match\_md5checksum, match\_sha256checksum, return\_stdout, return\_stderr, return\_exit\_status matchers are obsoleted

You can't write test code like this anymore.

```ruby
describe command('ls /tmp') do
  it { should return_stdout 'foo' }
  it { should return_stderr 'bar' }
  it { should return_exit_status 0 }
end
```

```ruby
describe file('/etc/services') do
  it { should match_md5checksum('fdcb69b5c0e9beb7d392fbc458bc6beb')
  it { should match_sha256sum('17feb8dc0817056a963c2861052d670b642c61f5625fae1fd59a2022be1dbb5b') }
end
```

Instead, you must write test code like this.

```ruby
describe command('ls /tmp') do
  its(:stdout) { should eq "foo\n" }
  its(:stderr) { should match /bar/ }
  its(:exit_status) { should eq 0 }
end
```

```ruby
describe file('/etc/services') do
  its(:md5sum)    { should eq 'fdcb69b5c0e9beb7d392fbc458bc6beb' }
  its(:sha256sum) { should eq '17feb8dc0817056a963c2861052d670b642c61f5625fae1fd59a2022be1dbb5b' }
end
```

#### spec_helper.rb incompatible

spec\_helper.rb does not have backward compatibility. So you should re-generate spec\_helper.rb by serverspec-init and check it.

#### Backend helper and DetectOS helper have been removed

In version 1, you need to include `SpecInfra::Helper::_backend_type_` `SpecInfra::Helper::DetectOS` to detect the os of target hosts like this.

```ruby
require 'serverspec'
include SpecInfra::Helper::Ssh
include SpecInfra::Helper::DetectOS
```

In version 2, you can specify backend type with `set :backend, :type` and auto detection is default behavior, so don't include `SpecInfra::Helper::_backend_type_` and `Specinfra::Helper::DetectOS`. 

```ruby
require 'serverspec'
# Set backend type
set :backend, :ssh
# Don't include Specinfra::Helper::DetectOS
```

#### sudo_prompt has been removed

Specinfra sets prompt internally by `-p` option of sudo command now. So we don't need set `sudo_prompt` by `RSpec.configure` or `Specinfra.configuration`.


#### os helper command behavior

The helper command `os` which returns OS infomation of target hosts has been changed in two point.

 * Return OS family in `small letters`
 * Return `release number` correctly

In v1, `os` command returns OS information like this.

```ruby
irb(main):004:0> os
=> {:family=>"FreeBSD10", :release=>nil, :arch=>"x86_64"}
```

In v2, `os` command returns OS information like this.

```ruby
irb(main):004:0> os
=> {:family=>"freebsd", :release=>"10", :arch=>"x86_64"}
```

#### PATH environment variable setting

In v1, `$PATH` is appended to your path configuration automatically, so you set paths excluding `$PATH` like this.

```ruby
RSpec.configure do |c|
  c.path = '/sbin:/usr/local/sbin'
end

# Or

Specinfra.configuration.path = '/sbin:/usr/local/sbin'
```

In v2, you must set `$PATH` in path configuration.

```ruby
set :path, '/sbin:/usr/local/sbin:$PATH'
```

(This is the syntax sugar of Specinfra.configuration. I will explain it later.)

Thanks to this change, you can change the path order like this.

```ruby
set :path, '$PATH:/sbin:/usr/local/sbin'
```

---

### New features

#### Syntax sugar of Specinfra.configuration

In v1, you can set configuration parameters and values like this.

```ruby
# Through RSpec.configure
RSpec.configure |c|
  c.host = 'target-host-name'
end

# Or call Specinfra.configuration directly
Specinfra.configuration.host = 'target-host-name'
```

In v2, you can set configuration parameters and values like this.

```ruby
set :host, 'target-host-name'
```

#### SSH settings

In v1, you must create Net::SSH object by yourself and set to `c.ssh` like this.

```ruby
RSpec.configure do |c|
  c.ssh = Net::SSH.start('host.example.jp', 'user', :port => 2222)
end
```

In v2, you can set SSH settings like this.

```ruby
set :host, 'host.example.jp'
set :ssh_options, :user => 'user', :port => 2222
```

#### Environment Variables

You can set any environment variables like this.

```ruby
set :env, :LANG => 'C', :LC_MESSAGES => 'C'
```

Note: In the case of SSH, environment variables should be accepted by `AcceptEnv` directive of `sshd_config`.
