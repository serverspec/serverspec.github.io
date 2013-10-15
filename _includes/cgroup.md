### <a name="cgroup">cgroup</a>

Linux cgroup resource type.

You can test cgroup parameters like this.

```ruby
describe cgroup('group1') do
  its('cpuset.cpus') { should eq 1 }
end
```
