### <a name="zfs">zfs</a>

ZFS resource type.

#### exist

In order to test a given zfs pool exists,  you should use **exist** matcher.

```ruby
describe zfs('rpool') do
  it { should exist }
end
```

#### have_property

In order to test a zfs pool has given properties,  you should use **have_property** matcher.

```ruby
describe zfs('rpool') do
  it { should have_property 'mountpoint' => '/rpool', 'compression' => 'off' }
end
```
