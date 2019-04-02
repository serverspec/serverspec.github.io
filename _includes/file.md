### <a name="file">file</a>

File and directory resource type.

#### be_file

In order to test a subject exists as a file, you should use **be_file** matcher.

```ruby
describe file('/etc/passwd') do
  it { should be_file }
end
```

#### exist

In order to test the presence of a file, you should use **exist** matcher.

```ruby
describe file('/etc/passwd') do
  it { should exist }
end
```

#### be_directory

In order to test a subject exists as a directory, you should use **be_directory** matcher.

```ruby
describe file('/var/log/httpd') do
  it { should be_directory }
end
```

#### be\_block\_device

In order to test a subject exists as a block device, you should use **be\_block\_device** matcher.

```ruby
describe file('/dev/disk0') do
  it { should be_block_device }
end
```

#### be\_character\_device

In order to test a subject exists as a character device, you should use **be\_character\_device** matcher.

```ruby
describe file('/dev/ttys0') do
  it { should be_character_device }
end
```

#### be_pipe

In order to test a subject exists as a name pipe, you should use the **be_pipe** matcher.

```ruby
describe file('/tmp/unicorn.fifo') do
  it { should be_pipe }
end
```

#### be_socket

In order to test a subject exists as a socket, you should use **be_socket** matcher.

```ruby
describe file('/var/run/unicorn.sock') do
  it { should be_socket }
end
```

#### be_symlink

In order to test a subject exists as a link, you should use **be_symlink** matcher.

```ruby
describe file('/etc/pam.d/system-auth') do
  it { should be_symlink }
end
```

#### contain

**Notice: Instead of ``contain``, you can use ``its(:content)`` and any standard rspec matchers. The matcher ``contain`` will be obsoleted.**

```ruby
describe file('/etc/httpd/conf/httpd.conf') do
  its(:content) { should match /ServerName www\.example\.jp/ }
end
```

In order to test a file contains a given string, you can use **contain** matcher.

```ruby
describe file('/etc/httpd/conf/httpd.conf') do
  it { should contain 'ServerName www\.example\.jp' }
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

**Notice: ``be_mode``, supports 3 and 4 number octet matching in the format '755' and '2755'**

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

#### be_immutable

In order to test a subject is immutable, you should use the **be\_immutable** matcher.

```ruby
describe file('/root/.ssh/authorized_keys') do
  it { should be_immutable }
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

#### be_version

In order to test a file's version using its metadata in Windows, you should use **be_version** matcher.

```ruby
describe file('C:\\Windows\\System32\\wuapi.dll') do
  it { should be_version('7.6.7600.256') }
end
```

#### its(:md5sum)

In order to test a file's md5 checksum matches a given value, you should use **its(:md5sum)**.

```ruby
describe file('/etc/services') do
  its(:md5sum) { should eq '35435ea447c19f0ea5ef971837ab9ced' }
end
```

#### its(:selinux_label)

In order to test a file's SELinux label matches a given value, you should use **its(:selinux_label)**.

```ruby
describe file('/etc/services') do
  its(:selinux_label) { should eq 'system_u:object_r:etc_t:s0' } 
end 
```

#### its(:sha256sum)

In order to test a file's sha256 checksum matches a given value, you should use **its(:sha256sum)**.

```ruby
describe file('/etc/services') do
  its(:sha256sum) { should eq 'a861c49e9a76d64d0a756e1c9125ae3aa6b88df3f814a51cecffd3e89cce6210' }
end
```

#### its(:size)

In order to test a file's size matches a given value, you should use **its(:size)**. The file size is passed as bytes.

```ruby
describe file('/etc/services') do
  its(:size) { should < 641021 }
end
```

#### its(:content\_as\_yaml)

In order to test YAML file's contents match a given value, you should use **its(:content\_as\_yaml)**.

```ruby
describe file('example.yml') do
  its(:content_as_yaml) { should include('foo' => include('bar' => 'hoge')) }
end
```

example.yml

```yaml
---
foo:
  bar: hoge
```

#### its(:content\_as\_json)

In order to test JSON file's contents match a given value, you should use **its(:content\_as\_json)**.

```ruby
describe file('example.json') do
  its(:content_as_json) { should include('foo' => include('bar' => 'hoge')) }
end
```

example.json

```json
{
  "foo": {
    "bar": "hoge"
  }
}
```
