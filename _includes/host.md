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

You can get the ipaddress of the host,  and can use any matchers rspec supports to them.

```ruby
describe host('example.jp') do
  its(:ipaddress) { should eq '1.2.3.4' }
end

describe host('example.jp') do
  its(:ipaddress) { should match /1\.2\.3\./ }
end

```
