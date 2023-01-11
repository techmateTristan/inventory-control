# TechMate Inventory Management Project
author: Tristan Garside <br/>
date:  27-12-2022

## Overview

A small database with a web frontend to manage an inventory,
 principally of devices (laptops, desktops, tablets and phones).
 Additionally the inventory will include office furniture,
 stationery and miscellaneous items.   

As the main focus 'devices' will be richer with fields such as
 product IDs, OS, unique IDs, and fields relating to state
 and pending maintenance etc.

All CRUD operations are to be supported, and with a range of useful 
 views.     


## Installation and Setup of tools

### [couchdb](https://docs.couchdb.org/en/3.2.2-docs/index.html)

#### Installation on Fedora 37 as at 27-12-2022
1. install snap if not already done so<br/>
```$ sudo dnf install snapd```
2. Follow the exact instructions as described in this
 [page](https://github.com/apache/couchdb-pkg/blob/main/README-SNAP.md)
 in the couchdb github repo
#### Setup
#### Opening interface to local network
1. Stop couchdb `$ sudo snap stop couchdb`
2. edit the `local.ini` file to change the bind address:<br/><br/>
`sudo micro /var/snap/couchdb/9/etc/local.ini`
```
[chttpd]
port = 5984
bind_address = 0.0.0.0
...

[httpd]
bind_address = 0.0.0.0
...
```
3. Open port 5984 in zone 'home' and limit ip range to
 local network only, via firewalld:<br/>
`$ sudo firewall-cmd --zone=home --add-source=192.168.100.0/24`<br/> 
`$ sudo firewall-cmd --zone=home --add-port=5984/tcp`<br/>
`$ sudo firewall-cmd --zone=home --list-all`<br/>
`$ sudo firewall-cmd --runtime-to-permanent`<br/>
`$ sudo systemctl restart firewalld`<br/>

optionally pen-test the port from a computer
 external to the network (when couchdb service
  is running):<br/>
`$ sudo nmap -sT -p 5984 <ip-address>`<br/><br/>
port should return "filtered"

4. Find and note down server ip:<br/>
`ip addr | grep "inet " | tail -1` 

5. Restart couchdb:<br/>
 `sudo snap start couchdb`

 
#### Interacting with couchdb via cURL
- See top-level view (pipe through python -mjson.tool to prettify JSON response)<br/>
`curl -X GET 'http://admin:<password>@<ip-address>:5984' | python -mjson.tool`
- Create a test database:<br/>
`curl -X PUT 'http://admin:<password>@<ip-address>:5984/test`
- Create a document:<br/>
```curl -X PUT 'http://admin:<password>@<ip-address>:5984/test/doc1' -d {"name": "Polly"}```
- View that document:<br/>
`curl -X GET 'http://admin:<password>@<ip-address>:5984/test/doc1' | python -mjson.tool`

#### Interacting with couchdb via Browser ("Fauxton ")

**url:**  \<ip-address\>:5984/_utils

### NodeJS and npm

`$ sudo dnf install nodejs`<br/>
npm (node package manager) is installed at ther same time
 as a (weak) dependency

`$ npm init`<br/>
initialises the package.json which organises all the modules
 the project will use
 
