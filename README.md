# GoDaddy-DNS-Update
Simple python code that can be used to automatically update GoDaddy DNS A/AAAA records

# Requirements

- Python 3
- Python module: pif
- Python module: godaddypy
- Access to ident.me service

# Installation

The two files should be installed in the same directory (such as /root/dnsupdate):

- Main code: dnsupdate
- Configuration file: dnsupdate.conf

Ensure permissions are appropriate:

> chmod 700 dnsupdate
> chmod 600 dnsupdate.conf

Log onto the GoDaddy Domain Manager, and ensure that A and AAAA records exist for your domain. Also generate the production API key and secret, which should be added to the conf file. Also change the domain.

A symlink can be added so that it is run hourly:

> ln -s /root/dnsupdate/dnsupdate /etc/cron.hourly/dnsupdate
