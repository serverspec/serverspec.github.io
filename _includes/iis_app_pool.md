### <a name="iis_app_pool">iis_app_pool</a>

IIS Application Pool resource type.

#### exists

In order to test that an IIS app pool exists, you should use **exists** matcher.

```ruby
describe iis_app_pool('Default App Pool') do
  it{ should exist }
end
```

#### have_dotnet_version

In order to test that an IIS app pool is using the correct .NET version, you should use **have_dotnet_version** matcher.

```ruby
describe iis_app_pool('Default App Pool') do
  it{ should have_dotnet_version('2.0') }
end
```
