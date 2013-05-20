### <a name="cron">cron</a>

Cron resource type.

#### have\_cron\_entry

In order to test cron have a given entry exists, you should use **have_cron_entry** matcher.

```ruby
describe cron do
  it { should have_entry '* * * * * /usr/local/bin/foo' }
end
```

You can test a given user has the cron entry like this.

```ruby
describe cron do
  it { should have_cron_entry('* * * * * /usr/local/bin/foo').with_user('mizzy') }
end
```
