# LogiSphere Infrastructure Lab

## Project Status
Current Phase: Active Directory Deployment

Completed:
- Base Server Configuration
- Active Directory Installation

In Progress:
- Organizational Units (OU)
- User Management

Planned:
- Group Policy Objects (GPO),
- Shared Folders
- Windows 11 Domain Client

## Project Overview

This project simulates the IT infrastructure of a logistics company using 
Windows Server 2022 and Active Directory.

## Lab Scenario
LogiSphere is a fictional logistics company used for learning and testing Windows Server administration.

Departments:
- IT
- HR
- Accounting
- Warehouse
- Management

Infrastructure Goals:
- Centralized authentication
- User and group management
- Group Policy administration
- Shared folders and permissions
- Domain-joined client computers

## Environment
- Windows Server 2022,
- Oracle VirtualBox
- Windows 11 Client (planned)
- Active Directory Domain Services (AD DS)
- Domain: logisphere.local

## Phase 1 - Base Server Configuration

Completed:
- Installed Windows Server 2022,
- Renamed server to DC01,
- Configured static IPv4 address (192.168.10.10),
- Configured DNS settings,
- Configured time zone,
- Created VirtualBox snapshot (DC01_BASE),

## Screenshots

### Server renamed to DC01
![DC01](screenshots/server-renamed-DC01-and-timezone.png)

### Static IP Configuration
![Static IP](screenshots/static-IP-configured.png)

## Phase 2 - Active Directory Deployment

### Active Directory Domain Services Installed
Successfully installed the Active Directory Domain Services (AD DS) role on DC01.
The server is now ready to be promoted to the first Domain Controller of the LogiSphere.local domain.
![AD DS](screenshots/ad-ds-role-installed.png)

### Active Directory Forest Creation
Created a new Active Directory forest named logisphere.local for the LogiSphere logistics company infrastructure. 
![AD DS Forest](screenshots/ad-new-forest.png)

### Domain Controller Configuration
Configured the first Domain Controller for the logisphere.local forest.
Enabled DNS Server and Global Catalog roles.
Configured Directory Services Restore Mode (DSRM) password.
![Domain Controller](screenshots/domain-controller-options.png)

### NetBIOS Domain Configuration
Configured the NetBIOS domain name for the Active Directory environment.
NetBIOS name: LOGISPHERE
Domain name: logisphere.local
![NetBIOS](screenshots/ad-netbios-name.png)

### Active Directory Deployment Review
Review the Active Directory deployment configuration before promoting DC01 to the first Domain Controller.
Configuration:
- Domain: logisphere.local
- NetBIOS: LOGISPHERE
- Forest Functional Level: Windows Server 2016 
- Domain Functional Level: Windows Server 2016
- DNS Server: Enabled
- Global Catalog: Enabled
![Review](screenshots/ad-review-options.png)

### Active Directory Prerequisites Check
Validated the Active Directory Domain Services configuration before domain controller promotion.
Results:
- All prerequisites checks passed successfully 
- DNS role configured
- Global Catalog enabled
- Forest root domain: logisphere.local
- Domain controller promotion ready
![AD Prerequisites check](screenshots/ad-prerequisites-check.png)

### Domain Controller Login
After Active Directory Domain Services installation and server promotion, DC01 successfully joined the LOGISPHERE domain as the first Domain Controller.
Login account: LOGISPHERE\Administrator
Domain: logisphere.local
![Domain Controller Login](screenshots/domain-controller-login-screen.png)

### Active Directory Management Tools Available

After promoting DC01 to a Domain Controller, Active Directory managment tools became available in Server Manager.
Installed managment tools:
- Active Directory Users and Computers
- Active Directory Administrative Center
- Active Directory Domains and Trusts
- Active Directory Sites and Services
- DNS Manager
- Group Policy Management

The server is fully operational as a Domain Controller for the LogiSphere domain.
![AD tools](screenshots/ad-tools-available.png)

## Phase 3 - Organizational Unit Structure

