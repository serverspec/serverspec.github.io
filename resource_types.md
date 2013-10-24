---
layout: layout
title: Resource Types
---

## Resource Types

<nav>
  [cgroup](#cgroup)
| [command](#command)
| [cron](#cron)
| [default_gateway](#default_gateway)
| [file](#file)
| [group](#group)
| [host](#host)
| [interface](#interface)
| [ipfilter](#ipfilter)
| [ipnat](#ipnat)
| [iptables](#iptables)
| [kernel_module](#kernel_module)
| [linux\_kernel\_parameter](#linux_kernel_parameter)
| [lxc](#lxc)
| [mail\_alias](#mail_alias)
| [package](#package)
| [php_config](#php_config)
| [port](#port)
| [routing_table](#routing_table)
| [selinux](#selinux)
| [service](#service)
| [user](#user)
| [yumrepo](#yumrepo)
| [zfs](#zfs)
</nav>

----

**Note:** In these examples, I'm using ``should`` syntax instead of ``expect`` syntax because I think ``should`` syntax is more readable than ``expect`` syntax and I like it.

Using ``expect`` syntax is recommended way because adding ``should`` to every object causes failures when used with BasicObject-subclassed proxy objects.

But the one-liner syntax used with the examples in this page doesn't add ``should`` to any objects, so this syntax doesn't cause the above problems.That's why I'm using the one-liner ``should`` syntax.

Please see [the document of rspec-expectations](https://github.com/rspec/rspec-expectations/blob/master/Should.md) if you'd like to know the detail of the issue.

----

*You can use more strict grammer syntax like ``be_a_file`` instead of ``be_file`` with all resource types.*

----

{% capture cgroup %}{% include cgroup.md %}{% endcapture %}
{{ cgroup | markdownify }}

----

{% capture command %}{% include command.md %}{% endcapture %}
{{ command | markdownify }}

----

{% capture cron %}{% include cron.md %}{% endcapture %}
{{ cron | markdownify }}

----

{% capture default_gateway %}{% include default_gateway.md %}{% endcapture %}
{{ default_gateway | markdownify }}

----

{% capture file %}{% include file.md %}{% endcapture %}
{{ file | markdownify }}

----

{% capture group %}{% include group.md %}{% endcapture %}
{{ group | markdownify }}

----

{% capture host %}{% include host.md %}{% endcapture %}
{{ host | markdownify }}

----

{% capture interface %}{% include interface.md %}{% endcapture %}
{{ interface | markdownify }}

----

{% capture ipfilter %}{% include ipfilter.md %}{% endcapture %}
{{ ipfilter | markdownify }}

----

{% capture ipnat %}{% include ipnat.md %}{% endcapture %}
{{ ipnat | markdownify }}

----

{% capture iptables %}{% include iptables.md %}{% endcapture %}
{{ iptables | markdownify }}

----

{% capture kernel_module %}{% include kernel_module.md %}{% endcapture %}
{{ kernel_module | markdownify }}

----

{% capture linux_kernel_parameter %}{% include linux_kernel_parameter.md %}{% endcapture %}
{{ linux_kernel_parameter | markdownify }}

----

{% capture lxc %}{% include lxc.md %}{% endcapture %}
{{ lxc | markdownify }}

----

{% capture mail_alias %}{% include mail_alias.md %}{% endcapture %}
{{ mail_alias | markdownify }}

----

{% capture package %}{% include package.md %}{% endcapture %}
{{ package | markdownify }}

----

{% capture php_config %}{% include php_config.md %}{% endcapture %}
{{ php_config | markdownify }}

----

{% capture port %}{% include port.md %}{% endcapture %}
{{ port | markdownify }}

----

{% capture routing_table %}{% include routing_table.md %}{% endcapture %}
{{ routing_table | markdownify }}

----

{% capture selinux %}{% include selinux.md %}{% endcapture %}
{{ selinux | markdownify }}

----

{% capture service %}{% include service.md %}{% endcapture %}
{{ service | markdownify }}

----

{% capture user %}{% include user.md %}{% endcapture %}
{{ user | markdownify }}

----

{% capture yumrepo %}{% include yumrepo.md %}{% endcapture %}
{{ yumrepo | markdownify }}

----

{% capture zfs %}{% include zfs.md %}{% endcapture %}
{{ zfs | markdownify }}
