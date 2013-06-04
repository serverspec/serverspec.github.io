---
layout: layout
title: Advanced Tips
---

## PATH environment variable

You can add PATH environment variable in spec_helper.rb or other places like this.

```ruby
RSpec.configure do |c|
  c.path = '/sbin:/usr/sbin'
  ...
```

In this case, a command is expanded to ``PATH=/sbin:/usr/sbin command``.

----

## Block scoped PATH environment variable

**This feature is experimental.So this may be changed in the future.**

You can also set PATH environment variable only in a block scope like this.

```ruby
describe package('jekyll') do
  let(:path) { '/usr/local/rbenv/shims' }
  it { should be_installed.by('gem') }
end
```

----

## Block scoped pre_command parameter

**This feature is experimental.So this may be changed in the future.**

You can set pre_command parameter like this.

```ruby
describe service('httpd') do
  let(:pre_command) { 'source ~/.zshrc' }
  it { should be_running }
end
```

In this case, a command is expanded to ``source ~/.zshrc && service httpd status``.
