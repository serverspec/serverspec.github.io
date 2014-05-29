### <a name="ppa">ppa</a>

PPA resource type.

#### exist

In order to test a given ppa repository exists,  you should use **exist** matcher.

PPA resource type accepts both `ppa:username/reponame` and `username/reponame` style.

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
