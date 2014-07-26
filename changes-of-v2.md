---
layout: layout
title: Changes of Version 2
---

This is the documentation of changes in Serverspec/Specinfra v2 beta. **Serverspec/Specinfra v2 will be released at October 2014.**

## How to install version 2 beta

Now Serverspec verion 2 is beta. You can install beta version with `--pre` option.

```
$ gem install serverspec --pre
```

---

## Changes of version 2

### RSpec 3 support

Serverspec v2 supports RSpec 3 and does not support RSpec 2 any more.

---

### SpecInfra renamed to Specinfra

`SpecInfra`, the base library of Serverspec, has been renamed to `Specinfra`.

---
### Backward Compatibility

Serverspec test code you wrote for v1 should  work with v2.

---

### Backward Incompatibility

#### spec_helper.rb incompatible

spec\_helper.rb does not have backward compatibility. So you should re-generate spec\_helper.rb by serverspec-init and check it.

#### SpecInfra::Helper::DetectOS has been removed

In version 1, you need to include `SpecInfra::Helper::DetectOS` to detect the os of target hosts like this.

```ruby
require 'spec_helper'
include SpecInfra::Helper::Ssh
include SpecInfra::Helper::DetectOS
```

In version 2, auto detection is default behavior, so you don't need to include `Specinfra::Helper::DetectOS`. 

```ruby
require 'spec_helper'
include SpecInfra::Helper::Ssh
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

Specinfra.configuraion.path = '/sbin:/usr/local/sbin'
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
set :ssh_options, :user => 'user', port => 2222
```

#### Environment Variables

You can set any environment variables like this.

```ruby
set :env, :LANG => 'C', :LC_MESSAGES => 'C'
```

Note: In the case of SSH, environment variables should be accepted by `AcceptEnv` directive of `sshd_config`.
