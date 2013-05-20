### <a name="ipfilter">ipfilter</a>

Ipfilter resource type.

#### have_rule

In order to test ipfilter has a given rule, you should use **have_rule** matcher.

```ruby
describe ipfilter do
  it { should have_rule 'pass in quick on lo0 all' }
end
```
