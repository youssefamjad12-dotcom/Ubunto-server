# Ubunto Server


````
# Ubuntu Server Installation on VMware

## Goal

Create a VMware virtual machine and install Ubuntu Server.

VM specifications for the Wazuh server:

| Setting | Value |
|---|---|
| OS | Ubuntu Server 24.04 LTS |
| CPU | 4 CPU cores |
| RAM | 8 GB |
| Disk | 100 GB |
| Network | NAT or Bridged |
| Firmware | UEFI |
| VM Name | Wazuh-Server |
| Hostname | wazuh-server |

---

# 1. Download Ubuntu Server ISO

Download Ubuntu Server 24.04 LTS ISO from the official Ubuntu website:

https://ubuntu.com/download/server

Download the:

```text
Ubuntu Server 24.04 LTS
````

 The file should look similar to:

```
ubuntu-24.04.x-live-server-amd64.iso
```

 Save the ISO somewhere easy to find.

 Example:

```
C:\ISO\ubuntu-24.04.x-live-server-amd64.iso
```

---

 # 2\. Open VMware

 Open:

```
VMware Workstation
```

 Then select:

```
Create a New Virtual Machine
```

 You can also use:

```
File
>
New Virtual Machine
```

---

 # 3\. Select Virtual Machine Type

 VMware will show:

```
New Virtual Machine Wizard
```

 Select:

```
Typical (recommended)
```

 Click:

```
Next
```

---

 # 4\. Select Ubuntu ISO

 VMware will ask:

```
How will you install the operating system?
```

 Select:

```
Installer disc image file (iso)
```

 Click:

```
Browse
```

 Select your Ubuntu ISO.

 Example:

```
C:\ISO\ubuntu-24.04.x-live-server-amd64.iso
```

 Click:

```
Next
```

---

 # 5\. Easy Install

 VMware may automatically detect Ubuntu.

 You may see fields such as:

```
Full name
User name
Password
```

 For example:

```
Full name:
Wazuh Administrator

User name:
wazuhadmin

Password:
YOUR_STRONG_PASSWORD
```

 If VMware offers:

```
Use Easy Install
```

 you can use it.

 However, for learning and troubleshooting, it is often easier to install Ubuntu manually.

 If you want a manual installation:

```
Select:
I will install the operating system later
```

 Then click:

```
Next
```

 If you choose manual installation, attach the Ubuntu ISO later.

---

 # 6\. Select Guest Operating System

 If VMware asks:

```
Guest Operating System
```

 Select:

```
Linux
```

 Then select:

```
Ubuntu 64-bit
```

 Click:

```
Next
```

---

 # 7\. Name the Virtual Machine

 Set:

```
Virtual machine name:

Wazuh-Server
```

 Example:

```
Wazuh-Server
```

 Choose where you want to store the VM.

 Example:

```
D:\VMware\Wazuh-Server
```

 Click:

```
Next
```

---

 # 8\. Configure Virtual Disk

 VMware will ask for disk size.

 Set:

```
100 GB
```

 For Wazuh, 100 GB is a good starting point for a small lab.

 Select:

```
Store virtual disk as a single file
```

 Click:

```
Next
```

---

 # 9\. Customize Hardware

 Before finishing the VM creation, click:

```
Customize Hardware
```

 We need to configure:

```
CPU
RAM
Network
CD/DVD
```

---

 # 10\. Configure RAM

 Select:

```
Memory
```

 Set:

```
8192 MB
```

 This equals:

```
8 GB RAM
```

 The configuration should look like:

```
Memory:

8192 MB
```

 Do not give all of your physical computer's RAM to the VM.

 For example, if your physical computer has 16 GB RAM:

```
Physical PC:
16 GB

Wazuh VM:
8 GB

Remaining:
~8 GB
```

---

 # 11\. Configure CPU

 Select:

```
Processors
```

 Configure:

```
Number of processors:
1

Number of cores per processor:
4
```

 Total:

```
4 vCPU
```

 You can also configure:

```
Number of processors:
4

