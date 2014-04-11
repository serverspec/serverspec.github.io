### <a name="iis_website">iis_website</a>

IIS Website resource type.

#### exists

In order to test that an IIS website exists, you should use **exists** matcher.

```ruby
describe iis_website('Default Website') do
  it{ should exist }
end
```

#### enabled

In order to test that an IIS website is set to automatically start, you should use **enabled** matcher.

```ruby
describe iis_website('Default Website') do
  it{ should be_enabled }
end
```

#### running

In order to test that an IIS website is currently running, you should use **running** matcher.

```ruby
describe iis_website('Default Website') do
  it{ should be_running }
end
```

#### in\_app\_pool

In order to test that an IIS website is currently assigned to the correct Application Pool, you should use **in\_app\_pool** matcher.

```ruby
describe iis_website('Default Website') do
  it{ should be_in_app_pool('Default App Pool') }
end
```

#### have\_physical\_path

In order to test that an IIS website gets its files from the correct location, you should use **have\_physical\_path** matcher.

```ruby
describe iis_website('Default Website') do
  it{ should have_physical_path('C:\\inetpub\\www') } 
end
```