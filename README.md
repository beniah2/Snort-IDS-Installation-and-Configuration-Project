# Snort IDS Installation and Configuration Project


I was assigned to install Snort on my Linux system, configure the core settings and prepare the IDS for live traffic analysis. I documented each step, the commands used and the reasoning behind them to produce a workable and reliable setup.

Objectives
• Install Snort on a Debian based system.
• Configure the network interface and subnet.
• Enable promiscuous mode for full packet capture.
• Locate and verify the default Snort configuration files.
• Prepare the environment for rule testing and log analysis.


---

### Project Story and Workflow

1. ## Installing Snort
I started by installing Snort. I updated my system, then ran the package installation command. This confirmed all dependencies were ready and Snort binaries were in place.

Command used:
sudo apt-get install snort -y


<img width="1190" height="361" alt="image" src="https://github.com/user-attachments/assets/b8d74211-80e5-43e7-9033-0da956e1723e" />

---

2. ## Selecting the Monitoring Interface
I needed Snort to listen on the correct interface. I checked available interfaces and confirmed my active one.

Command used:
ip a

I then noted the device name, which in my case was eth0.


<img width="1061" height="430" alt="image" src="https://github.com/user-attachments/assets/17145c7e-3303-4d4a-9a47-9cd96e26d4d9" />

---


3. ## Enabling Promiscuous Mode
I switched the interface to promiscuous mode to allow Snort to see all packets on the network, not only those addressed to my system.

Command used:
sudo ip link set interface promisc on

(interface should be replaced with eth0 or your actual device)


<img width="363" height="79" alt="image" src="https://github.com/user-attachments/assets/514e3e0e-de10-4475-bf4d-13e0c22d0b49" />


---

5. ## Locating the Default Configuration Directory
I checked the default Snort configuration path. This helped me verify rule files and confirm where Snort stored its settings.

Command used:
ls -al /etc/snort

<img width="732" height="346" alt="image" src="https://github.com/user-attachments/assets/cf180159-ec9e-40b1-9fd4-42e80435058f" />

---

6. ## Launch the snort configuration file
To manually edit the configuration file and view the firewall rules, use the command below.

Command: 
sudo vim /etc/snort/snort.lua


<img width="1165" height="800" alt="image" src="https://github.com/user-attachments/assets/cc2be15f-8836-48cb-98e2-891e4557852b" />

---

7. ## Defining the Network Range
I edited the Snort configuration to set the HOME_NET variable. This step tells Snort what traffic belongs to my network.

Example syntax in snort.lua
var HOME_NET 192.168.1.0/24


<img width="1182" height="798" alt="image" src="https://github.com/user-attachments/assets/ce6f512d-3ef0-4b89-b3eb-b081e5f2df5a" />

---

7. ## Testing Configuration settings
   To view configuration settins,use the command below.

   Command:
   sudo snort -T -i eth0 -c /etc/snort/snort.lua

<img width="1066" height="790" alt="image" src="https://github.com/user-attachments/assets/4df742dc-7864-4a86-a7c5-f394c88841b9" />

   



























