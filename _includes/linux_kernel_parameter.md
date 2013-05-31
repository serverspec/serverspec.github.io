### <a name="linux_kernel_parameter">linux\_kernel\_parameter</a>

Linux kernel parameter resource type.

You can test Linux kernel parameters like this.

```ruby
describe 'Linux kernel parameters' do
  context linux_kernel_parameter('net.ipv4.tcp_syncookies') do 
    its(:value) { should eq 1 }
  end

  context linux_kernel_parameter('kernel.shmall') do
    its(:value) { should be >= 4294967296 }
  end

  context linux_kernel_parameter('kernel.shmmax') do
    its(:value) { should be <= 68719476736 }
  end

  context linux_kernel_parameter('kernel.osrelease') do
    its(:value) { should eq '2.6.32-131.0.15.el6.x86_64' }
  end

  context linux_kernel_parameter('net.ipv4.tcp_wmem') do
    its(:value) { should match /4096\t16384\t4194304/ }
  end
end
```
