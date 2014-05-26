### <a name="ppa">ppa</a>

PPA resource type.

#### exist

In order to test a given ppa repository exists,  you should use **exist** matcher.

You can specify ppa name which is got rid of `ppa:`.

```ruby
describe ppa('launchpad-username/ppa-name') do
  it { should exist }
end
```

#### be_enabled

In order to test a given ppa repository is enabled,  you should use **be_enabled** matcher.

```ruby
describe ppa('launchpad-username/ppa-name') do
  it { should be_enabled }
end
```
