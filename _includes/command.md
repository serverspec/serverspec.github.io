### <a name="command">command</a>

Command resource type.

#### its(:stdout), its(:stderr), its(:exit_status)

You can get the stdout, stderr and exit status of the command result, and can use any matchers RSpec supports.

```ruby
describe command('ls -al /') do
  its(:stdout) { should match /bin/ }
end

describe command('ls /foo') do
  its(:stderr) { should match /No such file or directory/ }
end

describe command('ls /foo') do
  its(:exit_status) { should eq 0 }
end
```

#### contain

In order to test a command stdout/stderr a given string, you can use **contain** matcher.

```ruby
describe command('apachectl -M') do
  its(:stdout) { should contain('proxy_module') }
end
```

You can test a given string within a given range.

```ruby
describe command('apachectl -V') do
  # test 'Prefork' exists between "Server MPM" and "Server compiled".
  its(:stdout) { should contain('Prefork').from(/^Server MPM/).to(/^Server compiled/) }

  # test 'conf/httpd.conf' exists after "SERVER_CONFIG_FILE".
  its(:stdout) { should contain('conf/httpd.conf').after('SERVER_CONFIG_FILE') }

  # test 'Apache/2.2.29' exists before "Server built".
  its(:stdout) { should contain(' Apache/2.2.29').before('Server built') }
end
```
