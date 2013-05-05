---
layout: layout
title: changes
---

## Changes

### 0.2.26

 * [Support be_reachable matcher](https://github.com/mizzy/serverspec/pull/86)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.21...v0.2.22)

### 0.2.21

 * [Support Amazon Linux with Helper::DetectOS](https://github.com/mizzy/serverspec/pull/85)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.20...v0.2.21)

### 0.2.20

 * [Support be\_mounted and be\_resolvable matchers](https://github.com/mizzy/serverspec/pull/76)
 * [Support with and only\_with chains with be\_mounted matchers](https://github.com/mizzy/serverspec/pull/84)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.19...v0.2.20)

### 0.2.19
 * [Support have\_authorized\_key matcher](https://github.com/mizzy/serverspec/pull/75)
 * [Support check_gid for Solaris](https://github.com/mizzy/serverspec/pull/77)
 * [Support check\_login\_shell for Solaris](https://github.com/mizzy/serverspec/pull/78)
 * [Support check\_home\_directory for Solaris](https://github.com/mizzy/serverspec/pull/79)
 * [Change sysctl's path to fullpath for CentOS5](https://github.com/mizzy/serverspec/pull/80)
 * [Use getent instead of /etc/passwd](https://github.com/mizzy/serverspec/pull/81)
 * [Support check_running for gentoo](https://github.com/mizzy/serverspec/pull/82)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.18...v0.2.19)

### 0.2.18
 * [Fix command syntax error](https://github.com/mizzy/serverspec/pull/74)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.17...v0.2.18)

### 0.2.17
 * [Support have\_uid, have\_home\_directory, have\_login\_shell and have\_gid matchers](https://github.com/mizzy/serverspec/pull/71)
 * [Override check\_file\_contain\_within() for Solaris](https://github.com/mizzy/serverspec/pull/72)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.16...v0.2.17)

### 0.2.16
 * [Serverspec::Filter.filter_subject supports other than int](https://github.com/mizzy/serverspec/pull/70)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.15...v0.2.16)

### 0.2.15
 * [Some fixes in spec_helper created by serverspec-init](https://github.com/mizzy/serverspec/pull/68)
 * [Support linux kernel parameter checking](https://github.com/mizzy/serverspec/pull/69)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.14...v0.2.15)

### 0.2.14
 * [Support selinux matchers](https://github.com/mizzy/serverspec/pull/64)
 * [Change specs for serverspec itself](https://github.com/mizzy/serverspec/pull/65)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.13...v0.2.14)

### 0.2.13
 * Deprecate "get\_stdout" matcher.Use "return\_stdout" instead.
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.12...v0.2.13)

### 0.2.12
 * [Support generic command matchers](https://github.com/mizzy/serverspec/pull/61)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.11...v0.2.12)


### 0.2.11
 * [Support showing prompt for sudo password](https://github.com/mizzy/serverspec/pull/62)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.10...v0.2.11)

### 0.2.10
 * ["belong\_to\_group" matcher matches all groups](https://github.com/mizzy/serverspec/pull/59)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.9...v0.2.10)
 
### 0.2.9
 * [Fix bugs in OS auto detecting with Exec backend](https://github.com/mizzy/serverspec/pull/58)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.8...v0.2.9)


### 0.2.8
 * [Support detecting target host's OS automatically](https://github.com/mizzy/serverspec/pull/56)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.7...v0.2.8)

### 0.2.7
 * [Support have\_ipnat\_rule matcher for Solaris](https://github.com/mizzy/serverspec/pull/54)
 * [Support have\_svcprop and have\_svcprops matchers for Solaris](https://github.com/mizzy/serverspec/pull/55)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.6...v0.2.7)


### 0.2.6
 * [Support have\_ipfilter\_rule matcher for Solaris](https://github.com/mizzy/serverspec/pull/52)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.5...v0.2.6)

### 0.2.5
 * [Support handling sudo password](https://github.com/mizzy/serverspec/pull/51)
 * Some internal refactoring
   * [Send example to backend](https://github.com/mizzy/serverspec/pull/49)
   * [Simplify Exec backend with a method_missing method](https://github.com/mizzy/serverspec/pull/50)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.4...v0.2.5)

### 0.2.4
 * [Support be\_readable, be\_writable and be\_executable file matchers](https://github.com/mizzy/serverspec/pull/48)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.3...v0.2.4)

### 0.2.3
 * ["be\_running" matcher support a chain "under" and check\_running\_under\_supervisor](https://github.com/mizzy/serverspec/pull/44)
 * [Add dependency rspec to gemspec](https://github.com/mizzy/serverspec/pull/46)
 * [Change be\_installed\_by\_gem to be_installed.by('gem')](https://github.com/mizzy/serverspec/pull/47)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.2...v0.2.3)

### 0.2.2
 * [Add be_zfs matcher](https://github.com/mizzy/serverspec/pull/40)
 * [Support multiple properties with be_zfs mathcer](https://github.com/mizzy/serverspec/pull/41)
 * [Fix stat commands for exact match](https://github.com/mizzy/serverspec/pull/43)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.2.1...v0.2.2)

 
### 0.2.1
 * [Move backends and OS helpers to separate directories](https://github.com/mizzy/serverspec/pull/36)
 * [Fix installed\_by\_gem edge effect](https://github.com/mizzy/serverspec/pull/37)
 * [Add a Puppet backend](https://github.com/mizzy/serverspec/pull/38)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.1.7...v0.2.1)
 
### 0.1.7

 * [Support an Exec backend in addition to Ssh](https://github.com/mizzy/serverspec/pull/34)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.1.6...v0.1.7)

### 0.1.6

 * [Ignore "grep" in check_process()](https://github.com/mizzy/serverspec/pull/33)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.1.5...v0.1.6)

### 0.1.5

 * [Contain matcher supports some chains](https://github.com/mizzy/serverspec/pull/32)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.1.4...v0.1.5)

### 0.1.4

 * [Be\_running matcher runs check\_process() if check\_running() returns "stopped"](https://github.com/mizzy/serverspec/pull/31)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.1.3...v0.1.4)

### 0.1.3

 * [Change the command of check_process() from "ps -e" to "ps aux"](https://github.com/mizzy/serverspec/pull/28)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.1.2...v0.1.3)

### 0.1.2

 * Don't add sudo to ssh commands if ssh user is root
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.1.1...v0.1.2)

### 0.1.1

 * [Support get_stdout matcher](/matchers.html#commands)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.1.0...v0.1.1)

### 0.1.0

 * [Support have\_iptables\_rule matcher](/matchers.html#iptables)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.0.19...v0.1.0)
