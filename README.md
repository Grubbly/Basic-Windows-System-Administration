# Basic Windows Auditing
Using Windows Server 2012

Based on: https://youtu.be/I8mfnOOpe4E

## Server Manager
Quickest place to identify services, install new ones, or reconfigure existing ones.

### Check for updates
```Server Manager -> Local Server -> Windows Update```

or

```Control Panel -> System and Security -> Windows Update```

### Date and Time Settings
```Server Manager -> Local Server -> Time Zone -> Internet Time```

### Computer Name
```Server Manager -> Local Server -> Computer Name```

### Remote Desktop
```Server Manager -> Local Server -> Remote Desktop```

### Windows Firewall
```Server Manager -> Local Server -> Windows Firewall```

### Configure Static IP
```Server Manager -> Local Server -> [NetworkCardName](ex. Ethernet0) ```
* Right click network interface
* Click status
    * **Details** will give you information related to your IP address, DNS server, etc.
    * **Properties** will let you set a static IP address
        * Open up IPv4
        * Select `use the following IP address`
        * Enter IP settings

### Adding Roles and Features
```Server Manager -> Dashboard -> Add roles and features```
* Here you can install services like:
    * Active Directory
    * DNS
    * File server

## Active Directory
Add organization units, users, and groups.

### Setting user logon hours
``` Active Directory Users and Computers -> Right click user account -> Properties -> Account -> Logon Hours...```

## Group Policy

### Default Domain Policy
Policies in here span across the entire domain. Right click edit in hierarchy to edit rules.

#### Password Policies
```Default Domain Policy -> Computer Configuration -> Policies -> Windows Settings -> Security Settings -> Account Policies -> Password Policy```

#### Account Lockout Duration Policy
How long do you have to wait to try entering another password after failing X times?

```Default Domain Policy -> Computer Configuration -> Policies -> Windows Settings -> Security Settings -> Account Policies -> Account Lockout Policy```

### Set a custom group policy (Ex. Machine inactivity)

Create the new policy:

```Right click -> Create a GPO in this domain, and Link it here... -> Name it and press okay```


Edit the policy settings:

```Right Click Policy -> Edit... -> Computer Configuration -> Policies -> Windows Settings -> Security Settings -> Local Policies -> Security Options -> Interactive logon: Machine inactivity limit```

**Note**: TechNet is a good place to look to reference common group policy rules.

### DNS Manager
Holds HOST records (computers on the network) and aliases (CNAME) for hosts (```popcorn.microrave.net```)

## Firewalls

### Windows Advanced Firewall
Nice GUI for implementing firewall rules. If you are not writing rules for the domain controller, this interface provides enough functionality to implement what you need. To script firewall rules we use ```netsh```, let Tristan know if you want some material on how to use it (see https://github.com/Grubbly/Netsh-Firewall-Maker)

## Process Explorer
Get an in depth view of processes and what child processes they are running. This is helpful for finding hidden red team scripts.

## Zenmap
A GUI for nmap that can be used on windows. This is handy if you need to whip up a quick network diagram with all your hosts on it.