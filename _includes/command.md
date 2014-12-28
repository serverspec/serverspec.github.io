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
