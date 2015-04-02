### <a name="docker_image">docker_image</a>

Docker Image resource type

Image settings can be tested like this:

```ruby
describe docker_image('busybox:latest') do
  its(:Architecture) { should eq 'amd64' }
end
```

#### be_present

Check if a specific image been pulled to the host.

```ruby
describe docker_image('busybox:latest') do
  it { should be_present }
end
```

#### have_setting

In order to check  an image setting from `docker inspect`:

```ruby
describe docker_image('busybox:latest') do
  it { should_not have_setting('Architecture','i386') }
end
```