Number of cores per processor:
1
```

 The important part is:

```
Total CPU cores = 4
```

 Recommended:

```
Processors: 1
Cores per processor: 4
```

---

 # 12\. Configure Network

 Select:

```
Network Adapter
```

 You will normally see:

```
NAT
Bridged
Host-only
```

 For a Wazuh lab, use either:

```
NAT
```

 or:

```
Bridged
```

---

 # 13\. Option A — NAT

 Choose:

```
NAT
```

 NAT allows the VM to access the Internet through the VMware host.

 Network diagram:

```
Internet
   |
   |
Physical PC
   |
   |
VMware NAT
   |
   |
Ubuntu VM
```

 This is easy and usually works immediately.

 Use NAT if you mainly need:

```
Ubuntu -> Internet
```

---

 # 14\. Option B — Bridged Network

 Choose:

```
Bridged
```

 The Ubuntu VM becomes another machine on your physical network.

 Example:

```
Router
 |
 +---- Physical PC
 |
 +---- Ubuntu VM
 |
 +---- Other PCs
```

 Example IP addresses:

```
Physical PC:
192.168.1.10

Ubuntu VM:
192.168.1.50

Router:
192.168.1.1
```

 This is useful if other machines need to communicate directly with your Wazuh server.

 For a Wazuh lab where you plan to install agents on other machines, **Bridged** is often convenient.

---

 # 15\. Recommended Network Configuration

 For this Wazuh lab:

```
Network Adapter:
Bridged

Connect at power on:
Enabled
```

 If Bridged does not work in your environment, use:

```
NAT
```

 You can change this later.

---

 # 16\. Configure CD/DVD

 Select:

```
CD/DVD
```

 Choose:

```
Use ISO image file
```

 Click:

```
Browse
```

 Select your Ubuntu ISO:

```
ubuntu-24.04.x-live-server-amd64.iso
```

 Make sure:

```
Connect at power on
```

 is enabled.

---

 # 17\. Recommended Final VM Hardware

 Before closing the hardware settings, verify:

```
CPU:
4 cores

RAM:
8192 MB

Disk:
100 GB

Network:
Bridged

CD/DVD:
Ubuntu Server ISO

USB:
Default

Sound:
Default

Display:
Default
```

---

 # 18\. Finish VM Creation

 Click:

```
Close
```

 Then:

```
Finish
```

 You should now see:

```
Wazuh-Server
```

 in VMware.

---

 # 19\. Start the VM

 Select:

```
Wazuh-Server
```

 Click:

```
Power on this virtual machine
```

 Ubuntu should start booting.

---

 # 20\. Ubuntu Server Boot Screen

 You should see the Ubuntu Server installer.

 Wait for the installer to load.

 You should eventually see:

```
Welcome to Ubuntu
```

---

 # 21\. Select Language

 Choose:

```
English
```

 Press:

```
Enter
```

 or click:

```
Done
```

---

 # 22\. Keyboard Layout

 Select your keyboard layout.

 For a standard US keyboard:

```
English (US)
```

 Then:

```
Done
```

---

 # 23\. Ubuntu Installation Type

 Ubuntu Server will show installation options.

 Choose the standard Ubuntu Server installation.

 For example:

```
Ubuntu Server
```

 Continue.

---

 # 24\. Configure Network

 Ubuntu should automatically detect the VMware network adapter.

 You may see something similar to:

```
enp2s0
```

 or:

```
ens33
```

 Example:

```
enp2s0
DHCP
192.168.1.50/24
```

 If you receive an IP address automatically:

```
DHCP
```

 you can continue for now.

---

 # 25\. Check Network Information

 You may see:

```
IP Address:
192.168.1.50
```

 Write this address down.

 Your actual address will probably be different.

 Example:

```
Ubuntu VM IP:

192.168.1.50
```

---

 # 26\. Static IP — Optional During Installation

 For a Wazuh server, a static IP is recommended.

 If you already know your network configuration, you can configure it now.

 Example:

```
Subnet:
192.168.1.0/24

Ubuntu IP:
192.168.1.50

Gateway:
192.168.1.1

