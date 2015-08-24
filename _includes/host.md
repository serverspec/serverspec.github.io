### <a name="host">host</a>

Host resource type.

#### be_resolvable

In order to test a host is resolvable on the target host, you should use **be_resolvable** matcher.

```ruby
describe host('serverspec.org') do
  it { should be_resolvable }
end

describe host('serverspec.org') do
  it { should be_resolvable.by('hosts') }
end

describe host('serverspec.org') do
  it { should be_resolvable.by('dns') }
end
```

#### be_reachable

In order to test a given host is network reachable, you should use **be_reachable** matcher.

```ruby
describe host('target.example.jp') do
  # ping
  it { should be_reachable }
  # tcp port 22
  it { should be_reachable.with( :port => 22 ) }
  # set protocol explicitly
  it { should be_reachable.with( :port => 22, :proto => 'tcp' ) }
  # udp port 53
  it { should be_reachable.with( :port => 53, :proto => 'udp' ) }
  # timeout setting (default is 5 seconds)
  it { should be_reachable.with( :port => 22, :proto => 'tcp', :timeout => 1 ) }
end
```

#### its(:ipaddress)

You can get the ipaddress of the host, and can use any matchers rspec supports to them.

```ruby
describe host('example.jp') do
  its(:ipaddress) { should eq '1.2.3.4' }
end

describe host('example.jp') do
  its(:ipaddress) { should match /1\.2\.3\./ }
end

```
On a dualstack host this may return an IPv6 address, notably Linux. Use _its(:ipv4\_address)_ or _its(:ipv6\_address)_ described below to get the desired address format. 

#### its(:ipv4_address)

Query the IPv4 ipaddress of a host and apply any rspec supported matchers.

```ruby
describe host('example.jp') do
  its(:ipv4_address) { should eq '1.2.3.4' }
end

describe host('example.jp') do
  its(:ipv4_address) { should match /1\.2\.3\./ }
end

```

#### its(:ipv6_address)

Query the IPv6 ipaddress of a host and apply any rspec supported matchers.

```ruby
describe host('example.jp') do
  its(:ipv6_address) { should eq '2001:db8::1234' }
end

describe host('example.jp') do
  its(:ipv6_address) { should match /2001:db8:.*/ }
end

```
