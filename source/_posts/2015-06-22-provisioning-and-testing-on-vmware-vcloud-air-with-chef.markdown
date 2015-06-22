---
layout: post
title: "Provisioning and Testing on VMware vCloud Air with Chef"
date: 2015-06-22 10:32:57 -0600
comments: true
categories: 
---

[Taylor](https://github.com/taylor)@[Vulk](http://vulk.co) and I teamed up with [Chef](http://chef.io) to bring [VMWare vCloud Air](http://vcloud.vmware.com/) support to the chef toolchain including knife, chef-provisioning, and test-kitchen.

It's been a bit tricky with a few gotchas that we've worked around, mosty around how authentication to the base images is configured.

[Documentation](https://github.com/ii/chef-provisioning/blob/vcair/docs/providers/vcair.md#vcloud-air-provider) was created for the [vcair](https://github.com/chef/chef-provisioning-fog/pull/107) support for [chef-provisioning-fog](https://github.com/chef/chef-provisioning-fog)

We wrote [kitchen-vcair](https://github.com/vulk/kitchen-vcair) to add support for [test-kitchen](http://kitchen.ci)

Windows and linux vm walkthroughs where created for for [chef-provisioning](https://github.com/vulk/chef-metal/blob/vcair/docs/providers/vcair.md#linux-vm-video-walkthru) and [test-kitchen](https://github.com/vulk/kitchen-vcair#walkthru-of-kitchen-vcair-for-linux-guests).
