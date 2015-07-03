Somlyr
=============
## Summary
> **Openwrt** is a strong embeded network device developing platform,with it we can create some funny hardware device.it can be used as:
> **Router**|**Switch**|**Firewall**|**SDN Device**|**Some Other Smart Device**
> 
> when we begin the openwrt trip,we should think about what will be done?

## Vision
our **Vision** is to build a smart network device,which can be a network **smart** access point.
this smart device has some strong features:**Multi-Access**|**Advance-Security**|**Smart-Schedule**|

**Multi-Access**

* Giga Ethernet
* 802.1AC Wifi Mesh
* 3G/4G Module
* SSL based VPN
* IPSec based VPN

**Advanced-Security**

* Encyper
* IPSec IKE
* SSL
* IDS/IPS
* Netflow
* SPTN(smart ptn)

**Smart-Schedule**

* SDN based Schedule
* MML based Schedule
* SNMP based Schedule
* LOCAL based Schedule

## Build
build openwrt base project will be a likely progress,all we should be make something sure,include these:

* Network Environment
* Select Host Os
* Install Host Toolslet
* Select Openwrt Branch
* Configure Package GitSource
* Configure Your Project
* Make it

####1. Network Environment
when we build openwrt *first time*,the build progress need to download many packages from *openwrt repository*,it maybe a longtime.
*network problem* will broken down the building progress.

####2. Select Host Os
host os selection will help us to build openwrt more easily.
at our trying,we select the **ubuntu 14.04tls**.
any other host os selection,you will try it yourself.

####3. Install Host Toolslet
the openwrt make progress need some host toolslet,you should make sure these toolslet is installed on your host os before you start the *make progress*.
```bash
sudo apt-get install build-essential subversion git-core libncurses5-dev zlib1g-dev gawk flex quilt libssl-dev xsltproc libxml-parser-perl unzip
```
as we know,use none-root privilage to install these tools will be good selection.(*some softwares need to be maked at none-root privilage*)

####4. Select Openwrt Branch
there some Openwrt Branchs you can select,it's a good idea to select a Openwrt Branch based on [Openwrt hardware support](http://http://wiki.openwrt.org/toh/start)

**Barrier Breaker 14.07**
> The most recent OpenWrt releases are linked below. Use the latest available release for new deployments unless you know exactly what you do.
> *Released: Thu, 02 Oct 2014*
> you can clone from github:
> ```bash
> git clone git://git.openwrt.org/14.07/openwrt.git
> ```

**Chaos Calmer 15.05 RC2**
> This is the second release candidate of the upcoming stable version Chaos Calmer 15.05. Keep in mind that the RC version is not the final release yet, it is available here for testing and refinement purposes.
> *Released: Sat, 13 June 2015*
> you can clone from github:
> ```bash
> git clone git://git.openwrt.org/15.05/openwrt.git
> ```

**backfire(stable version)**
> you can clone from github:
> ```bash
> git clone git://git.openwrt.org/10.03/openwrt.git
> ```

**attitude adjustment(stable version)**
> you can clone from github:
> ```bash
> git clone git://git.openwrt.org/12.09/openwrt.git
> ```

**trunk(develop version)**
> you can clone from github:
> ```bash
> git clone git://git.openwrt.org/openwrt.git
> ```

####5. Prepare Your Project
when you have cloned the *openwrt*,you maybe need to modified the **openwrt feeds package source**,the **feeds.conf.default** is the default feeds configure file,you can modified it and rename to **feeds.conf**.a typical *feeds.conf* like:
```bash
src-git packages https://github.com/openwrt/packages.git;for-14.07
src-git luci https://github.com/openwrt/luci.git;luci-0.12
src-git routing https://github.com/openwrt-routing/packages.git;for-14.07
src-git telephony https://github.com/openwrt/telephony.git;for-14.07
src-git management https://github.com/openwrt-management/packages.git;for-14.07
src-git oldpackages http://git.openwrt.org/14.07/packages.git
#src-svn xwrt http://x-wrt.googlecode.com/svn/trunk/package
#src-svn phone svn://svn.openwrt.org/openwrt/feeds/phone
#src-svn efl svn://svn.openwrt.org/openwrt/feeds/efl
#src-svn xorg svn://svn.openwrt.org/openwrt/feeds/xorg
#src-svn desktop svn://svn.openwrt.org/openwrt/feeds/desktop
#src-svn xfce svn://svn.openwrt.org/openwrt/feeds/xfce
#src-svn lxde svn://svn.openwrt.org/openwrt/feeds/lxde
#src-link custom /usr/src/openwrt/custom-feed
```
package's repository will be set at this config-file.
**src-git**|**src-svn** command will get package from **git**|**svn** repository.
**src-link** command will get package from local dir.this is a handy command when try your *special* package(*can't be found at normal network repository*).

as you have correct your **feeds.config**,you need to update and install it,like:
```bash
cd openwrt_dir
./scripts/feeds update -a
./scripts/feeds install -a
```
*more **feeds** command you can try **./scripts/feeds --help***

####6. Make it
at this step,all feeds packages have been installed,so we can config our project,like:
```bash
cd openwrt_dir
make menuconfig
```

when make config is be done,we can start to make the whole project,like:
```bash
cd openwrt_dir
make V=s
```

consume a long making time,if you are luck,you will get your openwrt **factory&upgrade** binary at *./bin*.
*openwrt's build tools are very good,so you should be luck:)*

## Publish
## Debug