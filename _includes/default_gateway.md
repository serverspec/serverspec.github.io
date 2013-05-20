### <a name="default_gateway">default_gatewy</a>

Default gateway resource type.

In order to test a default gateway is set up correctly, you should use this syntax.

```ruby
describe default_gateway do
  its(:ipaddress) { should eq '192.168.10.1' }
  its(:interface) { should eq 'br0'          }
end
```
