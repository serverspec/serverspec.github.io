### <a name="yumrepo">yumrepo</a>

Yumrepo resource type.

#### exist

In order to test a given yum repository exists,  you should use **exist** matcher.

```ruby
describe yumrepo('epel') do
  it { should exist }
end
```

#### be_enabled

In order to test a given yum repository is enabled,  you should use **be_enabled** matcher.

```ruby
describe yumrepo('epel') do
  it { should be_enabled }
end
```
