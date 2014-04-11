### <a name="windows_feature">windows_feature</a>

Windows Feature resource type.

#### installed

In order to test that a windows feature has been installed, you should use **installed** matcher.

```ruby
describe windows_feature('Minesweeper') do
  it{ should be_installed }
end
```

You can optionally specify the method used to check the windows feature, as the same feature can have different names.

```ruby
describe windows_feature('IIS-Webserver') do
  it{ should be_installed.by("dism") }
end

describe windows_feature('Web-Webserver') do
  it{ should be_installed.by("powershell") }
end
```