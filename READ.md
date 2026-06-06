# LogiSphere Infrastructure Lab

## Project Overview

This project simulates the IT infrastructure of a logistics company using 
Windows Server 2022 and Active Directory .

## Eviroment
- Windows Server 2022,
- Oracle VirtualBox
- Windows 11 Client (planned)
- Active Directory (planned)
- Domain: Logisphere.local (planned)

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
