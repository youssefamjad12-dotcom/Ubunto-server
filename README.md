 # Ubuntu Server Installation on VMware

 ## Goal

 Create a VMware virtual machine and install **Ubuntu Server 24.04 LTS** as the operating system for a Wazuh server.

 ### VM Specifications

 | Setting | Value |
| --- | --- |
| Operating System | Ubuntu Server 24.04 LTS |
| CPU | 4 vCPUs |
| RAM | 8 GB |
| Disk | 60 GB |
| Network | NAT or Bridged |
| Firmware | UEFI |
| VM Name | Wazuh-Server |
| Hostname | wazuh-server |

---

 ## 1\. Download the Ubuntu Server ISO

 Download the Ubuntu Server 24.04 LTS ISO from the official Ubuntu website:

 https://ubuntu.com/download/server

 Download:

```
Ubuntu Server 24.04 LTS
```

 The file name should look similar to:

```
ubuntu-24.04.x-live-server-amd64.iso
```

 Save the ISO somewhere that is easy to find.

 Example:

```
C:\ISO\ubuntu-24.04.x-live-server-amd64.iso
```

---

 ## 2\. Open VMware

 Open:

```
VMware Workstation
```

 Then select:

```
Create a New Virtual Machine
```

 Alternatively, use:

```
File
>
New Virtual Machine
```

---

 ## 3\. Select the Virtual Machine Type

 VMware will display the **New Virtual Machine Wizard**.

 Select:

```
Typical (recommended)
```

 Click:

```
Next
```

---

 ## 4\. Select the Ubuntu ISO

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

 ## 5\. Easy Install

 VMware may automatically detect Ubuntu and display fields such as:

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

 However, for learning and troubleshooting, a manual Ubuntu installation can be easier to understand.

 If you want to perform the installation manually, select:

```
I will install the operating system later
```

 Then click:

```
Next
```

 If you choose the manual installation option, attach the Ubuntu ISO to the VM later.

---

 ## 6\. Select the Guest Operating System

 If VMware asks for the guest operating system, select:

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

 ## 7\. Name the Virtual Machine

 Set the virtual machine name to:

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

 ## 8\. Configure the Virtual Disk

 VMware will ask for the disk size.

 Set:

```
100 GB
```

 For a small Wazuh lab, 100 GB is a reasonable starting point. Actual storage requirements depend on the number of agents, event volume, retention period, and other Wazuh configuration choices.

 Select:

```
Store virtual disk as a single file
```

 Click:

```
Next
```

---

 ## 9\. Customize Hardware

 Before finishing the VM creation, click:

```
Customize Hardware
```

 Configure the following:

```
CPU
Memory
Network Adapter
CD/DVD
```

---

 ## 10\. Configure RAM

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

 Do not allocate all of your physical computer's RAM to the VM.

 For example, if your physical computer has 16 GB of RAM:

```
Physical PC:
16 GB

Wazuh VM:
8 GB

Remaining:
~8 GB
```

 The host operating system and other applications also need sufficient memory.

---

 ## 11\. Configure CPU

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

 This gives the VM:

```
Total:
4 vCPUs
```

 You could also configure:

```
Number of processors:
4

Number of cores per processor:
1
```

 For this lab, the recommended configuration is:

```
Processors: 1
Cores per processor: 4
```

 The important point is that the VM has a total of **4 vCPUs**.

---

 ## 12\. Configure the Network

 Select:

```
Network Adapter
```

 You will normally see options such as:

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

 ## 13\. Option A — NAT Networking

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

 NAT is easy to configure and usually works without additional network configuration.

 Use NAT if you mainly need:

```
Ubuntu VM -> Internet
```

---

 ## 14\. Option B — Bridged Networking

 Choose:

```
Bridged
```

 With bridged networking, the Ubuntu VM appears as another device on your physical network.

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

 The actual IP addresses will depend on your network.

 Bridged networking can be convenient when other physical machines need to communicate directly with the Wazuh server.

---

 ## 15\. Recommended Network Configuration

 For a Wazuh lab, you can use:

```
Network Adapter:
Bridged

Connect at power on:
Enabled
```

 If Bridged networking does not work in your environment, use:

```
NAT
```

 You can change the network mode later.

---

 ## 16\. Configure CD/DVD

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

 ## 17\. Verify the Final VM Hardware

 Before closing the hardware settings, verify the following:

