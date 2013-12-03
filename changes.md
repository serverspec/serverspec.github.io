---
layout: layout
title: Changes
---

## Changes

### 0.13.0

 * [Move Serverspec::Commands::* to SpecInfra::Command::*](https://github.com/serverspec/serverspec/pull/302)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.12.0...v0.13.0)

### 0.12.0

 * [Use specinfra.Specinfra is a common layer of serverspec and configspec.](https://github.com/serverspec/serverspec/pull/301)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.11.5...v0.12.0)

### 0.11.5

 * [Ensure no Ruby envvars are present when running command](https://github.com/serverspec/serverspec/pull/300)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.11.4...v0.11.5)

### 0.11.4

 * [Add Solaris 10 capability to serverspec](https://github.com/serverspec/serverspec/pull/298)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.11.3...v0.11.4)

### 0.11.3

 * Delete OS type cache by mistake, so recover it
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.11.2...v0.11.3)

### 0.11.2

 * [check_os returns os release (but currently support redhat only)](https://github.com/serverspec/serverspec/pull/295)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.11.1...v0.11.2)

### 0.11.1

 * [Don't set HostName gotten by vagrant ssh-config to c.host](https://github.com/serverspec/serverspec/pull/294)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.11.0...v0.11.1)

### 0.11.0

 * [Introduce property instead of attr](https://github.com/serverspec/serverspec/pull/293)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.10.13...v0.11.0)

### 0.10.13

 * [Allow to use '_' and '-' as vagrant machine name](https://github.com/serverspec/serverspec/pull/290)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.10.12...v0.10.13)

### 0.10.12

 * [Include tcp6 & udp6 as port protocol](https://github.com/serverspec/serverspec/pull/288)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.10.11...v0.10.12)

### 0.10.11

 * [Use IO#gets instead of Kernel#gets in serverspec-init](https://github.com/serverspec/serverspec/pull/287)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.10.10...v0.10.11)

### 0.10.10

 * [Support LXC](https://github.com/serverspec/serverspec/pull/285)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.10.9...v0.10.10)

### 0.10.9

 * [Replace CRLF with LF of STDOUT when SSH](https://github.com/serverspec/serverspec/pull/284)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.10.8...v0.10.9)

### 0.10.8

 * [Support its(:content) for file resource type](https://github.com/serverspec/serverspec/pull/281)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.10.7...v0.10.8)

### 0.10.7

 * [Windows: support for testing commands, plus a fix around windows registry key](https://github.com/serverspec/serverspec/pull/282)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.10.6...v0.10.7)

### 0.10.6

 * [Command type returns stdout, so you can use any matchers you like to the stdout](https://github.com/serverspec/serverspec/pull/280)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.10.5...v0.10.6)

### 0.10.5

 * [Add cgroup resource type](https://github.com/serverspec/serverspec/pull/279)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.10.4...v0.10.5)

### 0.10.4

 * [Fix how to find a service name and add some specs for Windows support](https://github.com/serverspec/serverspec/pull/275)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.10.3...v0.10.4)

### 0.10.3

 * [Ignore case of monit result](https://github.com/serverspec/serverspec/pull/274)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.10.2...v0.10.3)

### 0.10.2

 * [Support Plamo Linux](https://github.com/serverspec/serverspec/pull/273)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.10.1...v0.10.2)

### 0.10.0

 * [Fix how to check service running](https://github.com/serverspec/serverspec/pull/266)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.9.8...v0.10.0)

### 0.9.8

 * [Fix to return correct exit status](https://github.com/serverspec/serverspec/pull/262)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.9.7...v0.9.8)

### 0.9.7

 * [Add be\_installed.by('cpan')](https://github.com/serverspec/serverspec/pull/260)
 * [Add be\_installed.by('pear')](https://github.com/serverspec/serverspec/pull/261)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.9.6...v0.9.7)

### 0.9.6

 * [Fix a typo](https://github.com/serverspec/serverspec/pull/258)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.9.5...v0.9.6)

### 0.9.5

 * [Enable to configure a sudo prompt](https://github.com/serverspec/serverspec/pull/256)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.9.4...v0.9.5)

### 0.9.4

 * [Fix class name and specs for AIX](https://github.com/serverspec/serverspec/pull/247)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.9.3...v0.9.4)

### 0.9.3

 * [Support FreeBSD](https://github.com/serverspec/serverspec/pull/161)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.9.2...v0.9.3)

### 0.9.2

 * [Support AIX](https://github.com/serverspec/serverspec/pull/246)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.9.1...v0.9.2)

### 0.9.1

 * Fix a bug of serverspec-init
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.9.0...v0.9.1)

### 0.9.0

 * [Support Windows OS](https://github.com/serverspec/serverspec/pull/244)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.8.1...v0.9.0)

### 0.8.1

 * Fix a bug of check_mail_alias()
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.8.0...v0.8.1)

### 0.8.0

 * [Add mail alias resource type](https://github.com/serverspec/serverspec/pull/241)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.13...v0.8.0)

### 0.7.13

 * [Fix check_link() for Darwin](https://github.com/serverspec/serverspec/pull/240)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.12...v0.7.13)

### 0.7.12

 * [Add pip to package provider](https://github.com/serverspec/serverspec/pull/237)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.11...v0.7.12)

### 0.7.11

 * [Also use -F option with grep](https://github.com/serverspec/serverspec/pull/233)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.10...v0.7.11)

### 0.7.10

 * [Add check_zfs to Linux commands](https://github.com/serverspec/serverspec/pull/231)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.9...v0.7.10)

### 0.7.9

 * [Add with\_version to be\_installed matcher for Debian](https://github.com/serverspec/serverspec/pull/230)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.8...v0.7.9)

### 0.7.8

 * [Add have\_ipv4\_address matcher to interface resource](https://github.com/serverspec/serverspec/pull/228)
 * [Add capability to provide an alternate path for sudo](https://github.com/serverspec/serverspec/pull/229)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.7...v0.7.8)

### 0.7.7

 * [Get correct string from regexp in shell escape method](https://github.com/serverspec/serverspec/pull/227)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.6...v0.7.7)

### 0.7.6

 * [Specify /bin/sh explicitly for the users don't have valid login shell](https://github.com/serverspec/serverspec/pull/226)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.5...v0.7.6)

### 0.7.5

 * [Fix how to pass the argument to grep](https://github.com/serverspec/serverspec/pull/224)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.4...v0.7.5)


### 0.7.4

 * [Fix regular expression for build_command()](https://github.com/serverspec/serverspec/pull/223)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.3...v0.7.4)

### 0.7.3

 * [Add match_sha256checksum matcher of file type](https://github.com/serverspec/serverspec/pull/222)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.2...v0.7.3)

### 0.7.2

 * [Serverspec-init climbs up the directory tree to looking for the Vagrantfile](https://github.com/serverspec/serverspec/pull/221)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.1...v0.7.2)

### 0.7.1

 * [Fix regular expression for build_command()](https://github.com/serverspec/serverspec/pull/220)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.7.0...v0.7.1)

### 0.7.0

 * [Add sudo and env PATH to each command](https://github.com/serverspec/serverspec/pull/219)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.30...v0.7.0)

### 0.6.30

 * [Omit brackets when be_permissive and be_enforcing of selinux resource type](https://github.com/serverspec/serverspec/pull/218)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.29...v0.6.30)

### 0.6.29

 * [Fix selinux resource type to work correctly even if selinux related files are not installed](https://github.com/serverspec/serverspec/pull/217)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.28...v0.6.29)

### 0.6.28

 * [Fix check_listening for Solaris](https://github.com/serverspec/serverspec/pull/214)
 * [Fix check_listening_with_protocol for Solaris](https://github.com/serverspec/serverspec/pull/215)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.27...v0.6.28)

### 0.6.27

 * [Add be\_monitored\_by('god') for service resource type](https://github.com/serverspec/serverspec/pull/208)
 * [Add command test for be_running.under('supervisor')](https://github.com/serverspec/serverspec/pull/213)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.26...v0.6.27)

### 0.6.26

 * [Fix custom failure message duplication](https://github.com/serverspec/serverspec/pull/211)
 * [Fix check\_running\_under\_supervisor](https://github.com/serverspec/serverspec/pull/210)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.25...v0.6.26)

### 0.6.25

 * [Add php_config resource type](https://github.com/serverspec/serverspec/pull/196)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.24...v0.6.25)

### 0.6.24

 * [Add default run level in matcher definition](https://github.com/serverspec/serverspec/pull/206)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.23...v0.6.24)

### 0.6.23

 * [Add be_installed.by('rpm') support](https://github.com/serverspec/serverspec/pull/203)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.22...v0.6.23)

### 0.6.22

 * [Fix check\_intalled and check\_running for Solaris family](https://github.com/serverspec/serverspec/pull/202)
 * [Add Solaris 11 support](https://github.com/serverspec/serverspec/pull/201)
 * [Add be_listening.with(protocol) to port type](https://github.com/serverspec/serverspec/pull/200)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.21...v0.6.22)

### 0.6.21

 * [Fix a bug of file contain matcher](https://github.com/serverspec/serverspec/pull/197)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.20...v0.6.21)

### 0.6.20

 * [Fix SmartOS detection](https://github.com/serverspec/serverspec/pull/193)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.19...v0.6.20)

### 0.6.19

 * [Fix check_os to detect Solaris](https://github.com/serverspec/serverspec/pull/192)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.18...v0.6.19)

### 0.6.18

 * [serverspec-init reads Vagrantfile to generate settings](https://github.com/serverspec/serverspec/pull/191)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.17...v0.6.18)

### 0.6.17

 * [Support be_running.under('upstart')](https://github.com/serverspec/serverspec/pull/186)
 * [Add be\_monitored\_by to service type](https://github.com/serverspec/serverspec/pull/187)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.16...v0.6.17)

### 0.6.16

 * [Support SmartOS](https://github.com/serverspec/serverspec/pull/175)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.15...v0.6.16)


### 0.6.15

 * [Fix be\_enabled.with\_level and add specs](https://github.com/serverspec/serverspec/pull/173)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.14...v0.6.15)

### 0.6.14(yanked)

 * [Remove .with\_level from be\_running matcher](https://github.com/serverspec/serverspec/pull/172)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.13...v0.6.14)

### 0.6.13

 * [Add with\_level to be\_enabled matcher](https://github.com/serverspec/serverspec/pull/171)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.12...v0.6.13)

### 0.6.12

 * [Add interface resource type](https://github.com/serverspec/serverspec/pull/169)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.11...v0.6.12)

### 0.6.11

 * [Remove `-s sh` of check_access command](https://github.com/serverspec/serverspec/pull/168)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.10...v0.6.11)

### 0.6.10

 * [Support version checking with be_installed matcher for Solaris](https://github.com/serverspec/serverspec/pull/166)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.9...v0.6.10)

### 0.6.9

 * [Add check_reachable to Commands::Solaris](https://github.com/serverspec/serverspec/pull/165)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.8...v0.6.9)

### 0.6.8

 * [Fix check_yumrepo command](https://github.com/serverspec/serverspec/pull/163)
 * [Support `with_version` chain with be_installed matcher without `by` chain (But currently supported only on Red Hat family)](https://github.com/serverspec/serverspec/pull/164)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.7...v0.6.8)

### 0.6.7

 * [Add alternative syntax tests for file resource type](https://github.com/serverspec/serverspec/pull/159)
 * [Add yumrepo resource type](https://github.com/serverspec/serverspec/pull/162)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.6...v0.6.7)

### 0.6.6

 * [Support be_installed.by('pecl')](https://github.com/serverspec/serverspec/pull/157)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.5...v0.6.6)

### 0.6.5

 * [Add be_socket matcher](https://github.com/serverspec/serverspec/pull/156)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.4...v0.6.5)

### 0.6.4

 * [Update gemspec](https://github.com/serverspec/serverspec/pull/154)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.3...v0.6.4)

### 0.6.3

 * [Abort if sudo password is not set when using Backend::Ssh and user is not root](https://github.com/serverspec/serverspec/pull/152)
 * [Show the message of exception object when test fails](https://github.com/serverspec/serverspec/pull/153)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.2...v0.6.3)

### 0.6.2

 * [Add OS type caching to Helper::DetectOS](https://github.com/serverspec/serverspec/pull/151)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.1...v0.6.2)

### 0.6.1

 * [Fix Debian service detection](https://github.com/serverspec/serverspec/pull/130)
 * [Add kernel_module resource type](https://github.com/serverspec/serverspec/pull/150)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.6.0...v0.6.1)

### 0.6.0

 * [Remove obsoleted syntaxes, Puppet backend ans so on](https://github.com/serverspec/serverspec/pull/148)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.5.8...v0.6.0)

### 0.5.8

 * [Add env in front of PATH](https://github.com/serverspec/serverspec/pull/147)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.5.7...v0.5.8)

### 0.5.7

 * [Fix the bug of duplicating sudo with Backend::Ssh](https://github.com/serverspec/serverspec/pull/146)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.5.6...v0.5.7)

### 0.5.6

 * [Use Commands::Base without OS detection](https://github.com/serverspec/serverspec/pull/143)
 * [OS detection doesn't check RSpec.configuration.os now](https://github.com/serverspec/serverspec/pull/144)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.5.5...v0.5.6)

### 0.5.5

 * [Use Comands::Base automatically before OS detection](https://github.com/serverspec/serverspec/pull/142)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.5.4...v0.5.5)

### 0.5.4

 * [Make backend class singleton](https://github.com/serverspec/serverspec/pull/139)
 * [Pass example object to backend in before filter, not in matchers and types](https://github.com/serverspec/serverspec/pull/140)
 * [Add custom failure message for should_not](https://github.com/serverspec/serverspec/pull/141)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.5.3...v0.5.4)

### 0.5.3

 * [Fix a bug of check_installed on Debian squeeze](https://github.com/serverspec/serverspec/pull/138)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.5.2...v0.5.3)

### 0.5.2

 * [More strict checking for SELinux](https://github.com/serverspec/serverspec/pull/137)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.5.1...v0.5.2)

### 0.5.1

 * [Check both current status and setting in the config file of SELinux](https://github.com/serverspec/serverspec/pull/136)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.5.0...v0.5.1)

### 0.5.0

 * [\[EXPERIMENTAL\] Dynamic path and pre_command by let](https://github.com/serverspec/serverspec/pull/134)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.14...v0.5.0)


### 0.4.14

 * [Add npm to package provider](https://github.com/serverspec/serverspec/pull/132)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.13...v0.4.14)

### 0.4.13

 * [Add custom path to the command and remove default PATH setting](https://github.com/serverspec/serverspec/pull/133)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.12...v0.4.13)

### 0.4.12

 * [Change command path to relative](https://github.com/serverspec/serverspec/pull/129)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.11...v0.4.12)

### 0.4.11

 * [Add vagrant instance support](https://github.com/serverspec/serverspec/pull/128)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.10...v0.4.11)

### 0.4.10

 * [Fix commands.check\_mode and commands.get\_mode for compatibility with Mac OS X v10.4](https://github.com/serverspec/serverspec/pull/127)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.9...v0.4.10)

### 0.4.9

 * [Match gem version when multiple versions installed](https://github.com/serverspec/serverspec/pull/125)
 * [Precise version checking of installed by gem](https://github.com/serverspec/serverspec/pull/126)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.8...v0.4.9)

### 0.4.8

 * [Specify the absolute path of /sbin commands](https://github.com/serverspec/serverspec/pull/124)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.7...v0.4.8)

### 0.4.7

 * Update sample spec supporting new syntaxes generated by serverspec-init
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.6...v0.4.7)

### 0.4.6

 * [Show obsolete warning when using a string as a subject](https://github.com/serverspec/serverspec/pull/123)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.5...v0.4.6)

### 0.4.5

 * [Support explicit zfs subject type](https://github.com/serverspec/serverspec/pull/119)
 * [Support explicit ipnat subject type](https://github.com/serverspec/serverspec/pull/120)
 * [Support explicit ipfilter subject type](https://github.com/serverspec/serverspec/pull/121)
 * [Support have_propety with service type for Solaris](https://github.com/serverspec/serverspec/pull/122)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.4...v0.4.5)

### 0.4.4

 * [Support explicit selinux subject type](https://github.com/serverspec/serverspec/pull/117)
 * [Support explicit user and group subject types](https://github.com/serverspec/serverspec/pull/118)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.3...v0.4.4)

### 0.4.3

 * [Support explicit linux kernel parameter subject type](https://github.com/serverspec/serverspec/pull/112)
 * [Support explicit iptables subject type](https://github.com/serverspec/serverspec/pull/113)
 * [Support explicit host subject type](https://github.com/serverspec/serverspec/pull/114)
 * [Support explicit routing table subject type](https://github.com/serverspec/serverspec/pull/115)
 * [Support explicit default gateway subject type](https://github.com/serverspec/serverspec/pull/116)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.2...v0.4.3)

### 0.4.2

 * [Support explicit cron subject type](https://github.com/serverspec/serverspec/pull/110)
 * [Support explicit command subject type](https://github.com/serverspec/serverspec/pull/111)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.1...v0.4.2)

### 0.4.1

 * [Support explicit package subject type](https://github.com/serverspec/serverspec/pull/107)
 * [Support explicit port subject type](https://github.com/serverspec/serverspec/pull/108)
 * [Support explicit file subject type](https://github.com/serverspec/serverspec/pull/109)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.4.0...v0.4.1)

### 0.4.0

 * [Update gemspec](https://github.com/serverspec/serverspec/pull/106)
 * [Support explicit service subject type](https://github.com/serverspec/serverspec/pull/105)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.3.2...v0.4.0)


### 0.3.2

 * [Fix be_mode, be_executable, be_owned_by and be_grouped_into matcher on Darwin (OS X)](https://github.com/serverspec/serverspec/pull/103)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.3.1...v0.3.2)

### 0.3.1

 * [Support have_entry and be_default_gateway matchers for checking a routing table](https://github.com/serverspec/serverspec/pull/92)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.3.0...v0.3.1)

### 0.3.0

 * [Support the mechanism for handling host attributes](https://github.com/serverspec/serverspec/pull/98)
 * [Fix match_md5checksum matcher on Darwin (OS X)](https://github.com/serverspec/serverspec/pull/101)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.28...v0.3.0)


### 0.2.28

 * [Make runuser redhat-specific and use generic 'su' in other linuxes](https://github.com/serverspec/serverspec/pull/100)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.27...v0.2.28)

### 0.2.27

 * [Support checking read/write/execute access rights by a specific user](https://github.com/serverspec/serverspec/pull/99)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.26...v0.2.27)

### 0.2.26

 * [Support match_md5checksum matcher](https://github.com/serverspec/serverspec/pull/97)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.25...v0.2.26)

### 0.2.25

 * [Support Darwin (Mac OS X)](https://github.com/serverspec/serverspec/pull/95)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.24...v0.2.25)


### 0.2.24

 * [Fix bug of be_mounted matcher](https://github.com/serverspec/serverspec/pull/91)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.23...v0.2.24)


### 0.2.23

 * [Escape shell command arguments](https://github.com/serverspec/serverspec/pull/87)
 * [Show the command and its stdout message when should fails](https://github.com/serverspec/serverspec/pull/88)
 * [Add commands/linux.rb and move linux specific commands from base.rb to linux.rb](https://github.com/serverspec/serverspec/pull/89)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.22...v0.2.23)


### 0.2.22

 * [Support be_reachable matcher](https://github.com/serverspec/serverspec/pull/86)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.21...v0.2.22)

### 0.2.21

 * [Support Amazon Linux with Helper::DetectOS](https://github.com/serverspec/serverspec/pull/85)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.20...v0.2.21)

### 0.2.20

 * [Support be\_mounted and be\_resolvable matchers](https://github.com/serverspec/serverspec/pull/76)
 * [Support with and only\_with chains with be\_mounted matchers](https://github.com/serverspec/serverspec/pull/84)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.19...v0.2.20)

### 0.2.19
 * [Support have\_authorized\_key matcher](https://github.com/serverspec/serverspec/pull/75)
 * [Support check_gid for Solaris](https://github.com/serverspec/serverspec/pull/77)
 * [Support check\_login\_shell for Solaris](https://github.com/serverspec/serverspec/pull/78)
 * [Support check\_home\_directory for Solaris](https://github.com/serverspec/serverspec/pull/79)
 * [Change sysctl's path to fullpath for CentOS5](https://github.com/serverspec/serverspec/pull/80)
 * [Use getent instead of /etc/passwd](https://github.com/serverspec/serverspec/pull/81)
 * [Support check_running for gentoo](https://github.com/serverspec/serverspec/pull/82)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.18...v0.2.19)

### 0.2.18
 * [Fix command syntax error](https://github.com/serverspec/serverspec/pull/74)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.17...v0.2.18)

### 0.2.17
 * [Support have\_uid, have\_home\_directory, have\_login\_shell and have\_gid matchers](https://github.com/serverspec/serverspec/pull/71)
 * [Override check\_file\_contain\_within() for Solaris](https://github.com/serverspec/serverspec/pull/72)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.16...v0.2.17)

### 0.2.16
 * [Serverspec::Filter.filter_subject supports other than int](https://github.com/serverspec/serverspec/pull/70)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.15...v0.2.16)

### 0.2.15
 * [Some fixes in spec_helper created by serverspec-init](https://github.com/serverspec/serverspec/pull/68)
 * [Support linux kernel parameter checking](https://github.com/serverspec/serverspec/pull/69)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.14...v0.2.15)

### 0.2.14
 * [Support selinux matchers](https://github.com/serverspec/serverspec/pull/64)
 * [Change specs for serverspec itself](https://github.com/serverspec/serverspec/pull/65)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.13...v0.2.14)

### 0.2.13
 * Deprecate "get\_stdout" matcher.Use "return\_stdout" instead.
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.12...v0.2.13)

### 0.2.12
 * [Support generic command matchers](https://github.com/serverspec/serverspec/pull/61)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.11...v0.2.12)


### 0.2.11
 * [Support showing prompt for sudo password](https://github.com/serverspec/serverspec/pull/62)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.10...v0.2.11)

### 0.2.10
 * ["belong\_to\_group" matcher matches all groups](https://github.com/serverspec/serverspec/pull/59)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.9...v0.2.10)
 
### 0.2.9
 * [Fix bugs in OS auto detecting with Exec backend](https://github.com/serverspec/serverspec/pull/58)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.8...v0.2.9)


### 0.2.8
 * [Support detecting target host's OS automatically](https://github.com/serverspec/serverspec/pull/56)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.7...v0.2.8)

### 0.2.7
 * [Support have\_ipnat\_rule matcher for Solaris](https://github.com/serverspec/serverspec/pull/54)
 * [Support have\_svcprop and have\_svcprops matchers for Solaris](https://github.com/serverspec/serverspec/pull/55)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.6...v0.2.7)


### 0.2.6
 * [Support have\_ipfilter\_rule matcher for Solaris](https://github.com/serverspec/serverspec/pull/52)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.5...v0.2.6)

### 0.2.5
 * [Support handling sudo password](https://github.com/serverspec/serverspec/pull/51)
 * Some internal refactoring
   * [Send example to backend](https://github.com/serverspec/serverspec/pull/49)
   * [Simplify Exec backend with a method_missing method](https://github.com/serverspec/serverspec/pull/50)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.4...v0.2.5)

### 0.2.4
 * [Support be\_readable, be\_writable and be\_executable file matchers](https://github.com/serverspec/serverspec/pull/48)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.3...v0.2.4)

### 0.2.3
 * ["be\_running" matcher support a chain "under" and check\_running\_under\_supervisor](https://github.com/serverspec/serverspec/pull/44)
 * [Add dependency rspec to gemspec](https://github.com/serverspec/serverspec/pull/46)
 * [Change be\_installed\_by\_gem to be_installed.by('gem')](https://github.com/serverspec/serverspec/pull/47)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.2...v0.2.3)

### 0.2.2
 * [Add be_zfs matcher](https://github.com/serverspec/serverspec/pull/40)
 * [Support multiple properties with be_zfs mathcer](https://github.com/serverspec/serverspec/pull/41)
 * [Fix stat commands for exact match](https://github.com/serverspec/serverspec/pull/43)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.2.1...v0.2.2)

 
### 0.2.1
 * [Move backends and OS helpers to separate directories](https://github.com/serverspec/serverspec/pull/36)
 * [Fix installed\_by\_gem edge effect](https://github.com/serverspec/serverspec/pull/37)
 * [Add a Puppet backend](https://github.com/serverspec/serverspec/pull/38)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.1.7...v0.2.1)
 
### 0.1.7

 * [Support an Exec backend in addition to Ssh](https://github.com/serverspec/serverspec/pull/34)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.1.6...v0.1.7)

### 0.1.6

 * [Ignore "grep" in check_process()](https://github.com/serverspec/serverspec/pull/33)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.1.5...v0.1.6)

### 0.1.5

 * [Contain matcher supports some chains](https://github.com/serverspec/serverspec/pull/32)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.1.4...v0.1.5)

### 0.1.4

 * [Be\_running matcher runs check\_process() if check\_running() returns "stopped"](https://github.com/serverspec/serverspec/pull/31)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.1.3...v0.1.4)

### 0.1.3

 * [Change the command of check_process() from "ps -e" to "ps aux"](https://github.com/serverspec/serverspec/pull/28)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.1.2...v0.1.3)

### 0.1.2

 * Don't add sudo to ssh commands if ssh user is root
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.1.1...v0.1.2)

### 0.1.1

 * [Support get_stdout matcher](/matchers.html#commands)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.1.0...v0.1.1)

### 0.1.0

 * [Support have\_iptables\_rule matcher](/matchers.html#iptables)
 * [View Diff](https://github.com/serverspec/serverspec/compare/v0.0.19...v0.1.0)