### Organizational Units Created

Created the Organizational Unit (OU) structure for the LogiSphere Active Directory environment.

Departments:
- IT
- HR
- Accounting
- Warehouse
- Management

Additional Organizational Units:
- Groups
- Workstations

This structure will be used to organize users, computers, security groups and Group Policy Objects (GPOs).
![OU Structure](screenshots/ou-structure-created.png)

## Phase 4 - User Management

### First Domain User Created

Created the first domain user account for the LogiSphere Active Directory environment.

User details:
- Name: Lukas Schneider
- Department: IT
- Username: l.schneider
- Domain: logisphere.local

The account was created inside the IT Organizational Unit (OU) following the company structure.

![First Domain User](screenshots/first-domain-user-created.png)

### Department Users Accounts Created

Created domain user accounts for all LogiSphere departments.

### IT
- Lukas Schneider
- Felix Weber
![It-users](screenshots/it-users.png)

### HR
- Anna Berg
- Julia Fischer
![HR-users](screenshots/hr-users.png)

### Accounting
- Thomas Becker
- Sandra Wagner
![Accounting-users](screenshots/accounting-users.png)

### Warehouse
- Michael Hoffmann
- Kevin Schulz
![Warehouse-users](screenshots/warehouse-users.png)

### Management
- Markus Kaiser
![Management-users](screenshots/management-users.png)

Each user account was created inside its corresponding Organizational Unit (OU) to maintain a structured Active Directory environment.

## Phase 5 - Security Groups

Created dedicated Active Directory Security Groups for each department.

Security Groups:
- GG_IT
- GG_HR
- GG_ACCOUNTING
- GG_WAREHOUSE
- GG_MANAGEMENT

All groups were created as:
- Group Scope: Global
- Group Type: Security

Department users were assigned to their corresponing security groups to simplify permission management and feature access control configuration.

### Department Security Groups

![Security Groups](!screenshots/security-groups-created.png)

## Phase 6 - File Server and NTFS Permissions

### Department Shared Folders

Created departmental shared folders and configured NTFS permissions based on Active Directory Security Groups.
![NTFS Permissions](screenshots/department-shares.png)

### NTFS Permissions Configuration

Configured NTFS permissions using Active Directory Security Groups.

Example:
- GG_IT = Modify
- Administrators = Full Control
- SYSTEM = Full Control

Inheritance was disabled to ensure department specific access control.

![NTFS Advanced](screenshots/department-shares-advanced.png)

### SMB Network Shares

Configured SMB network shares for all company departments.
Available shared folders:
- Accounting
- HR
- IT
- Management
- Warehouse

Verified network access using: \\localhost

The shares are accessible over the network and integrated with Active Directory security groups and NTFS permissions.
![SMB Shares](screenshots/smb-shares.png)

## Phase 7 - Windows 10 Domain Client Deployment

### Client Network Configuration

Configured a Windows 10 client machine for communication with the Active Directory environment.

Client Configuration:
- Hostname: WIN10-CLIENT
- IP Address: 192.168.10.20
- Subnet Mask: 255.255.255.0
- DNS Server: 192.168.10.10

The client was connected to the LABNET internal network in Oracle VirtualBox.

![Client Network Configuration](screenshots/win10-network-config.png)

### Connectivity Verification

Verified network communication between the Windows 10 client and the Domain Controller (DC01).

Test:
- ping 192.168.10.10

Result:
- Successful communication
- 0% packet loss

![Client Ping Test](screenshots/win10-ping-dc01.png)

### DNS Resolution Test

Verified DNS name resolution from the Windows 10 client using the Domain Controller DNS service.

Tests performed:
- nslookup dc01.logisphere.local
- nslookup logisphere.local

Results:
- dc01.logisphere.local resolved to 192.168.10.10
- logisphere.local resolved to 192.168.10.10

The client was successfully communicates with the DNS service hosted on DC01.

![DNS Resolution](screenshots/win10-dns-resolution.png)

