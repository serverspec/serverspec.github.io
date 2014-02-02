### <a name="group">group</a>

Group resource type.

#### exist

In order to test a group exists, you should use **exist** matcher.

```ruby
describe group('wheel') do
  it { should exist }
end
```

#### have\_gid

In order to test a group have a given gid, you should use **have\_gid** matcher.

```ruby
describe group('root') do
  it { should have_gid 0 }
end
```

