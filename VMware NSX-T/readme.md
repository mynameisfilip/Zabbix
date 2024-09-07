# VMware NSX-T Zabbix Monitoring Template

This repository contains a **Zabbix Monitoring Templates** specifically designed for monitoring **VMware NSX-T** environments. These templates provide monitoring capabilities for key components and services within an NSX-T deployment.

## Requirements

Before using this template, ensure that you meet the following prerequisites:

- Zabbix 6.0 or newer
- VMware NSX-T 3.2 or higher
- HTTPS access to NSX-T Manager API from Zabbix server
- Read-only Principal identity user created in NSX-T

## Installation

Follow these steps to install and configure the VMware NSX-T Zabbix Monitoring Template:
1. Import templates to your Zabbix server in the following order:
   - Template_NSX_Macros
   - Template_NSX_Management_Nodes
   - Template_NSX_Edge_Transport_Nodes
   - Template_NSX_Cluster_Management
2. Edit Macros in template *Template_NSX_Macros* to reflect your environment and needs.
3. Import private key and certificate of your NSX-T Principal identity user to Zabbix server. Default location:
   - SSLCertLocation "/usr/share/zabbix/ssl/certs"
   - SSLKeyLocation "/usr/share/zabbix/ssl/keys"
4. Link template *Template_NSX_Cluster_Management* to a Zabbix host representing your NSX-T Management cluster VIP or hostname.
5. Host discovery rules in template *Template_NSX_Cluster_Management* will create Zabbix hosts for each NSX-T Manager Nodes and NSX-T Edge Transport Nodes.
