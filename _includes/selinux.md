### <a name="selinux">selinux</a>

SELinux resource type.

#### be\_disabled, be\_enforcing, be\_permissive

In order to test SELinux is running in a given mode, you should use **be\_disabled, be\_enforcing and be\_permissive** matchers.

```ruby
# SELinux should be disabled
describe selinux do
  it { should be_disabled }
end

# SELinux should be enforcing
describe selinux do
  it { should be_enforcing }
end

# SELinux should be permissive
describe selinux do
  it { should be_permissive }
end
```

To check if a given policy is used in permissive or enforcing mode append the **with_policy** matcher.

```ruby
# SELinux should be enforcing with policy mls
describe selinux do
  it { should be_enforcing.with_policy('mls') }
end

# SELinux should be permissive with policy targeted
describe selinux do
  it { should be_permissive.with_policy('targeted') }
end
```
