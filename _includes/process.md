### <a name="process">process</a>

Process resource type.

You can test any process parameter available through the `ps` command like this:

```ruby
describe process("memcached") do
    its(:args) { should match /-c 32000\b/ }
end
```

For the complete list of available parameters, check the manual page
for `ps(1)`, section _Standard Format Specifiers_. When several
processes match, only the parameters of the first one are available.

#### be_running

To check if a given process is running, you should use **be_running** matcher.

```ruby
describe process("memcached") do
  it { should be_running }
end
```
