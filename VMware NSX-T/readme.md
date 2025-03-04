# VMware NSX-T Zabbix Monitoring Template

This repository contains **Zabbix Monitoring Templates** designed for monitoring **VMware NSX-T** environment. These templates allow you to monitor critical aspects of VMware NSX-T infrastructure using **Zabbix**, providing visibility into the health, performance, and availability of NSX-T components such as:

- **NSX Management** 
  - Management cluster status
  - Manager Node status
    - Service status, CPU/Memory usage, Filesystem information, Uptime
- **NSX Fabric**
  - Edge cluster status
  - Edge Transport node status
    -  CPU/Memory usage, Filesystem information, Uptime
    -  Network interface status
    -  Network interface statistics
  - Compute manager status


## Requirements

Before using these templates, ensure that you meet the following prerequisites:

- Zabbix 6.0 or newer
- VMware NSX-T 3.2 or higher
- HTTPS access to NSX-T Manager API from Zabbix server
- Read-only Principal identity user created in NSX-T

## Installation

Follow these steps to install and configure the VMware NSX-T Zabbix Monitoring Templates:
1. Import templates to your Zabbix server in the following order:
   - Template_NSX_Macros
   - Template_NSX_Management_Nodes
   - Template_NSX_Edge_Transport_Nodes
   - Template_NSX_Cluster_Management
2. Edit Macros in template *Template_NSX_Macros* to reflect your environment and needs.
3. Import private key and certificate of your NSX-T Principal identity user to a Zabbix server. Default location:
   - SSLCertLocation "/usr/share/zabbix/ssl/certs"
   - SSLKeyLocation "/usr/share/zabbix/ssl/keys"
4. Create a Zabbix host to represent your NSX-T Management Cluster VIP or hostname.
5. Link template *Template_NSX_Cluster_Management* to a Zabbix host created in step 4.
6. Host discovery rules in template *Template_NSX_Cluster_Management* will create Zabbix hosts for each NSX Manager Node and NSX Edge Transport Node.



*These templates were created with a limited NSX-T environment deployed and thus may not monitor all that you wish to monitor.
