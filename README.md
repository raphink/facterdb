facterdb
========

[![Build Status](https://img.shields.io/travis/mcanevet/facterdb/master.svg)](https://travis-ci.org/mcanevet/facterdb)
[![Code Climate](https://img.shields.io/codeclimate/github/mcanevet/facterdb.svg)](https://codeclimate.com/github/mcanevet/facterdb)
[![Gem Version](https://img.shields.io/gem/v/facterdb.svg)](https://rubygems.org/gems/facterdb)
[![Gem Downloads](https://img.shields.io/gem/dt/facterdb.svg)](https://rubygems.org/gems/facterdb)
[![Coverage Status](https://img.shields.io/coveralls/mcanevet/facterdb.svg)](https://coveralls.io/r/mcanevet/facterdb?branch=master)

A Gem that contains a lot of facts for a lot of Operating Systems.

Usage
-----

```ruby
require 'facterdb'
include FacterDB
FacterDB::get_os_facts()
```

Returns an Array of Hash containing the whole facts database.

TODO: find a way to filter out facts.

Facter versions supported
-------------------------
* 1.6
* 1.7
* 2.0
* 2.1
* 2.2
* 2.3
* 2.4

Operating Systems supported
-----------------------------------------------
* ArchLinux
* CentOS 5
* CentOS 6
* CentOS 7
* Debian 6
* Debian 7
* Debian 8
* Fedora 19
* FreeBSD 9
* FreeBSD 10
* Gentoo
* OpenSuse 12
* OpenSuse 13
* Oracle 5
* Oracle 6
* Oracle 7
* RedHat 5
* RedHat 6
* RedHat 7
* Scientific 5
* Scientific 6
* Scientific 7
* SLES 11
* Solaris 11
* Ubuntu 10.04
* Ubuntu 12.04
* Ubuntu 14.04
* Ubuntu 14.10
* Ubuntu 15.04

Add new Operating System support
--------------------------------

There is `Vagrantfile` to automagically populate `facts` directory by spawning a new VM and launches a provisioning scripts.

```
$ cd facts
$ vagrant up --provision
```

Create i386 facts from x86_64's ones

```
for file in facts/*/*-x86_64.facts; do cat $file | sed -e 's/x86_64/i386/' -e 's/amd64/i386/' > $(echo $file | sed 's/x86_64/i386/'); done
```
Create RedHat, Scientific, OracleLinux facts from CentOS's ones

```
for file in facts/*/centos-*.facts; do cat $file | sed -e 's/CentOS/RedHat/' > $(echo $file | sed 's/centos/redhat/'); done
for file in facts/*/centos-*.facts; do cat $file | sed -e 's/CentOS/Scientific/' > $(echo $file | sed 's/centos/scientific/'); done
for file in facts/*/centos-*.facts; do cat $file | sed -e 's/CentOS/OracleLinux/' > $(echo $file | sed 's/centos/oraclelinux/'); done
```
