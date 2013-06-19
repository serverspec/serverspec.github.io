### <a name="file">file</a>

File and directory resource type.

#### be_file

In order to test a subject exists as a file, you should use **be_file** matcher.

```ruby
describe file('/etc/passwd') do
  it { should be_file }
end
```

#### be_directory

In order to test a subject exists as a directory, you should use **be_directory** matcher.

```ruby
describe file('/var/log/httpd') do
  it { should be_directory }
end
```

#### be_socket

In order to test a subject exists as a socket, you should use **be_scoket** matcher.

```ruby
describe file('/var/run/unicorn.sock') do
  it { should be_socket }
end
```

#### contain

In order to test a file contains a given string, you should use **contain** mathcer.

```ruby
describe file('/etc/httpd/conf/httpd.conf') do
  it { should contain 'ServerName www.example.jp' }
end
```

You can test a file contains a given string within a given range.

```ruby
describe file('Gemfile') do
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
describe file('/etc/sudoers') do
  it { should be_mode 440 }
end
```

#### be\_owned\_by

In order to test a subject is owned by a given user, you should use **be\_owned\_by** matcher.

```ruby
describe file('/etc/sudoers') do
  it { should be_owned_by 'root' }
end
```

#### be\_grouped\_into

In order to test a subject is grouped into a given group, you should use **be\_grouped\_into** matcher.

```ruby
describe file('/etc/sudoers') do
  it { should be_grouped_into 'wheel' }
end
```

#### be\_linked\_to

In order to test a subject is linked to a given file or directory, you should use **be\_linked\_to** matcher.

```ruby
describe file('/etc/system-release') do
  it { should be_linked_to '/etc/redhat-release' }
end
```

#### be_readable

In order to test a subject is readable, you should use **be\_readable** matcher.

```ruby
describe file('/etc/sudoers') do
  it { should be_readable }
end
```

You can also test a subject is readable by owner, group members, others or a specific user.

```ruby
describe file('/etc/sudoers') do
  it { should be_readable.by('owner') }
  it { should be_readable.by('group') }
  it { should be_readable.by('others') }
  it { should be_readable.by_user('apache') }
end
```

#### be_writable

In order to test a subject is writable, you should use **be\_writable** matcher.

```ruby
describe file('/etc/sudoers') do
  it { should be_writable }
end
```

You can also test a subject is writable by owner, group members, others or a specific user.

```ruby
describe file('/etc/sudoers') do
  it { should be_writable.by('owner') }
  it { should be_writable.by('group') }
  it { should be_writable.by('others') }
  it { should be_writable.by_user('apache') }
end
```

#### be_executable

In order to test a subject is executable, you should use **be\_executable** matcher.

```ruby
describe file('/etc/init.d/httpd') do
  it { should be_executable }
end
```

You can also test a subject is executable by owner, group members, others or a specific user.

```ruby
describe file('/etc/init.d/httpd') do
  it { should be_executable.by('owner') }
  it { should be_executable.by('group') }
  it { should be_executable.by('others') }
  it { should be_executable.by_user('httpd') }
end
```

#### be_mounted

In order to test a directory is mounted, you should use **be\_mounted** matcher.

```ruby
describe file('/') do
  it { should be_mounted }
end
```

You can also test a directory is mounted with correct attributes.

```ruby
describe file('/') do
  it { should be_mounted.with( :type => 'ext4' ) }
end

describe file('/') do
  it { should be_mounted.with( :options => { :rw => true } ) }
end

describe file('/') do
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

#### match_md5checksum

In order to test a file's md5 checksum matches a given value, you should use **match_md5checksum** matcher.

```ruby
describe file('/etc/services') do
  it { should match_md5checksum '35435ea447c19f0ea5ef971837ab9ced' }
end
```
