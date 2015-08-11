### <a name="linux_audit_system">linux\_audit\_system</a>

Allow checking the configuration of linux audit system via `/sbin/auditctl`. Suitable for server hardening.

#### be_running

To make sure that the audit system is running.

```ruby
describe linux_audit_system do
  it { should be_running }
end
```

#### be_enabled

To make sure that the audit system is enabled (mode '1').

```ruby
describe linux_audit_system do
  it { should be_enabled }
end
```

#### rules

To check that audit system has a given auditing rule. Argument can be a string for equality comparison or a regular expression.

```ruby
describe linux_audit_system do
  its(:rules) { should include '-w /etc/audit/ -p wa' }
  its(:rules) { should include '-w /var/lib/ -p wa' }
  its(:rules) { should include %r!/var/lib/! }
  its(:rules) { should_not include %r!/var/log! }
end
```
