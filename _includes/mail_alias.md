### <a name="mail_alias">mail\_alias</a>

Mail alias resource type.

You can test mail aliases like this.

```ruby
describe mail_alias('daemon') do
  it { should be_aliased_to 'root' }
end
```
