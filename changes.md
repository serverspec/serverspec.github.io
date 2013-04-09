---
layout: layout
title: changes
---

## Changes

### 0.2.2
 * [Add be_zfs matcher](https://github.com/mizzy/serverspec/pull/40)
 * [Support multiple properties with be_zfs mathcer](https://github.com/mizzy/serverspec/pull/41)
 * [Fix stat commands for exact match](https://github.com/mizzy/serverspec/pull/43)
 
### 0.2.1
 * [Move backends and OS helpers to separate directories](https://github.com/mizzy/serverspec/pull/36)
 * [Fix installed_by_gem edge effect](https://github.com/mizzy/serverspec/pull/37)
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