DNS:
8.8.8.8
```

 Do NOT blindly use these values.

 Use the values appropriate for your network.

 If you are not sure, select:

```
DHCP
```

 and configure the static IP after Ubuntu installation.

---

 # 27\. Proxy Configuration

 Ubuntu may ask:

```
Configure proxy
```

 If you do not use a proxy:

```
Leave blank
```

 Then:

```
Done
```

---

 # 28\. Ubuntu Archive Mirror

 Ubuntu may show:

```
Ubuntu archive mirror
```

 Leave the default unless you have a specific reason to change it.

 Click:

```
Done
```

 Ubuntu will test the mirror.

---

 # 29\. Storage Configuration

 Ubuntu will ask how to configure storage.

 For a dedicated Wazuh VM, you can use:

```
Use an entire disk
```

 Select the VMware virtual disk.

 It should be approximately:

```
100 GB
```

 Example:

```
/dev/sda
100 GB
```

---

 # 30\. Storage Layout

 For a simple Wazuh lab, use:

```
Use an entire disk
```

 You do not need a complicated partition layout.

 Ubuntu will create the required partitions.

 Review the storage configuration carefully.

 Then select:

```
Done
```

 Ubuntu will warn that data will be destroyed.

 Because this is a new VMware virtual disk, select:

```
Continue
```

---

 # 31\. Create Ubuntu User

 Ubuntu will ask for your profile information.

 Example:

```
Your name:
Wazuh Administrator

Server name:
wazuh-server

Username:
wazuhadmin

Password:
YOUR_STRONG_PASSWORD
```

 Example:

```
Name:
Wazuh Administrator

Server name:
wazuh-server

Username:
wazuhadmin
```

 Use a strong password.

---

 # 32\. Server Name

 Set:

```
wazuh-server
```

 This will become the Ubuntu hostname.

 Example:

```
Your server's name:
wazuh-server
```

---

 # 33\. SSH Configuration

 Ubuntu will ask:

```
Install OpenSSH server?
```

 Select:

```
Install OpenSSH server
```

 This is recommended.

 It allows you to connect remotely:

```
ssh wazuhadmin@SERVER_IP
```

 Continue.

---

 # 34\. Additional Server Software

 Ubuntu may offer additional packages or applications.

 For the initial Wazuh server:

```
Do not select unnecessary additional software
```

 You can install software later.

 Continue.

---

 # 35\. Start Ubuntu Installation

 Ubuntu will now install the operating system.

 You should see something similar to:

```
Installing system
```

 Wait for the installation to finish.

 Do not power off the VM.

---

 # 36\. Installation Complete

 When Ubuntu finishes, you should see:

```
Install complete
```

 Select:

```
Reboot Now
```

---

 # 37\. Remove Ubuntu ISO

 After reboot, VMware may ask you to remove the installation media.

 If necessary:

```
VM
>
Settings
>
CD/DVD
```

 Disconnect the ISO.

 Or select:

```
Disconnect
```

 Then reboot the VM.

 This prevents VMware from starting the Ubuntu installer again.

---

 # 38\. First Ubuntu Boot

 After reboot, you should see something similar to:

```
Ubuntu 24.04 LTS wazuh-server tty1
```

 You will also see:

```
wazuh-server login:
```

---

 # 39\. Login

 Enter the username you created.

 Example:

```
login:
wazuhadmin
```

 Enter your password.

 You should now be logged into Ubuntu.

---

 # 40\. Check Hostname

 Run:

```
hostname
```

 Expected:

```
wazuh-server
```

---

 # 41\. Check IP Address

 Run:

```
ip addr
```

 Look for your network interface.

 Example:

```
enp2s0:
    inet 192.168.1.50/24
