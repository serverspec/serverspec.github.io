### <a name="cron">cron</a>

Cron resource type.

#### have\_entry

In order to test cron have a given entry exists, you should use **have_entry** matcher.

```ruby
describe cron do
  it { should have_entry '* * * * * /usr/local/bin/foo' }
end
```

You can test a given user has the cron entry like this.

```ruby
describe cron do
  it { should have_entry('* * * * * /usr/local/bin/foo').with_user('mizzy') }
end
```

You can get all cron table entries and use regexp like this.

```ruby
describe cron do
  its(:table) { should match  /you can use regexp/ }
end
```
