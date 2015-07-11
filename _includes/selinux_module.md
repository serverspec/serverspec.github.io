### <a name="selinux_module">selinux\_module</a>

SELinux Module resource type.

#### be\_enabled

In order to test if a SELinux module is enabled, the following syntax is used.

```ruby
describe selinux_module('zebra') do
  it { should be_enabled }
end
```

#### be\_installed

To check if a given SELinux module is installed, the following syntax is used. 

```ruby
describe selinux_module('zebra') do
  it { should be_installed }
end
```

To see if a given version of SELinux module is installed the *with_version* matcher is appended.

```ruby
describe selinux_module('zebra') do
  it { should be_installed.with_version('1.13.0') }
end
```