```
CPU:
4 vCPUs

RAM:
8192 MB

Disk:
100 GB

Network:
Bridged

CD/DVD:
Ubuntu Server ISO

Firmware:
UEFI
```

 Other devices can normally remain at their default settings unless you have a specific requirement.

---

 ## 18\. Finish VM Creation

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

 ## 19\. Start the VM

 Select:

```
Wazuh-Server
```

 Click:

```
Power on this virtual machine
```

 Ubuntu should begin booting.

---

 # Ubuntu Server Installation

 ## 20\. Ubuntu Server Boot Screen

 You should see the Ubuntu Server installer.

 Wait for the installer to load.

 You should eventually see a screen similar to:

```
Welcome to Ubuntu
```

---

 ## 21\. Select the Language

 Choose:

```
English
```

 Then select:

```
Done
```

---

 ## 22\. Configure the Keyboard Layout

 Select your keyboard layout.

 For a standard US keyboard:

```
English (US)
```

 Then select:

```
Done
```

---

 ## 23\. Select the Ubuntu Installation Type

 Ubuntu Server will display the available installation options.

 Select the standard:

```
Ubuntu Server
```

 Continue with the installation.

---

 ## 24\. Configure the Network

 Ubuntu should automatically detect the VMware network adapter.

 You may see an interface such as:

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

 If Ubuntu automatically receives an IP address through DHCP, you can continue with DHCP for now.

---

 ## 25\. Check the Network Information

 You may see an IP address such as:

```
192.168.1.50
```

 Write down the IP address.

 Your actual address will probably be different.

 Example:

```
Ubuntu VM IP:

192.168.1.50
```

---

 ## 26\. Static IP — Optional During Installation

 A static IP address is useful for a server such as Wazuh because other systems may need to connect to it.

 If you already know your network configuration, you can configure a static IP during installation.

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

 **Do not blindly use these values.**

 Use the network settings appropriate for your environment.

 If you are unsure about your network configuration, select:

```
DHCP
```

 and configure a static address later.

---

 ## 27\. Proxy Configuration

 Ubuntu may ask:

```
Configure proxy
```

 If you do not use a proxy, leave the field blank.

 Then select:

```
Done
```

---

 ## 28\. Ubuntu Archive Mirror

 Ubuntu may display:

```
Ubuntu archive mirror
```

 Leave the default mirror unless you have a specific reason to change it.

 Select:

```
Done
```

 Ubuntu will test the mirror.

---

 ## 29\. Configure Storage

 Ubuntu will ask how you want to configure the storage.

 For a dedicated Wazuh lab VM, you can select:

```
Use an entire disk
```

 Select the VMware virtual disk.

 It should be approximately:

```
100 GB
```

 For example:

```
/dev/sda
100 GB
```

---

 ## 30\. Review the Storage Layout

 For a simple Wazuh lab, you can use:

```
Use an entire disk
```

 You do not need a complicated partition layout for this basic installation.

 Ubuntu will create the required partitions.

 Review the proposed storage configuration carefully.

 Then select:

```
Done
```

 Ubuntu will warn that existing data on the selected disk will be destroyed.

 Because this is a new VMware virtual disk, select:

```
Continue
```

---

 ## 31\. Create the Ubuntu User

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

 For example:

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

 ## 32\. Set the Server Name

 Set the hostname to:

```
wazuh-server
```

 For example:

```
Your server's name:
wazuh-server
```

 This will become the Ubuntu hostname.

---

 ## 33\. Configure SSH

 Ubuntu will ask:

```
Install OpenSSH server?
```

 Select:

```
Install OpenSSH server
```

 This is useful because it allows you to connect to the server remotely.

 For example:

```
ssh wazuhadmin@SERVER_IP
```

 Continue with the installation.

---

 ## 34\. Additional Server Software

 Ubuntu may offer additional packages or applications.

 For the initial Wazuh server installation:

```
Do not select unnecessary additional software.
```

 You can install additional software later when required.

 Continue with the installation.

---

 ## 35\. Start the Ubuntu Installation

 Ubuntu will now install the operating system.

 You should see something similar to:

```
Installing system
```

 Wait for the installation to finish.

 Do not power off the VM during the installation.

---

 ## 36\. Installation Complete

 When the installation finishes, you should see:

```
Install complete
```

 Select:

```
Reboot Now
```

---

 ## 37\. Remove the Ubuntu ISO

 After the VM reboots, VMware may still have the Ubuntu ISO connected.

 If necessary, open:

