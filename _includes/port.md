### <a name="port">port</a>

Port resource type.

#### be_listening

In order to test a given port is listening, you should use **be_listening** matcher.

```ruby
describe port(80) do
  it { should be_listening }
end
```

You can also specify ``tcp`` or ``udp``.


```ruby
describe port(80) do
  it { should be_listening.with('tcp') }
end

describe port(53) do
  it { should be_listening.with('udp') }
end
```
