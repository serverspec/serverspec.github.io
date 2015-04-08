### <a name="interface">interface</a>

Network interface resource type.

#### exist

In order to test a interface exist, you should use **exist** matcher.

```ruby
describe interface('eth0') do
  it { should exist }
end
```

#### speed

In order to test the speed of network interface is set up correctly, you should use this syntax.

```ruby
describe interface('eth0') do
  its(:speed) { should eq 1000 }
end
```

#### have\_ipv4\_address

In order to test a interface has a ip address, you should use **have\_ipv4\_address** matcher.

```ruby
describe interface('eth0') do
  it { should have_ipv4_address("192.168.10.10") }
  it { should have_ipv4_address("192.168.10.10/24") }
end
```
