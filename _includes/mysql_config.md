### <a name="mysql_config">mysql_config</a>

MySQL config resource type.

You can test MySQL config parameters like this.

```ruby
describe 'MySQL config parameters' do
  context mysql_config('innodb-buffer-pool-size') do
    its(:value) { should > 100000000 }
  end

  context mysql_config('socket') do
    its(:value) { should eq '/tmp/mysql.sock' }
  end
end
```
