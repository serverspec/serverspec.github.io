### <a name="php_config">php_config</a>

PHP config resource type.

You can test PHP config parameters like this.

```ruby
describe 'PHP config parameters' do
  context  php_config('default_mimetype') do
    its(:value) { should eq 'text/html' }
  end

  context php_config('session.cache_expire') do
    its(:value) { should eq 180 }
  end

  context php_config('mbstring.http_output_conv_mimetypes') do
    its(:value) { should match /application/ }
  end
```
