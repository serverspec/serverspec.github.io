### <a name="package">package</a>

Package resource type.

#### be_installed

In order to test a package is installed, you should use **be_installed** matcher.

```ruby
describe package('httpd') do
  it { should be_installed }
end
```

You can also test a given version of gem is installed.

```ruby
describe package('jekyll') do
  it { should be_installed.by('gem').with_version('0.12.1') }
end
```

Or to test a pip packge is installed.

```ruby
describe package('requests') do
  it { should be_installed.by('pip').with_version('2.18.1') }
end
```
