### <a name="kernel_module">kernel_module</a>

Kernel module resource type.

#### be\_loaded

In order to test a given kernel module is loaded, you should use **be_loaded** matcher.

```ruby
describe kernel_module('virtio_balloon') do
  it { should be_loaded }
end
```

