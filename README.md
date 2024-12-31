# Snort-home-lab
# Intusion Detection Using Snort
## What is intrusion detection system (IDS)?
=> Intrusion detection system is a device or a software that intercept all inbound or outbound traffic  of network for suspecious pattern
- IDS is placed inside or outside the firewall
- Checks traffic for signature that match known intrusion patterns and signal an alarm

## What is Snort?
=> Snort is an open source IDS . Snort have ips capability that can detect monitor suspecious anomaly behviour in the network
- Snort can help us to detect any suspecious activity in the network level like web based attack , wifi etc.
- capability:-
- (1) Real Time Monetoring
- (2) Packet Logging
- (3) OS Fingerprinting
- (4) protocol support

## Objective of this project :-
(1) Understand Intrusion Detection Systems (IDS):
Learn the role of Snort as an IDS and its importance in network security.

(2) Install and Configure Snort:
Set up Snort in your home lab and configure it to monitor network traffic.

(3) Write  Snort Rules:
Create basic rules to detect common network patterns like  ssh , icmp ping requests.

(4) Capture and Analyze Alerts:
Generate traffic  and observe how Snort detects and logs activities.

(5) Familiarize with Snort Logging:
Understand how Snort logs alerts and review these logs for insights.

## Skill Learned :-
(*) Network Traffic Monitoring:
Understand how to capture and analyze network packets.

(*)Intrusion Detection System (IDS) Basics:
Learn the principles of IDS and how Snort functions as one.

(*)Snort Installation and Configuration:
Gain practical experience setting up and configuring Snort for various network environments.

(*)Rule Creation and Management:
Write and manage Snort rules to detect specific network activities or threats.

(*)Log Analysis:
Interpret and analyze Snort alert logs to identify security incidents.

(*)Network Protocol Understanding:
Deepen your knowledge of protocols like TCP, UDP, HTTP, and ICMP while working with traffic data.

## Let's Begin....

## Step 1 :- Update the ubuntu Packages.
- First we need to install the snort on ubuntu machine .
- open the ubuntu terminal and make sure every package is update and upgrade . for this ( Type **sudo apt-get update && apt-get upgrade**) and hit enter
![Administrator_ Command Prompt 12_31_2024 11_29_20 AM](https://github.com/user-attachments/assets/e96cf8c8-75d4-4b03-97fc-e037b44021b6)

## Step 2 :- Download & Confighure Snort.
- After updating the ubuntu packages let's install Sort .
- Open the ubuntu terminal ( type **sudo apt install snort** ) & hit enter.
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 11_40_45 AM](https://github.com/user-attachments/assets/af85358d-2828-427c-a0bb-d3da2d787809)

- After the installation the snort window will appear and it will ask for ip range . If we are suing the virual machine and if so we have to give the range like (**192.168.19.0/24**) and if we are suing on cloud and single machine the we can give the ip address like (**192.168.190.131/24**) .
- To check the ip range and interface of the network in ubuntu terminal ( type **ip addr**) it will show ip address and interface .
  ![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 11_49_10 AM](https://github.com/user-attachments/assets/eff17a77-e439-45ab-9d0f-46b84d85025e)
- In my case my ip range is **192.168.190.131/24** . I am using the virtual machine and i want to add ip range so i will type **192.168.190.0/24** in snort ip section.
 - Snort will install .
 - To check if install is install properly or not open ubuntu terminal and ( Type **snort --version**) & hit enter . If snort is downloaded successfully it will show the ineterface like..
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 11_55_49 AM](https://github.com/user-attachments/assets/de4daf5c-9383-49d9-bcae-cb20a4fb0136)

- Now, (type **sudo ip link set (your interface name like ens0) promisc on**) & hit enter . (eg:- **sudo ip link set ens33 promisc on) . By this ,Promiscuous mode is enabled on the network interface card (NIC) when using Snort to allow it to capture all network traffic passing through the interface, not just the traffic intended for that specific machine.
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 11_59_07 AM](https://github.com/user-attachments/assets/66cf87a5-a3af-445f-9fdd-594a40d1c3a6)

- After sucessfully install the snort check the conguration file which is very important and core file  of the snort . (type **ls /etc/snort** ) & hit enter . The snort files are generally located in the /etc/ location.
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 12_08_16 PM](https://github.com/user-attachments/assets/837dcb09-e3f8-41f9-a36b-52abcc8a9d8e)


 









