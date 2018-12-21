# Server Setup

I have a Dell r710 that I bought a few years back and it currently gathers dust.

I currently have a small like 500 GB HDD plugged into it. It’s currently running Debian.

I’ve also purchased installed 10 3.5” hotswaps.

I’d like to soup it.

I’m also sitting on:
-	8 TB Western Digital Gold HDD
-	4 TB Western Digital Black HDD
-	4 TB Western Digital Black HDD

I’m envisioning the r710 doing 3 things:
1. Plex media server
2. NAS backup of all the files I’ve accumulated across my devices
3. It’s going to run a Python script I built that gathers stock market data

## Server OS Setup
- [ ] Get usable (~16 GB) flash drive
- [ ] Determine which OS to use
- [ ] Download OS iso
- [ ] Create bootable image of OS onto a flash drive
- [ ] Swap out current HD for WD 8TB Gold
- [ ] Configure server for BIOS/UEFI for bootable image 
- [ ] Install OS on HD

## Server Hardware Upgrade
- [ ] Figure out DIMM type
- [ ] Figure out DIMM install pattern
- [ ] Purchase more DIMM
- [ ] Install DIMM

## Backup all files
- [ ] Get usable (~1 TB) backup disk
- [ ] Purchase (~8 TB) Red NAS drive
- [ ] Backup Dawson HDD
- [ ] Backup Old Personal Macbook Pro
- [ ] Backup New Dawson Macbook Pro
- [ ] Backup Home Office Computer
- [ ] Backup Kapua’s Old Macbook Pro


## NAS Software
- [ ] Read up on Unraid and Xpenolgoy

## Questions
- [ ] To what extent can I pair mismatched disks by brand, color, size?
- [ ] Can I run one disk on 24/7 and another on an as needed basis?
- [ ] Can I NAS one disk but not another?
- [ ] Can I FTP or SSH into my file system?
- [ ] Can I access my filesystem over the internet?
- [x] Is Unraid an OS?


## Things I Need to Research
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

https://clients.ionswitch.com/cart.php?a=add&pid=13   code: 2018-BLACKFRIDAY512

Discord discussions

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