```

 You can use the easier command:

```
hostname -I
```

 Example:

```
192.168.1.50
```

 Write down this IP.

---

 # 42\. Check Internet

 Run:

```
ping -c 4 google.com
```

 You should receive replies.

 Example:

```
64 bytes from ...
64 bytes from ...
64 bytes from ...
64 bytes from ...
```

 If this works:

```
Ubuntu VM -> Internet
```

 is working.

---

 # 43\. Check DNS

 Run:

```
getent hosts google.com
```

 You should receive an IP address.

---

 # 44\. Check CPU

 Run:

```
nproc
```

 Expected:

```
4
```

---

 # 45\. Check RAM

 Run:

```
free -h
```

 You should see approximately:

```
total
7.5Gi
```

 The exact number may be slightly lower than 8 GB.

---

 # 46\. Check Disk

 Run:

```
df -h
```

 You should see approximately:

```
/dev/sda
100G
```

 The exact output depends on the Ubuntu partition layout.

---

 # 47\. Update Ubuntu

 Run:

```
sudo apt update
```

 Then:

```
sudo apt upgrade -y
```

 Wait for the update to finish.

---

 # 48\. Reboot After Updates

 Run:

```
sudo reboot
```

 Wait for Ubuntu to restart.

 Login again.

---

 # 49\. Test SSH From Your Computer

 From your Windows computer, open PowerShell.

 Run:

```
ssh wazuhadmin@192.168.1.50
```

 Replace:

```
192.168.1.50
```

 with the IP of your Ubuntu VM.

 Example:

```
ssh wazuhadmin@192.168.1.50
```

 Enter your Ubuntu password.

 If you can login:

```
Windows PC
    |
    | SSH
    v
Ubuntu VM
```

 SSH is working.

---

 # 50\. Check SSH Service

 Inside Ubuntu:

```
sudo systemctl status ssh
```

 You want:

```
Active: active (running)
```

 Press:

```
q
```

 to exit.

---

 # 51\. Check Network Configuration

 Run:

```
ip addr
```

 Then:

```
ip route
```

 You should have a default route.

 Example:

```
default via 192.168.1.1
```

---

 # 52\. Final Ubuntu VM Check

 Run:

```
echo "===== HOSTNAME ====="
hostname

echo "===== IP ADDRESS ====="
hostname -I

echo "===== CPU ====="
nproc

echo "===== RAM ====="
free -h

echo "===== DISK ====="
df -h /

echo "===== NETWORK ====="
ip route

echo "===== SSH ====="
systemctl is-active ssh
```

 Expected:

```
===== HOSTNAME =====
wazuh-server

===== IP ADDRESS =====
192.168.1.50

===== CPU =====
4

===== RAM =====
approximately 8 GB

===== DISK =====
approximately 100 GB

===== NETWORK =====
default via 192.168.1.1

===== SSH =====
active
```

---

 # 53\. VMware VM Final Configuration

 Your VMware VM should now look approximately like:

```
VM Name:
Wazuh-Server

Operating System:
Ubuntu Server 24.04 LTS

CPU:
4 cores

RAM:
8 GB

Disk:
100 GB

Network:
Bridged

Firmware:
UEFI

CD/DVD:
Ubuntu ISO disconnected after installation

SSH:
Enabled

Hostname:
wazuh-server
```

---

 # 54\. Network Architecture

 If using Bridged networking:

```
                 INTERNET
                    |
                    |
                 ROUTER
              192.168.1.1
                    |
          +---------+---------+
          |                   |
          |                   |
      Windows PC          VMware Host
      192.168.1.10             |
                                |
                            VMware VM
                                |
                                |
                         Ubuntu Server
                         wazuh-server
                         192.168.1.50
```

 The actual IP addresses depend on your network.

---

 # 55\. If Using NAT

 If you selected NAT instead of Bridged:

```
                 INTERNET
                    |
                    |
              Physical PC
                    |
              VMware NAT
                    |
                    |
              Ubuntu VM
              wazuh-server
```

 The Ubuntu VM will receive a VMware NAT address.

 Check it with:

```
hostname -I
```

 NAT is fine for testing Wazuh, but if other physical machines need to connect directly to your Wazuh server, Bridged networking is often easier.

---

 # 56\. Ubuntu Server Installation Is Complete

 At this point you have:

```
VMware
   |
   +-- Wazuh-Server VM
          |
          +-- Ubuntu Server 24.04 LTS
          |
          +-- 4 CPU cores
          |
          +-- 8 GB RAM
          |
          +-- 100 GB Disk
          |
          +-- Network
          |
          +-- SSH
          |
          +-- Internet
```

 The Ubuntu Server VM is now ready for the next stage:

```
Ubuntu Server
      |
      v
Wazuh Installation
      |
      +-- Wazuh Manager
      +-- Wazuh Indexer
      +-- Wazuh Dashboard
      +-- Filebeat
```

 # END

```
Have a nice day
```
