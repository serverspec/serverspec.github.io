### <a name="bond">bond</a>

Network bond resource type.

### exist

In order to test a bond exists, you shoud use **exist** matcher.

```ruby
describe bond('bond0') do
  it { should exist }
end
```

#### have_interface

In order to test a bond has a correct member, you should use **have_interface** matcher.

```ruby
describe bond('bond0') do
  it { should have_interface 'eth0' }
end
```
