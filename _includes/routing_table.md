### <a name="routing_table">routing_table</a>

Routing table resource type.

#### have_entry

In order to test a routing table has a given entry, you should use **have_entry** matcher.

```ruby
describe routing_table do
  it do
    should have_entry(
      :destination => '192.168.100.0/24',
      :interface   => 'eth1',
      :gateway     => '192.168.10.1',
    )
  end
end
```
