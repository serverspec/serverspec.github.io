### <a name="docker_image">docker_image</a>

Docker Image resource type

Check the attributes hash returned by `docker inspect`.

```ruby
describe docker_image('busybox:latest') do
  its(:inspection) { should_not include 'Architecture' => 'i386' }
end
```

You can also specify hash key like this.

```ruby
describe docker_image('busybox:latest') do
  its(['Architecture']) { should eq 'amd64' }
end
```

You can also specify nested hash key like this.

```ruby
describe docker_image('busybox:latest') do
  its(['Config.Cmd']) { should include '/bin/sh' }
end
```

#### exist

Check if a specific image been pulled to the host.

```ruby
describe docker_image('busybox:latest') do
  it { should exist }
end
```
