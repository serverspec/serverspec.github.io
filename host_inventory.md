---
layout: layout
title: Host Inventory
---

## Host Inventory

You can get host inventory information.

```ruby
host_inventory['memory']['total']
```

This is one of the features of Specinfra precisely, not Serverspec. But you can use this feature from Serverspec.

From [Itamae](http://itamae.kitchen/), you can use this feature like this.

```ruby
node['memory']['total']
```

----

## Supported inventory types

### cpu

```ruby
host_inventory['cpu']['total']               # => 1
host_inventory['cpu']['0']['vendor_id']        # => GenuineIntel
host_inventory['cpu']['0']['cpu_family']       # => 6
host_inventory['cpu']['0']['model']            # => 58
host_inventory['cpu']['0']['model_name']       # => Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz
host_inventory['cpu']['0']['stepping']         # => 9
host_inventory['cpu']['0']['microcode']        # => 0x19
host_inventory['cpu']['0']['cpu_mhz']          # => 2395.601
host_inventory['cpu']['0']['cache_size']       # => 6144KB
host_inventory['cpu']['0']['physical_id']      # => 0
host_inventory['cpu']['0']['siblings']         # => 1
host_inventory['cpu']['0']['core_id']          # => 0
host_inventory['cpu']['0']['cpu_cores']        # => 1
host_inventory['cpu']['0']['apicid']           # => 0
host_inventory['cpu']['0']['initial_apicid']   # => 0
host_inventory['cpu']['0']['fpu']              # => yes
host_inventory['cpu']['0']['fpu_exception']    # => yes
host_inventory['cpu']['0']['cpuid_level']      # => 13
host_inventory['cpu']['0']['wp']               # => yes
host_inventory['cpu']['0']['flags']            # => ["fpu", "vme", "de", "pse", "tsc", "msr", "pae", "mce", "cx8", "apic", "sep", "mtrr", "pge", "mca", "cmov", "pat", "pse36", "clflush", "mmx", "fxsr", "sse", "sse2", "syscall", "nx", "rdtscp", "lm", "constant_tsc", "rep_good", "nopl", "xtopology", "nonstop_tsc", "pni", "pclmulqdq", "monitor", "ssse3", "cx16", "sse4_1", "sse4_2", "popcnt", "aes", "xsave", "avx", "rdrand", "lahf_lm"]
host_inventory['cpu']['0']['bogomips']         # => 4791.20
host_inventory['cpu']['0']['clflush_size']     # => 64
host_inventory['cpu']['0']['cache_alignment']  # => 64
host_inventory['cpu']['0']['address_sizes']    # => 36 bits physical, 48 bits virtual
host_inventory['cpu']['0']['power_management'] # =>
```

----

### domain

You can get domain name like this.

```ruby
host_inventory['domain'] # => localdomain
```

----

### ec2

You can get ec2 metadata which can be taken from http://169.254.169.254/latest/meta-data/.

```ruby
host_inventory['ec2']['ami-id'] # => ami-35072834
```

`host_inventory[:ec2]` is a hash which has keys and values like this.

```ruby
{"ami-id"=>"ami-35072834",
 "ami-launch-index"=>"0",
 "ami-manifest-path"=>"(unknown)",
 "block-device-mapping"=>{"ami"=>"/dev/xvda", "root"=>"/dev/xvda"},
 "hostname"=>"ip-172-30-1-119.ap-northeast-1.compute.internal",
 "instance-action"=>"none",
 "instance-id"=>"i-0d307c14",
 "instance-type"=>"t2.micro",
 "local-hostname"=>"ip-172-30-1-119.ap-northeast-1.compute.internal",
 "local-ipv4"=>"172.30.1.119",
 "mac"=>"06:7f:7c:cb:8e:d0",
 "metrics"=>{"vhostmd"=>"<?xml version=\"1.0\" encoding=\"UTF-8\"?>"},
 "network"=>
  {"interfaces"=>
    {"macs"=>
      {"06:7f:7c:cb:8e:d0"=>
        {"device-number"=>"0",
         "interface-id"=>"eni-d98d1dae",
         "ipv4-associations"=>{"54.64.165.234"=>"172.30.1.119"},
         "local-hostname"=>"ip-172-30-1-119.ap-northeast-1.compute.internal",
         "local-ipv4s"=>"172.30.1.119",
         "mac"=>"06:7f:7c:cb:8e:d0",
         "owner-id"=>"853708250916",
         "public-hostname"=>"",
         "public-ipv4s"=>"54.64.165.234",
         "security-group-ids"=>"sg-00478965",
         "security-groups"=>"launch-wizard-4",
         "subnet-id"=>"subnet-6654bd11",
         "subnet-ipv4-cidr-block"=>"172.30.1.0/24",
         "vpc-id"=>"vpc-3108e254",
         "vpc-ipv4-cidr-block"=>"172.30.0.0/16"}}}},
 "placement"=>{"availability-zone"=>"ap-northeast-1b"},
 "profile"=>"default-hvm",
 "public-hostname"=>"",
 "public-ipv4"=>"54.64.165.234",
 "public-keys"=>
  {"0"=>
    {"openssh-key"=>
      "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCBgoqZg320DAgdessGJXTadkkQ9HHd552na9nERPiOU36WU1DE83CHDrCi7rToPLji0M+l1Vi8yXUrqPkTeC2AY7HpbG2aY+7ReLtsZin+gB2+oEMk3UGQP29foG3AB6syy7n9lm71qz9q91tItaBMszVNH7oRC1a7ZB8eJx6hNAid8uD8zsvmldOLZ+rCWTRBJLbjEm3AYTFfduL/1wptA+/7u7CJ8rRCxg4Dfwja0APTZeyjL31w3AraGTlQL0IxxTjogVb1AoGbpWC8RjUfV/IAGJGntpIJF1J+tayDSCIpvic9oi9DqGmijZpnwisdVCn88o9yL9vJ7Wpj4iDt miya\n"}},
 "reservation-id"=>"r-53e9b055",
 "security-groups"=>"launch-wizard-4",
 "services"=>{"domain"=>"amazonaws.com"}}
```

----

### filesystem

You can get file system information like this.

```ruby
host_inventory['filesystem']['/dev/xvda1']['kb_size']       # => 8123812
host_inventory['filesystem']['/dev/xvda1']['kb_used']       # => 1094944
host_inventory['filesystem']['/dev/xvda1']['kb_available']  # => 6928620
host_inventory['filesystem']['/dev/xvda1']['percent_used']  # => 14%
host_inventory['filesystem']['/dev/xvda1']['mount']         # => /

```

On Solaris there are multiple instances of the file system _swap_. To provide access to every instance an integer, starting at 0 and incrementing by 1, is appended to the name.

```ruby
host_inventory['filesystem']['swap0']['mount']  # => /etc/svc/volatile
host_inventory['filesystem']['swap1']['mount']  # => /tmp
```

----

### fqdn

You can get FQDN like this.

```ruby
host_inventory['fqdn'] # => localhost.localdomain
```

----

### hostname

You can get host name like this.

```ruby
host_inventory['hostname'] # => localhost
```

----

### kernel

You can get kernel information like this.

```ruby
host_inventory['kernel']['machine']       # => x86_64
host_inventory['kernel']['name']          # => Linux
host_inventory['kernel']['release']       # => 3.13.0-83-generic
host_inventory['kernel']['version']       # => 3.13.0
host_inventory['kernel']['version_major'] # => 3.13
```

----

### memory

You can get memory information like this.

```ruby
host_inventory['memory']['swap']             # => {"cached"=>"0kB", "total"=>"0kB", "free"=>"0kB"}
host_inventory['memory']['total']            # => 1020044kB
host_inventory['memory']['free']             # => 506900kB
host_inventory['memory']['buffers']          # => 142640kB
host_inventory['memory']['cached']           # => 298484kB
host_inventory['memory']['active']           # => 402636kB
host_inventory['memory']['inactive']         # => 55024kB
host_inventory['memory']['dirty']            # => 80kB
host_inventory['memory']['writeback']        # => 0kB
host_inventory['memory']['anon_pages']       # => 16564kB
host_inventory['memory']['mapped']           # => 6076kB
host_inventory['memory']['slab']             # => 38688kB
host_inventory['memory']['slab_reclaimable'] # => 30356kB
host_inventory['memory']['slab_unreclaim']   # => 8332kB
host_inventory['memory']['page_tables']      # => 1948kB
host_inventory['memory']['nfs_unstable']     # => 0kB
host_inventory['memory']['bounce']           # => 0kB
host_inventory['memory']['commit_limit']     # => 510020kB
host_inventory['memory']['committed_as']     # => 56248kB
host_inventory['memory']['vmalloc_total']    # => 34359738367kB
host_inventory['memory']['vmalloc_used']     # => 2448kB
host_inventory['memory']['vmalloc_chunk']    # => 34359716791kB
```

----

### platform

You can get OS type like this.

```ruby
host_inventory['platform'] # => redhat
```

----

### platform_version

You can get OS version like this.

```ruby
host_inventory['platform_version'] # => 6.5
```

----

### virtualization

To find out if the host is running on a virtualized platform or in a container use the _virtualization_ keyword.

```ruby
host_inventory['virtualization'][:system] # => "docker"
```

### block_device

You can get block devices.

```ruby
host_inventory['block_device']['sda']['size'] # => 81920000
```

`host_inventory['block_device']` is a hash which has keys and values like this.

```ruby
{
    "loop0" => {
        "rotational" => "1",
         "removable" => "0",
              "size" => "0"
    },
     "ram0" => {
        "rotational" => "1",
         "removable" => "0",
              "size" => "32768"
    },
      "sda" => {
             "model" => "VBOX HARDDISK",
               "rev" => "1.0",
             "state" => "running",
           "timeout" => "30",
            "vendor" => "ATA",
        "rotational" => "1",
         "removable" => "0",
              "size" => "81920000"
    }
```
