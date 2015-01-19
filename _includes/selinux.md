### <a name="selinux">selinux</a>

SELinux resource type.

#### be\_disabled, be\_enforcing, be\_permissive

In order to test SELinux is a given mode, you should use **be\_disabled, be\_enforcing and be\_permissive** matchers.

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
