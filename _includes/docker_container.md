### <a name="docker_container">docker_container</a>

Docker Container resource type

Container settings can be tested like this.

```ruby
describe docker_container('focused_curie') do
  its(['HostConfig.NetworkMode']) { should eq 'bridge' }
  its(:Path) { should eq '/bin/sh' }
end
```

#### exist

Check if a named container exists.

```ruby
describe docker_container('focused_curie') do
  it { should exist }
end
```

#### be_running

Check if a named container is running.

```ruby
describe docker_container('focused_curie') do
  it { should be_running }
end
```

#### have_volume

In order to test if a volume has been mounted.

```ruby
describe docker_container('focused_curie') do
  it { should have_volume('/tmp','/data') }
end
```
