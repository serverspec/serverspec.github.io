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

#### be_installed

In order to test a given service is installed, you should use **be_installed** matcher.

*Currently only supported in Windows*

```ruby
describe service('DNS Client') do
  it { should be_installed }
end
```

#### be_running

In order to test a given service/process is running, you should use **be_running** matcher.

```ruby
describe service('ntpd') do
  it { should be_running }
end
```

You can test a given service/process is running under [supervisor](http://supervisord.org/), [upstart](https://launchpad.net/upstart), [systemd](https://wiki.freedesktop.org/www/Software/systemd/), and [daemontools](http://cr.yp.to/daemontools.html).

```ruby
describe service('ntpd') do
  it { should be_running.under('supervisor') }
end

describe service('ntpd') do
  it { should be_running.under('upstart') }
end

describe service('ntpd') do
  it { should be_running.under('systemd') }
end

describe service('ntpd') do
  it { should be_running.under('daemontools') }
end
```

#### be\_monitored\_by

In order to test a service/process is monitored by a given software, you should use **be\_monitored\_by** matcher.

```ruby
describe service('sshd') do
  it { should be_monitored_by('monit') }
end

describe service('unicorn') do
  it { should be_monitored_by('god') }
end

```

Should the monitor resource not match the service name the **with\_name** matcher can be used override it.

```ruby
describe service('tinc') do
  it { should be_monitored_by('monit').with_name('tinc-myvpn') }
end

```


#### have\_start\_mode

In order to test a service's startup mode is correct, you should use **have\_start\_mode** matcher.

*Currently only supported in Windows*

```ruby
describe service('DNS Client') do
  it { should have_start_mode('Manual') }
end
```
