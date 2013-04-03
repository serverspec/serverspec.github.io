---
layout: layout
title: changes
---

## Changes

### 0.1.4

 * Be\_running matcher runs check\_process() if check\_running() returns "stopped".
   * [Pull Request #31](https://github.com/mizzy/serverspec/pull/31)
 * [View Diff](https://github.com/mizzy/serverspec/compare/v0.1.3...v0.1.4)

### 0.1.3

 * Change the command of check_process() from "ps -e" to "ps aux"
   * [Pull Request #28](https://github.com/mizzy/serverspec/pull/28)
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
