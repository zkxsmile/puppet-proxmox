# proxmox

A "one click" Proxmox installation over a fresh Debian install.

## Table of Contents

1. [Description](#description)
1. [Setup - The basics of getting started with proxmox](#setup)
    * [What proxmox affects](#what-proxmox-affects)
    * [Setup requirements](#setup-requirements)
    * [Beginning with proxmox](#beginning-with-proxmox)
1. [Usage - Configuration options and additional functionality](#usage)
1. [Limitations - OS compatibility, etc.](#limitations)
1. [Development - Guide for contributing to the module](#development)

## Description

The purpose of this module is to provision Proxmox servers at providers who don't offer the option.
You just order a Debian 10, run puppet and voila! You have a default Proxmox server.

We do not plan on adding features for anything that can be done via Proxmox's web interface, command line, terraform... 

## Setup

### What proxmox affects

The module only does one thing, install Proxmox. But Proxmox itself changes a lot of things during the installation process (just look at how long it takes).
So, the resulting product of a successful puppet run should no longer be considered as a Debian, but a Proxmox server.
They have a lot in common, but when you have a specific problem or need, go to Proxmox's documentation first.

### Setup Requirements

* A clean Debian install
* A correct hostname configuration:

**/etc/hosts** file should at least contain IPv4 config:
```
127.0.0.1 localhost.localdomain localhost
<public_server_ip>  proxmox.domain.com proxmox
<puppetserver_ip>   puppet
```
**/etc/hostname** should just contain the fqdn (proxmox.domain.com)

* Install puppet-agent
* puppet-run
* Profit!

## Usage

```
include proxmox
```

## Limitations

There might be some edge cases because our only test machine is based on Hetzners Debian 10.4 minimal amd64.
It seems standard enough but maybe other providers put stuff that gets in the way, or Hetzner does something 
we didn't notice and we need to do it on other servers too...

We didn't write any tests, help with that would be very welcome.

## Development

Start by submitting an issue that explains what you want to do.
Branch if you are in the org, fork if you are not. Then, make a pull request.

## Links

[1]: https://puppet.com/docs/pdk/latest/pdk_generating_modules.html
[2]: https://puppet.com/docs/puppet/latest/puppet_strings.html
[3]: https://puppet.com/docs/puppet/latest/puppet_strings_style.html
