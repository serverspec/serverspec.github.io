### <a name="x509_certificate">x509_certificate</a>

x509_certificate resource type

#### be_certificate

In order to check whether a file is a certificate, use **be_certificate** matcher.

```ruby
describe x509_certificate('some_cert.pem') do
  it { should be_certificate }
end
```

#### be_valid

You can ensure that a certificate is valid at present moment using **be_valid** matcher.

```ruby
describe x509_certificate('some_cert.pem') do
   it { should be_valid }
end
```

#### validity\_in\_days

In order to ensure that a certificate is valid for a certain amount of days, use **validity\_in\_days**.

```ruby
describe x509_certificate('some_cert.pem') do
  its(:validity_in_days) { should_not be < 100 }
  its(:validity_in_days) { should be >= 100 }
end
```

#### subject

In order to check the **subject** of a certificate, use: 

```ruby
describe x509_certificate('some_cert.pem') do
  its(:subject) { should eq '/C=DE/O=What/OU=Ever/CN=Root CA' }
end
```
#### issuer

In order to check the **issuer** of a certificate, use:

```ruby
describe x509_certificate('some_cert.pem') do
  its(:issuer) { should match  /O=What/ }
end
```
#### email

In order to check the **email** of a certificate, use:

```ruby
describe x509_certificate('some_cert.pem') do
  its(:email) { should be_empty }
end
```

#### have_purpose

Certificates can have purposes enabled or not, i.e. a certificate that may be used for client side SSL authentication.
Check with **have_purpose**:

```ruby
describe x509_certificate('some_cert.pem') do
  it { should have_purpose 'SSL server CA' }
  it { should_not have_purpose 'SSL server' }
end
```

#### keylength

In oder to ensure that the key of a certificate has been generated with a certain key length, use the **key_length** matcher. 
It returns the key length as an integer, so it can be easily compared like:

```ruby
describe x509_certificate('some_cert.pem') do
  its(:keylength) { should be >= 2048 }
end
```
