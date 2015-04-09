### <a name="bridge">bridge</a>

Network bridge resource type.

#### exist

In order to test a bridge exists, you should use **exist** matcher.

```ruby
describe bridge('br0') do
  it { should exist }
end
```

#### have_interface

In order to test a bridge has a correct interface, you should use **have_interface** matcher.

```ruby
describe bridge('br0') do
  let(:stdout) { 'eth0' }
  it { should have_interface 'eth0' }
end
```
