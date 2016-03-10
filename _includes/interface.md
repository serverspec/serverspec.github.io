### <a name="interface">interface</a>

Network interface resource type.

#### exist

In order to test an interface exists, you should use **exist** matcher.

```ruby
describe interface('eth0') do
  it { should exist }
end
```

#### up

In order to test an interface is up, you should use **be_up** matcher.

```ruby
describe interface('eth0') do
  it { should be_up }
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

In order to test an interface has an IP address, you should use **have\_ipv4\_address** matcher.

```ruby
describe interface('eth0') do
  it { should have_ipv4_address("192.168.10.10") }
  it { should have_ipv4_address("192.168.10.10/24") }
end
```
#### have\_ipv6\_address

In order to test an interface has an IPv6 address, you should use **have\_ipv6\_address** matcher.

```ruby
describe interface('eth0') do
  it { should have_ipv6_address("fe80::1") }
  it { should have_ipv6_address("fd00::1/48") }
end
```

#### its(:ipv4_address)

Query the IPv4 ipaddress of an interface and apply any rspec supported matchers.

```ruby
describe interface('eth0') do
  its(:ipv4_address) { should eq '1.2.3.4/1' }
end

describe interface('eth0') do
  its(:ipv4_address) { should match /1\.2\.3\./ }
end
```

#### its(:ipv6_address)

Query the IPv6 ipaddress of an interface and apply any rspec supported matchers.

```ruby
describe interface('eth0') do
  its(:ipv6_address) { should eq '2001:db8::1234/1' }
end

describe interface('eth0') do
  its(:ipv6_address) { should match /2001:db8:.*/ }
end
```
