### <a name="interface">interface</a>

Network interface resource type.

In order to test a network interface is set up correctly, you should use this syntax.

```ruby
describe interface('eth0') do
  its(:speed) { should eq 1000 }
end
```
