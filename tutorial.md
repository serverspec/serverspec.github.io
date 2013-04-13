---
layout: layout
title: tutorial
---

<nav>
  [Writing tests](#writing_tests)
| [Multi OS support](#multi_os_support)
| [Sudo password support](#sudo_password_support)
</nav>

## Tutorial

### <a name="writing_tests">Writing tests</a>

#### Basic structure of test files

Test files must be placed under the directory which name matches the target host name like this.

```
spec/target.example.jp/http_spec.rb
```

You can write a test file like this.

```ruby
require 'spec_helper'

decribe '<name of the resource being tested>' do
  # your tests ...
end
```

See details on [Matchers](/matchers.html).

----

#### <a name="multi_os_support">Multi OS support</a>

Serverspec is supporting Red Hat based OS, Debian based OS, Gentoo and Solaris now.

Serverspec can detect target host's OS automatically.

If you'd like to set target host's OS explicitly, you should include `Serverspec::Helper::OSName` like this.

```ruby
require 'serverspec'
require 'pathname'
require 'net/ssh'

RSpec.configure do |c|
  # Include backend helper
  c.include(Serverspec::Helper::Ssh)
  # Include OS helper
  c.include(Serverspec::Helper::Debian)
  # Add SSH before hook in case you use the SSH backend
  # (not required for the Exec backend)
  c.before do
    host  = File.basename(Pathname.new(example.metadata[:location]).dirname)
    if c.host != host
      c.ssh.close if c.ssh
      c.host  = host
      options = Net::SSH::Config.for(c.host)
      user    = options[:user] || Etc.getlogin
      c.ssh   = Net::SSH.start(c.host, user, options)
    end
  end
end
```

You can select **Serverspec::Helper::RedHat**, **Serverspec::Helper::Debian**, **Serverspec::Helper::Gentoo** or **Serverspec::Helper::Solaris**.

----

#### <a name="sudo_password_support">Sudo password support</a>

If you log into servers as non-root user, serverspec add "sudo" in front of the command.You can specify sudo password like this.

```
$ SUDO_PASSWORD=xxxxxxxx rake spec
```

If you'd like to give sudo password by another way, please customize spec_helper.rb.
