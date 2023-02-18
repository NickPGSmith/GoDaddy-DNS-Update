# GoDaddy-DNS-Update

I am running a home webserver, but my ISP does not offer a static IP allocation: periodically I get a new IP address for my domain I bought through GoDaddy. GoDaddy offers a domain management service via the Web: you can add/remove/update the DNS A/AAAA records for the domains(s) you have bought. They also offer an API that can be used to do this programatically, and there are some python modules available that make this easy to use.

Here is a simple python program to use this; I run on Fedora Linux. When run, the dnsupdate.conf file is read, and the public IP addresses (v4 and v6) are obtained from the [ident.me](https://ident.me) service. The current GoDaddy A and AAAA records' IP addresses are obtained, and if necessary, the records are updated.

A log file (dnsupdate.log) is created that will show errors, and information on what IP information it has obtained, and if it has needed to update the GoDaddy record(s).

## Requirements

- Python 3
- Python module: [pif](https://pypi.python.org/pypi/pif/0.8.2)
- Python module: [godaddypy](https://pypi.python.org/pypi/GoDaddyPy)
- Access to ident.me service

## Installation

The two files should be installed in the same directory (such as /root/dnsupdate):

- Main code: dnsupdate
- Configuration file: dnsupdate.conf

Ensure permissions are appropriate:

```
chmod 700 dnsupdate
chmod 600 dnsupdate.conf
```

Log onto the GoDaddy Domain Manager, and ensure that A and AAAA records exist for your domain. Also generate the production API key and secret, which should be added to the conf file. Also change the domain. You can choose to send out an email notification when a record is changed.

A symlink can be added so that it is run hourly:

```
ln -s /root/dnsupdate/dnsupdate /etc/cron.hourly/dnsupdate
```
