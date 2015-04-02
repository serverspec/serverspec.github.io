---
layout: layout
title: Resource Types
---

<script src="http://code.jquery.com/jquery-1.11.0.min.js"></script>
<script>
  $(document).ready(function() {
    var resource_types = $('#main_content');

    $(document).on('scroll', function (event) {
      console.log(event);
      var past_breakpoint = $(this).scrollTop() > 443
      resource_types.toggleClass("fixed-resource-types", past_breakpoint);
    });
  });
</script>

## Resource Types

<nav class="resource-types">
  [bond](#bond)
| [bridge](#bridge)
| [cgroup](#cgroup)
| [command](#command)
| [cron](#cron)
| [default_gateway](#default_gateway)
| [docker_container](#docker_container)
| [docker_image](#docker_image)
| [file](#file)
| [group](#group)
| [host](#host)
| [iis\_app\_pool](#iis_app_pool)
| [iis\_website](#iis_website)
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
| [ppa](#ppa)
| [process](#process)
| [routing_table](#routing_table)
| [selinux](#selinux)
| [service](#service)
| [user](#user)
| [x509_certificate](#x509_certificate)
| [x509\_private\_key](#x509_private_key)
| [windows\_feature](#windows_feature)
| [windows\_registry\_key](#windows_registry_key)
| [yumrepo](#yumrepo)
| [zfs](#zfs)
</nav>

----

**Note:** In the following examples, due to my preference I’m using `should` syntax, but Serverspec works well on `expect` syntax.

----

*You can use more strict grammar syntax like ``be_a_file`` instead of ``be_file`` with all resource types.*

----

{% capture bond %}{% include bond.md %}{% endcapture %}
{{ bond | markdownify }}

----

{% capture bridge %}{% include bridge.md %}{% endcapture %}
{{ bridge | markdownify }}

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

{% capture docker_container %}{% include docker_container.md %}{% endcapture %}
{{ docker_container | markdownify }}

----

{% capture docker_image %}{% include docker_image.md %}{% endcapture %}
{{ docker_image | markdownify }}

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

{% capture iis_app_pool %}{% include iis_app_pool.md %}{% endcapture %}
{{ iis_app_pool | markdownify }}

----

{% capture iis_website %}{% include iis_website.md %}{% endcapture %}
{{ iis_website | markdownify }}

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

{% capture ppa %}{% include ppa.md %}{% endcapture %}
{{ ppa | markdownify }}

----

{% capture process %}{% include process.md %}{% endcapture %}
{{ process | markdownify }}

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

{% capture x509_certificate %}{% include x509_certificate.md %}{% endcapture %}
{{ x509_certificate | markdownify }}

----

{% capture x509_private_key %}{% include x509_private_key.md %}{% endcapture %}
{{ x509_private_key | markdownify }}

----

{% capture windows_feature %}{% include windows_feature.md %}{% endcapture %}
{{ windows_feature | markdownify }}

----

{% capture windows_registry_key %}{% include windows_registry_key.md %}{% endcapture %}
{{ windows_registry_key | markdownify }}

----

{% capture yumrepo %}{% include yumrepo.md %}{% endcapture %}
{{ yumrepo | markdownify }}

----

{% capture zfs %}{% include zfs.md %}{% endcapture %}
{{ zfs | markdownify }}
