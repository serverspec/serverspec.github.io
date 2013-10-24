### <a name="lxc">LXC</a>

LXC(Linux Container) resource type.

You can test LXC like this.

```ruby
describe lxc('ct01') do
  it { should exist }
  it { should be_running }
end
```
