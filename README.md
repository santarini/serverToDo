# Server Setup

## About

I have a Dell r710 that I bought a few years back and it currently gathers dust.

I currently have a small like 500 GB HDD plugged into it. It’s currently running Debian.

I’ve also purchased installed 10 3.5” hotswaps.

I’d like to soup it.

I’m also sitting on:
-	8 TB Western Digital Gold HDD
-	8 TB Western Digital Red HDD
-	4 TB Western Digital Black HDD
-	4 TB Western Digital Black HDD

I’m envisioning the r710 doing 3 things:
1. Plex media server
2. NAS backup of all the files I’ve accumulated across my devices
3. It’s going to run a Python script I built that gathers stock market data

### Update 12/29/18

It turns out my r710 has a PERC 6/i RAID Controller that only supports physical disks up to 2TB. There is another RAID controller for the r710 called the PERC H700 that supports drives up to 4TB. That is a fat bummer and I wish I knew that earlier because basically all my 8TBs are useless for this project. I could probably use them for a detached NAS.

My alternatives:
* Upgrade the RAID Controller and use 4TB WD Blacks that I have on hand.
* Buy 2TB HDDs

### Update 12/30/18

I woke up to my r710 stuck in the BIOs with an ugly error and 4 errors on the LCD.

Memory write/read failure at 1E171100, read 00000000
Expecting A5A5A5A5
Decreasing available memory.

These errors appeared on the LCD:
* E1410 System Fatal Error detececd
* E1422 CPU 2 machine check error. Power cycle AC
* E2110 Multibit Error on DIMM B2. Reseat DIMM.

In BIOS [you can view the system logs](https://www.dell.com/support/article/aw/en/awbsdt1/sln292270/poweredge-server-error-messages-in-system-event-log-and-how-they-can-be-viewed?lang=en) by pressing CTRL+E during system start to access the configuration utility.

~~~
Entry 46 of 46
Severity: Critical
Date and Time: Sun Dec 30 2018 08:26:44
Description:
ECC Uncorr Err: Memory sensor, uncorrectable ECC ( DIMM_B2 ) was asserted
~~~

Entry 37 of 46
> Severity: Non-Recoverable
> Date and Time: Sun Dec 30 2018 08:26:44
> Description:
> CPU Machine Chk: Processor sensor, transition to non-recoverable was asserted

> Entry 36 of 46
> Date and Time: Sun Dec 30 2018 06:39:02
> Severity: Critical
> Description:
> ECC Uncorr Err: Memory sensor, uncorrectable ECC ( DIMM_B2 ) was asserted


> Entry 16 of 46
> Date and Time: Sun Dec 30 2018 05:20:07
> Severity: Critical
> Description:
> CPU1 Status: Process sensor for CPU1, IERR was asserted

## To-Dos

### Server OS Setup
- [x] Get usable (~16 GB) flash drive
- [x] Determine which OS to use
- [x] Download OS iso
- [x] Create bootable image of OS onto a flash drive
- [x] Swap out current HD for WD 8TB Gold
- [x] Configure server for BIOS/UEFI for bootable image 
- [x] Install OS on HD

### Server Error Fix
- [x] Figure out DIMM type
- [x] Figure out [DIMM install pattern](https://www.dell.com/downloads/global/products/pedge/en/server-pedge-installing-upgrading-memory-11g.pdf)
- [ ] Purchase more DIMM
- [ ] Install DIMM

### Server Hardware Upgrade
- [x] Figure out DIMM type
- [ ] Figure out DIMM install pattern
- [ ] Purchase more DIMM
- [ ] Install DIMM

### Backup all files
- [ ] Get usable (~1 TB) backup disk
- [ ] Purchase (~8 TB) Red NAS drive
- [ ] Backup Dawson HDD
- [ ] Backup Old Personal Macbook Pro
- [ ] Backup New Dawson Macbook Pro
- [ ] Backup Home Office Computer
- [ ] Backup Kapua’s Old Macbook Pro


### NAS Software
- [ ] Read up on Unraid and Xpenolgoy

### Questions
- [ ] To what extent can I pair mismatched disks by brand, color, size?
- [ ] Can I run one disk on 24/7 and another on an as needed basis?
- [ ] Can I NAS one disk but not another?
- [ ] Can I FTP or SSH into my file system?
- [ ] Can I access my filesystem over the internet?
- [x] Is Unraid an OS?


### Things I Need to Research
- [ ] NAS
- [ ] Find some literature on this homelab stuff
- [ ] RAID
- [ ] VMs
- [ ] Emby
- [ ] Serviio
- [ ] Tversity
- [ ] Plex Linux
- [ ] Plex Adult
- [ ] Plex Documentary
- [ ] Plex Reality
- [ ] Flexible expansion
- [ ] Parity drive
- [ ] unRAID Array
- [ ] Server Name Indication
- [ ] VPS
- [ ] Static IP costs
- [ ] microk8s
- [ ] kubernetes
- [ ] Docker container
- [ ] ESXi
- [ ] Hyper visor



## Discord Discussion Notes

https://clients.ionswitch.com/cart.php?a=add&pid=13   code: 2018-BLACKFRIDAY512

##### Can I host websites from a server at home?

Yep. Provided your ISP doesn't block the ports required to do so or you are able to use a non-standard port.
Also, if you do not have a static IP addres, you'll have to use some sort of dynamic DNS service.
Or obtain a static address from your service provider.

##### Can I use one static IP for multiple domain names?
##### Do you know of any literature on this stuff you point me towards?

As for the part about hosting at home, it would be different per ISP and situation, so no set documentation that I could recommend on that per se, but I can help answer questions to the best of my ability.

My recommendation is that you use a software such as WHM / cPanel to do this. It's what I host some various websites with.

The software costs me around $20/month.

Per instance

So I have a virtual machine running CentOS which has WHM / cPanel installed on it. Multiple websites run on this server but are sort of sandboxed so the websites are separate and the site owners can't access the other website's files, etc.


I think I pay $10 per month per static IPv4 I get from my ISP

##### What if I wanted to host a Django website?

Honestly if you're just looking to run a basic website of some sort, just go get a $5/mo VPS from any of the big providers
I recommend digitalocean or AWS

you don't want to run anything designed to be web facing from a home internet connection
Vultr is also good
Several of them have $2.50/mo offerings too

Also, if you need a static public IP, honestly running a VPN back from a cheapo VPS is probably cheaper and easier than getting one from your ISP

##### I want to set up a build so that one disk contains all of my Plex data and that a second disk is dedicated to regularly executing python web scraping scripts that populate a database. Is unRAID the best option? Would I be able to use plex while Python scripts are executing simultaneously?

Analog PotatoToday
well, all the cool kids do something like docker and then containerize each task
that way if plex or the python scripts fail/cause problems it doesn't interrupt each other

BryceTechToday at 10:32 PM
cough cough ESXi

Analog PotatoToday at 10:33 PM
^ this
I have ESXi running with 6 VMs, that way each task is separate

https://my.vmware.com/en/web/vmware/evalcenter?p=free-esxi6

Here is another good link- just ignore the vCenter part: https://www.altaro.com/vmware/vsphere-home-lab-free/
