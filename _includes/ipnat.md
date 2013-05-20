### <a name="ipnat">ipnat</a>

Ipnat resource type.

#### have_rule

In order to test ipnat has a given rule, you should use **have_rule** matcher.

```ruby
describe ipnat do
  it { should have_rule 'map net1 192.168.0.0/24 -> 0.0.0.0/32' }
end
```
