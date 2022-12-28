# Techmate Inventory Management Project
author: Tristan Garside <br/>
date:  27-12-2022

## Overview

## Installation and Setup of tools

### [couchdb](https://docs.couchdb.org/en/3.2.2-docs/index.html)

#### Installation on Fedora 37 as at 27-12-2022
1. install snap if not already done so<br/>
```$ sudo dnf install snapd```
2. Follow the exact instructions as described in this
 [page](https://github.com/apache/couchdb-pkg/blob/main/README-SNAP.md)
 in the couchdb github repo
#### Setup
##### Opening "Fauxton" interface to local network
1. Stop couchdb `$ sudo snap stop couchdb`
2. edit the `local.ini` file to change the bind address:<br/><br/>
`sudo micro /var/snap/couchdb/9/etc/locval.ini`
```
[chttpd]
port = 5984
bind_address = 0.0.0.0
...

[httpd]
bind_address = 0.0.0.0
...
```
3. Open port 5984 in firewalld:<br/>
`$ sudo firewall-cmd --add-port=5984/tcp`
`$ sudo systemctl restart firewalld`

4. Find server ip: `ip addr | grep "inet "` 

5. Restart couchdb `sudo snap start couchdb`

6. Connect to server in browser using address <server-ip>:5984 

