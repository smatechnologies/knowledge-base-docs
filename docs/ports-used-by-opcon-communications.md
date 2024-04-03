---
sidebar_label: 'Ports Used By OpCon Communications'
hide_title: 'true'
---

## Ports Used By OpCon Communications

**OpCon** and **LSAM**s need for communication purpose that some ports or ranges are open. You'll find below a list of default ports used. 

* Communication OpCon Server -> Windows LSAM : Port **3100**, **3110** (a third port is necessary for TLS communication)
* Communication OpCon Server -> UNIX LSAM: **3100** to **3110** (range)
* Communication OpCon Server -> IBM i LSAM: **3100**, **3110** and **3301**
* Communication OpCon Server -> SQL LSAM: **21100** and **21110**
* Communication OpCon Server -> Java LSAM: **17100** and **17110**
* Communication OpCon Server -> SAP LSAM: **13100** and **13110**
* Communication OpCon Server -> SAP BW LSAM: **14100** and **14110**

**Other communications**

* Communication Enterprise Manager -> SQL Server: **1433**
* Communication between 2 SQL Servers (mirroring): **5022 (both sides)**
* Replication OpCon Production Server <- Failover Server: **3200**
* Log files sharing between Enterprise Manager -> OpCon Server: **139** or **445**
* Communication Solution Manager -> OpCon Server: **8443** or **443 (https)**
* OpCon Server -> Active Directory (AD) Server (synchronization of user accounts): 3**89 / 3268 (ldap) 636 / 3269 (ldaps)**
* Communication ImpEx2 (Deploy server module): **9011**
* OpCon Server -> SMTP Server: **25** (can be different following your configuration). OpCon Server must be authorized to send emails on your SMTP Server. 