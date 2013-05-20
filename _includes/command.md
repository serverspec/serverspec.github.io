### <a name="command">command</a>

Command resource type.

#### return_stdout

In order to test a given command returns correct stdout, you should use **return_stdout** matcher.

```ruby
describe command('whoami') do
  it { should return_stdout 'root' }
end
```

You can also use a regular expression.

```ruby
describe command('cat /etc/resolv.conf') do
  it { should return_stdout /8\.8\.8\.8/ }
end
```

#### return_stderr

In order to test a given command returns correct stderr, you should use **return_stderr** matcher.

```ruby
describe command('ls /foo') do
  it { should return_stderr 'ls: /foo: No such file or directory' }
end
```

You can also use a regular expression.

```ruby
describe command('ls /foo') do
  it { should return_stderr /No such file or directory/ }
end
```
    
#### return\_exit\_status

In order to test a given command returns correct exit status, you should use **return\_exit\_status** matcher.

```ruby
describe command('ls /tmp') do
  it { should return_exit_status 0 }
end
```
