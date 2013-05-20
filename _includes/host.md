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
