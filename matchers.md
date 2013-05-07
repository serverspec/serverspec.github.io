---
layout: layout
title: matchers
---

## Matchers

<nav>
  [Cron](#cron)
| [Commands](#commands)
| [Files and Directories](#files_and_directories)
| [Linux kernel parameters](#linux_kernel_parameters)
| [Networks](#networks)
| [Packages](#packages)
| [Ports](#ports)
| [SELinux](#selinux)
| [Services](#services)
| [Users and Groups](#users_and_groups)
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

#### be_mounted

In order to test a directory is mounted, you should use **be\_mounted** matcher.

```ruby
describe '/' do
  it { should be_mounted }
end
```

You can also test a directory is mounted with correct attributes.

```ruby
describe '/' do
  it { should be_mounted.with( :type => 'ext4' ) }
end

describe '/' do
  it { should be_mounted.with( :options => { :rw => true } ) }
end

describe '/' do
  it do
    should be_mounted.only_with(
      :device  => '/dev/mapper/VolGroup-lv_root',
      :type    => 'ext4',
      :options => {
        :rw   => true,
        :mode => 620,
      }
    )
  end
end
```

``only_with`` needs all attributes of the mounted directory.

----

### <a name="linux_kernel_parameters">Linux kernel parameters</a>

You can test Linux kernel parameters like this.

```ruby
describe 'Linux kernel parameters' do
  context 'net.ipv4.tcp_syncookies' do 
    its(:value) { should eq 1 }
  end

  context 'kernel.shmall' do
    its(:value) { should be >= 4294967296 }
  end

  context 'kernel.shmmax' do
    its(:value) { should be <= 68719476736 }
  end

  context 'kernel.osrelease' do
    its(:value) { should eq '2.6.32-131.0.15.el6.x86_64' }
  end

  context 'net.ipv4.tcp_wmem' do
    its(:value) { should match /4096\t16384\t4194304/ }
  end
end
```
----

### <a name="networks">Networks</a>

Matchers for testing network related settings.

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

#### be_resolvable

In order to test a host is resolvable on the target host, you should use **be_resolvable** matcher.

```ruby
describe 'serverspec.org' do
  it { should be_resolvable }
end

describe 'serverspec.org' do
  it { should be_resolvable.by('hosts') }
end

describe 'serverspec.org' do
  it { should be_resolvable.by('dns') }
end
```

#### be_reachable

In order to test a given host is network reachable, you should use **be_reachable** matcher.

```ruby
describe 'target.example.jp' do
  # ping
  it { should be_reachable }
  # tcp port 22
  it { should be_reachable.with( :port => 22 ) }
  # set protocol explicitly
  it { should be_reachable.with( :port => 22, :proto => 'tcp' ) }
  # udp port 53
  it { should be_reachable.with( :port => 53, :proto => 'udp' ) }
  # timeout setting (default is 5 seconds)
  it { should be_reachable.with( :port => 22, :proto => 'tcp', :timeout => 1 ) }
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
### <a name="selinux">SELinux</a>

Matchers for testing SELinux.

#### be\_disabled/be\_enforcing/be\_permissive

In order to test SELinux is a given mode, you should use **be\_disabled, be\_enforcing and be\_permissinve** matchers.

```ruby
### SELinux should be disabled
describe 'selinux' do
  it { should be_disabled }
end

### SELinux should be enforcing
describe 'selinux' do
  it { should be_enforcing }
end

### SELinux should be permissive
describe 'selinux' do
  it { should be_permissive }
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

#### have_uid

In order to test a user have a given uid, you should use **have_uid** matcher.

```ruby
describe 'root' do
  it { should have_uid 0 }
end
```

#### have\_home\_directory

In order to test a user have a given home directory, you should use **have\_home\_directory** matcher.

```ruby
describe 'root' do
  it { should have_home_directory '/root' }
end
```

#### have\_login\_shell

In order to test a user have a given login shell, you should use **have\_login\_shell** matcher.

```ruby
describe 'root' do
  it { should have_login_shell '/bin/bash' }
end
```

#### have\_authorized\_key

In order to test a have have a given authorized key, you should use **have\_authorized\_key** matcher.

```ruby
describe 'root' do
  it { should have_authorized_key 'ssh-rsa ABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGH foo@bar.local' }
end
```

#### have\_gid

In order to test a group have a given gid, you should use **have\_gid** matcher.

```ruby
describe 'root' do
  it { should have_gid 0 }
end
```
