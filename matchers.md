---
layout: layout
title: matchers
---

## Matchers

<nav>
  [Cron](#cron)
| [Commands](#commands)
| [Files and Directories](#files_and_directories)
| [Iptables](#iptables)
| [Packages](#packages)
| [Ports](#ports)
| [Services](#services)
| [Users and Groups](#user_and_groups)
</nav>

### <a name="cron">Cron</a>

Matchers for testing cron.

#### have\_cron\_entry

In order to test cron have a given entry exists, you should use **have_cron_entry** matcher.

```ruby
describe 'cron' do
  it { should have_cron_entry '* * * * * /usr/local/bin/foo' }
end
```

You can test a given user has the cron entry like this.

```ruby
describe 'cron' do
  it { should have_cron_entry('* * * * * /usr/local/bin/foo').with_user('mizzy') }
end
```

----

### <a name="commands">Commands</a>

Matchers for testing executing command result.

#### return_stdout

In order to test a given command returns correct stdout, you should use **return_stdout** matcher.

```ruby
describe 'whoami' do
  it { should return_stdout 'root' }
end
```

You can also use a regular expression.

```ruby
describe 'cat /etc/resolv.conf' do
  it { should return_stdout /8\.8\.8\.8/ }
end
```

#### return_stderr

In order to test a given command returns correct stderr, you should use **return_stderr** matcher.

```ruby
describe 'ls /foo' do
  it { should return_stderr 'ls: /foo: No such file or directory' }
end
```

You can also use a regular expression.

```ruby
describe 'ls /foo' do
  it { should return_stderr /No such file or directory/ }
end
```

#### return\_exit\_status

In order to test a given command returns correct exit status, you should use **return\_exit\_status** matcher.

```ruby
describe 'ls /tmp' do
  it { should return_exit_status 0 }
end
```

#### get_stdout

**Warning! get\_stdout will be deprecated. Please use return_stdout instead**

In order to test a given command gets correct stdout, you should use **get_stdout** matcher.

```ruby
describe 'whoami' do
  it { should get_stdout 'root' }
end
```



----

### <a name="files_and_directories">Files/Directories</a>

Matchers for testing files and directories.

#### be_file

In order to test a subject exists as a file, you should use **be_file** matcher.

```ruby
describe '/etc/passwd' do
  it { should be_file }
end
```

#### be_directory

In order to test a subject exists as a directory, you should use **be_directory** matcher.

```ruby
describe '/var/log/httpd' do
  it { should be_directory }
end
```

#### contain

In order to test a file contains a given string, you should use **contain** mathcer.

```ruby
describe '/etc/httpd/conf/httpd.conf' do
  it { should contain 'ServerName www.example.jp' }
end
```

You can test a file contains a given string within a given range.

```ruby
describe 'Gemfile' do
  # test 'rspec' exists between "group :test do" and "end".
  it { should contain('rspec').from(/^group :test do/).to(/^end/) }

  # test 'rspec' exists after "group :test do".
  it { should contain('rspec').after(/^group :test do/) }

  # test 'rspec' exists before "end".
  it { should contain('rspec').before(/^end/) }
end

```

#### be_mode

In order to test a subject is set to given mode, you should use **be_mode** matcher.

```ruby
describe '/etc/sudoers' do
  it { should be_mode 440 }
end
```

#### be\_owned\_by

In order to test a subject is owned by a given user, you should use **be\_owned\_by** matcher.

```ruby
describe '/etc/sudoers' do
  it { should be_owned_by 'root' }
end
```

#### be\_grouped\_into

In order to test a subject is grouped into a given group, you should use **be\_grouped\_into** matcher.

```ruby
describe '/etc/sudoers' do
  it { should be_grouped_into 'wheel' }
end
```

#### be\_linked\_to

In order to test a subject is linked to a given file or directory, you should use **be\_linked\_to** matcher.

```ruby
describe '/etc/system-release' do
  it { should be_linked_to '/etc/redhat-release' }
end
```

#### be_readable

In order to test a subject is readable, you should use **be\_readable** matcher.

```ruby
describe '/etc/sudoers' do
  it { should be_readable }
end
```

You can also test a subject is readable by owner, group members or others.

```ruby
describe '/etc/sudoers' do
  it { should be_readable.by('owner') }
  it { should be_readable.by('group') }
  it { should be_readable.by('others') }
end
```

#### be_writable

In order to test a subject is writable, you should use **be\_writable** matcher.

```ruby
describe '/etc/sudoers' do
  it { should be_writable }
end
```

You can also test a subject is writable by owner, group members or others.

```ruby
describe '/etc/sudoers' do
  it { should be_writable.by('owner') }
  it { should be_writable.by('group') }
  it { should be_writable.by('others') }
end
```

#### be_executable

In order to test a subject is executable, you should use **be\_executable** matcher.

```ruby
describe '/etc/sudoers' do
  it { should be_executable }
end
```

You can also test a subject is executable by owner, group members or others.

```ruby
describe '/etc/sudoers' do
  it { should be_executable.by('owner') }
  it { should be_executable.by('group') }
  it { should be_executable.by('others') }
end
```

----

### <a name="iptables">Iptables</a>

Matchers for testing iptables.

#### have\_iptables\_rule

In order to test iptables has a given rule, you should use **have\_iptables\_rule** matcher.

```ruby
describe 'iptables' do
  it { should have_iptables_rule('-P INPUT ACCEPT') }
end
```

You can give a table name and a chain name like this.

```ruby
describe 'iptables' do
  it { should have_iptables_rule('-P INPUT ACCEPT').with_table('mangle').with_chain('INPUT') }
end
```

----

### <a name="packages">Packages</a>

Matchers for testing packages.

#### be_installed

In order to test a package is installed, you should use **be_installed** matcher.

```ruby
describe 'httpd' do
  it { should be_installed }
end
```

You can also test a given version of gem is installed.

```ruby
describe 'jekyll' do
  it { should be_installed.by('gem').with_version('0.12.1') }
end
```


#### be\_installed\_by\_gem

**Warning! be\_installed\_by\_gem will be deprecated. Please use be\_installed.by('gem') instead**

In order to test a gem is installed, you should use **be\_installed\_by\_gem** matcher.

```ruby
describe 'jekyll' do
  it { should be_installed_by_gem }
end
```

You can also test a given version of gem is installed.

```ruby
describe 'jekyll' do
  it { should be_installed_by_gem.with_version('0.12.1') }
end
```


----

### <a name="ports">Ports</a>

Matchers fo testing packages.

#### be_listening

In order to test a given port is listening, you should use **be_listening** matcher.

```ruby
describe 'port 80' do
  it { should be_listening }
end
```

----

### <a name="services">Services</a>

Matchers for testing services.

#### be_enabled

In order to test a given service is enabled(automatically start when OS booting up), you should use **be_enabled** matcher.

```ruby
describe 'ntpd' do
  it { should be_enabled }
end
```

#### be_running

In order to test a given service/process is running, you should use **be_running** matcher.

```ruby
describe 'ntpd' do
  it { should be_running }
end
```

You can test a given service/process is running under [supervisor](http://supervisord.org/).

```ruby
describe 'ntpd' do
  it { should be_running.under('supervisor') }
end
```

----
### <a name="users_and_groups">Users/Groups</a>

Matchers for testing users and groups.

#### be_user

In order to test a subject exists as a user, you should use **be_user** matcher.

```ruby
describe 'root' do
  it { should be_user }
end
```

#### be_group

In order to test a subject exists as a group, you should use **be_group** matcher.

```ruby
describe 'wheel' do
  it { should be_group }
end
```


#### belong\_to\_group

In order to test a user belongs to a given group, you should use **belong\_to\_group** matcher.

```ruby
describe 'apache' do
  it { should belong_to_group 'apache' }
end
```
