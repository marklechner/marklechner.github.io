---
layout: post
title:  "Setting up Kali"
date:   2020-01-03 12:00:00 -0500
categories: tech 
---

## Enable and set up ssh
* Download kali image
* Download and install virtualbox
* Create new VM and choose debian
* Allocate memory (go for 4gb if you can) and static disk (min 20gb but go for 30gb if you can)
* Before installing image make sure to add secondary network adapter (hostonly)
* Install Kali
* Verify secondary interface eth1 is up and has ip assigned to it by running `ip addr`
* Change root passowrd by running `sudo passwd`
* Install/update openssh-server (might not be necesarry): `apt-get install openssh-server`
* Setup persistency
    * remove levels: `update-rc.d -f ssh remove`
    * add default run level: `update-rc.d -f ssh defaults`
* replace default keys with newly generated set
    * `mkdir /etc/ssh/default_keys_bkp`
    * `mv /etc/ssh/ssh_host_* /etc/ssh/default_keys_bkp/`
    * `dpkg-reconfigure openssh-server`
* ensure PermitgRootLogin is set to yes in /etc/ssh/sshd_config 
* restart ssh: `sudo service ssh restart`
* ensure ssh starts automatically upon boot: `update-rc.d -f ssh enable 2 3 4 5`

## Set up key authentication (optional)
* on kali: `mkdir /root/.ssh`
* on host machine generate keypair unless you have ~/.ssh/id_rsa.pub in place already: `ssh-keygen -t rsa`
* then copy your public key over to authorized_hosts:
    * `scp ~/.ssh/id_rsa.pub root@<kali_ip>:/root/.ssh/authorized_keys`

## Set up Burp
### Disable detectportal.firefox.com
This is to avoid noise form detectportal to pollute our intercept
* enter about:config in searchbar
* look or search for network.captive-portal-service.enabled and set it to false

### Enable proxy
* enter about:preferences in searchbar
* select network settings
* manual proxy configuration
* use 127.0.0.1 with port 8080 for HTTP proxy
* also enable it for all other protocols

### Install Burp CA Cert
* With Burp running, visit http://burp in your browser and click the "CA Certificate" link to download and save your Burp CA certificate
* Go to "Privacy and Security" / "View Certificates"
* Select the "Authorities" tabClick "Import", select the Burp CA certificate file that you previously saved and click “Open”
* In the dialog box that pops up, check the box "Trust this CA to identify web sites", and click "OK".
* Close all dialogs and restart Firefox.
* If everything has worked, you should now be able to visit any HTTPS URL via Burp without any security warnings

## Common issue
### Kali Connectivity Issues
* symptoms: no internet connection, ssh timing out
* possible cause: eth0 (NAT) or eth1 (hostonly) interfaces do not have IP assigned
* verify: `ifconfig`
* fix: `dhclient eth0` and/or `dhclient eth1`