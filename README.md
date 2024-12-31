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

## Tools used in this project :-
- (1) **Vmware**
- (2) **Ubuntu**
- (3) **Snort installed in ubuntu**
- (4) **windows machine for request generate**

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

- Now, (type **sudo ip link set (your interface name like ens0) promisc on**) & hit enter . (eg:- **sudo ip link set ens33 promisc on**) . By this ,Promiscuous mode is enabled on the network interface card (NIC) when using Snort to allow it to capture all network traffic passing through the interface, not just the traffic intended for that specific machine.
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 11_59_07 AM](https://github.com/user-attachments/assets/66cf87a5-a3af-445f-9fdd-594a40d1c3a6)

- After sucessfully install the snort check the conguration file which is very important and core file  of the snort . (type **ls /etc/snort** ) & hit enter . The snort files are generally located in the /etc/ location.
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 12_08_16 PM](https://github.com/user-attachments/assets/837dcb09-e3f8-41f9-a36b-52abcc8a9d8e)
- Now open the **snort.conf** file for configuration (Type **sudo vim /etc/snort/snort.conf** ) . It will open the configuration file for configuration the snort.
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 2_46_17 PM](https://github.com/user-attachments/assets/e2b6fb35-dc2b-4d4c-b72f-3754c917cba3)

- Now the configuration file is open . Scroll down and under the step1 section there will be an interface of **ip var $HOME_NET any** . This is for the actual network we want to monitor . We have give the ip range of our network which we want to monitor . In my case it is **192.168.190.131/24** .
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 2_57_50 PM](https://github.com/user-attachments/assets/c5db7327-a22e-4d5b-a84c-f68b8e6b5e34)

- There will be *ipvar EXTERNAL_NET any . Leave it as it is because we want to monitor the traffic from any network or any incoming traffic so leave it as it is.
- There will be local.rules file this file contain the rules which is created by snort by default . We want to create our own rules so comment these rules so snort ignor them . From **local.rules to befor step 8 line . ( Type line from to (eg:- in my case it is from 592,717/^/#) . it will comment down the line from 592 to 717 which snort will ignore so that we can make our own rules.
  ![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 3_17_25 PM](https://github.com/user-attachments/assets/c1558d3d-19e5-42cb-9b53-0ec24049af30)

- Now ( **type :wq**) to save the file and exit.
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 3_23_36 PM](https://github.com/user-attachments/assets/576ac473-d8b2-442e-9a80-bedf085d69e1)

- Now just check once the snort.config file to ensure that every community rule is commented or remove . ( Type **sudo snort -T -i ens33 -c /etc/snort/snort.conf** ) and hit enter.
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 3_24_56 PM](https://github.com/user-attachments/assets/4a739836-5a70-4b2d-b718-a2c8bdb061fb)

- We can see that there is no rule in the snort.conf file.
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 3_32_45 PM](https://github.com/user-attachments/assets/7e9bd298-d051-4998-b084-4d5999fc4902)
- We have completed the configuration of snort let's begin with writing our own rules.

## Step 3 :- Making the snort rules.
- For making our own rules ( Type **sudo vim /etc/snort/rules/local.rules** ) and hit enter . The file will open and let's write our first rule.
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 3_40_21 PM](https://github.com/user-attachments/assets/f2ab01e4-af7b-417a-947e-9f741802bae9)

- We are going to write an icmp rule that will detect or monitor any icmp packet coming to our network . For this type **alert icmp any any -> $HOME_NET any (msg : "icmp packet detected" ; sid:10001 ; rev:1;)
- alert icmp any means any ip any means any port traffic comming to any ip range of home network will generate the alert the icmp packet detected . sid:10001 = id of the signature , rev:1 = version of the signature . It will generate the alert when any traffic is come to hoem network .
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 4_14_12 PM](https://github.com/user-attachments/assets/e24c6316-66a2-43da-845a-c194f05f398c)
- Now we are going to run the snort ( type **sudo snort -q -l /var/log/snort -i ens33 -A console -c /etc/snort/snort.conf** ) and hit enter.
- Note ( **-q = quite mode , -l = set the logging directory , i = interface , A = alert**)
- Now open the windows terminal and type **ping ip_address_of_ubuntu_machine** (eg: ping 192.168.190.131) & hit enter . It will send the icmp ping request to the ubuntu machine which will be detected by snort . We can see in the picture .
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 8_45_14 PM](https://github.com/user-attachments/assets/92d5beb5-6a67-44e4-8767-2b2adf9eb830)
- That means our snort is generating an alarm when someone is trying to send the icmp ping request to our snort IDS.

- (2) Write the rule of ssh login :- when someone try to login with ssh to our ubuntu machine the snort should generate an alert .
-  type (**alert ssh any any -> $HOME_NET 192.168.190.131 ( msg : "ssh Authentication detected: ; sid:1002 ; rev:1;**)
- Now type on windows terminal (**ssh 192.168.190.131) . It will try to login ssh to our ubuntu machine and our snort will generate an alarm .
![Ubuntu 64-bit - VMware Workstation 17 Player (Non-commercial use only) 12_31_2024 8_45_14 PM](https://github.com/user-attachments/assets/d3dbb6cc-5e6a-419e-aba6-62a95a05afda)

- We can see the log files which snort generate in ( **etc/var/log/snort** )
  ![(4) Intrusion Detection With Snort - YouTube - Google Chrome 12_31_2024 9_06_57 PM](https://github.com/user-attachments/assets/da2e90cf-6e96-4253-b90a-9f58c1c94bdd)

  - We can also check the log files in wireshark by uploading the log file on wireshark.

  ## Conclusion :-
Setting up a Snort home lab is a significant milestone in advancing your understanding of intrusion detection and prevention systems (IDS/IPS). Through this project, you have achieved the following:
Practical Experience: You gained hands-on experience in configuring Snort, a powerful open-source IDS/IPS tool, enhancing your practical skills in network security.
Network Traffic Analysis: By capturing and analyzing network traffic, you developed a deeper understanding of normal and malicious network behaviors, crucial for identifying security threats.
Rule Creation and Tuning: Writing and tuning Snort rules allowed you to customize detection mechanisms, improving your ability to respond to specific security scenarios.
Home Lab Integration: Integrating Snort into your home lab environment provided a controlled setup to simulate real-world scenarios, helping bridge theoretical knowledge with practical application.
Foundation for Advanced Security Practices: This project serves as a foundation for exploring advanced topics such as threat hunting, incident response, and integrating Snort with other security tools like SIEM systems.









  
 




 