```
VM
>
Settings
>
CD/DVD
```

 Disconnect the ISO or disable:

```
Connect at power on
```

 Then reboot the VM if necessary.

 This prevents VMware from booting into the Ubuntu installer again.

---

 # First Ubuntu Boot

 ## 38\. First Ubuntu Boot

 After rebooting, you should see something similar to:

```
Ubuntu 24.04 LTS wazuh-server tty1
```

 You should also see:

```
wazuh-server login:
```

---

 ## 39\. Log In

 Enter the username you created during installation.

 Example:

```
login:
wazuhadmin
```

 Enter your password.

 You should now be logged into Ubuntu.

---

 ## 40\. Check the Hostname

 Run:

```
hostname
```

 Expected output:

```
wazuh-server
```

---

 ## 41\. Check the IP Address

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

 You can also use the simpler command:

```
hostname -I
```

 Example:

```
192.168.1.50
```

 Write down this IP address.

---

 ## 42\. Test Internet Connectivity

 Run:

```
ping -c 4 google.com
```

 You should receive replies similar to:

```
64 bytes from ...
64 bytes from ...
64 bytes from ...
64 bytes from ...
```

 If this works, the following connection is working:

```
Ubuntu VM -> Internet
```

---

 ## 43\. Test DNS Resolution

 Run:

```
getent hosts google.com
```

 You should receive an IP address.

 This confirms that DNS resolution is working.

---

 ## 44\. Check CPU

 Run:

```
nproc
```

 Expected output:

```
4
```

---

 ## 45\. Check RAM

 Run:

```
free -h
```

 You should see approximately:

```
7.5Gi
```

 The exact amount may be slightly lower than 8 GB because of system and virtualization overhead.

---

 ## 46\. Check Disk Space

 Run:

```
df -h
```

 You should see approximately:

```
/dev/sda
100G
```

 The exact output depends on Ubuntu's partition layout and filesystem configuration.

---

 # Update Ubuntu

 ## 47\. Update Ubuntu

 Run:

```
sudo apt update
```

 Then:

```
sudo apt upgrade -y
```

 Wait for the updates to finish.

---

 ## 48\. Reboot After Updates

 Run:

```
sudo reboot
```

 Wait for Ubuntu to restart.

 Then log in again.

---

 # Test SSH

 ## 49\. Test SSH from Your Computer

 From your Windows computer, open PowerShell.

 Run:

```
ssh wazuhadmin@192.168.1.50
```

 Replace:

```
192.168.1.50
```

 with the actual IP address of your Ubuntu VM.

 Example:

```
ssh wazuhadmin@192.168.1.50
```

 Enter your Ubuntu password when prompted.

 If the connection succeeds:

```
Windows PC
    |
    | SSH
    v
Ubuntu VM
```

 SSH is working.

---

 ## 50\. Check the SSH Service

 Inside Ubuntu, run:

```
sudo systemctl status ssh
```

 You want to see:

```
Active: active (running)
```

 Press:

```
q
```

 to exit the status screen.

---

 # Verify the Network

 ## 51\. Check the Network Configuration

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

 The actual gateway will depend on your network.

---

 # Final Verification

 ## 52\. Run a Final Ubuntu Server Check

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

 Expected output should look approximately like:

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

 Your IP address and network gateway will depend on your environment.

---

 # 53\. Final VMware VM Configuration

 Your VMware VM should now look approximately like this:

```
VM Name:
Wazuh-Server

Operating System:
Ubuntu Server 24.04 LTS

CPU:
4 vCPUs

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

 # 54\. Network Architecture — Bridged Mode

 If you are using Bridged networking, the architecture may look like this:

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

 # 55\. Network Architecture — NAT Mode

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

 The Ubuntu VM will receive an IP address from the VMware NAT network.

 Check the IP address with:

```
hostname -I
```

 NAT is suitable for testing Wazuh. However, if other physical machines need to communicate directly with your Wazuh server, Bridged networking may be more convenient.

---

 # 56\. Ubuntu Server Installation Complete

 At this point, you have:

```
VMware
   |
   +-- Wazuh-Server VM
          |
          +-- Ubuntu Server 24.04 LTS
          |
          +-- 4 vCPUs
          |
          +-- 8 GB RAM
          |
          +-- 100 GB Disk
          |
          +-- Network
          |
          +-- SSH
          |
          +-- Internet Connectivity
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

 Have a nice day!
