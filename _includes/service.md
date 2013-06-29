### <a name="service">service</a>

Service resource type.

#### be_enabled

In order to test a given service is enabled(automatically start when OS booting up), you should use **be_enabled** matcher.

```ruby
describe service('ntpd') do
  it { should be_enabled }
end
```

You can test a service is enabled with a given run level.(This works only with Red Hat and Debian family currently.)

```ruby
describe service('ntpd') do
  it { should be_enabled.with_level(3) }
end
```

#### be_running

In order to test a given service/process is running, you should use **be_running** matcher.

```ruby
describe service('ntpd') do
  it { should be_running }
end
```

You can test a given service/process is running under [supervisor](http://supervisord.org/).

```ruby
describe service('ntpd') do
  it { should be_running.under('supervisor') }
end
```
