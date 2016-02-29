### <a name="ip6tables">ip6tables</a>

Ip6tables resource type.

#### have\_rule

In order to test ip6tables has a given rule, you should use **have\_rule** matcher.

```ruby
describe ip6tables do
  it { should have_rule('-P INPUT ACCEPT') }
end
```

You can give a table name and a chain name like this.

```ruby
describe ip6tables do
  it { should have_rule('-P INPUT ACCEPT').with_table('mangle').with_chain('INPUT') }
end
```
