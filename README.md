# standalone-poc-ftp-attack

# OVERVIEW

As discussed in the previous attack using a malicious backdoor exploit from using the Metasploit Framework , the same attack can generally be performed by a standalone POC a python script that also spawns a backdoor in the intentionally vulnerable metasploitable2 machine using the same ftp version.

# Disclaimer 

The attack simulation to be shown was performed in a closed network using one attack machine and one intentionally vulnerable machine. Please do not attempt to perform this attack on networks you do not own or have explicit permission to perform the specified attack.

# INFORMATION GATHERING

TOOLS USED
1. nmap
2. ping

The first step was to ping the vulnerable machine

ping -c 4 <target-ip>

RESULT 

4 packets transmitted 0% packet loss

The second step was to use the network mapper to identify  the port 21 ftp service

nmap -sV -sC -p21 <target-ip>

RESULT 

port = 21\tcp

State = open

version = vsftpd 2.3.4

# Enumeration 

ports found open were 

port 22 - supporting OpenSSH
port 21 - supporting ftp

we then focused on the ftp 

found the specific version 

vsftpd 2.3.4

# vulnerability Analysis

Further researching the version vsftpd 2.3.4 using the searchsploit command 

searchsploit vsftpd 2.3.4 

Result

A backdoor vulnerability was found a standalone POC and a Metasploit one

# Exploitation

I then began the exploitation phase using the standalone POC 

first:

  searchsploit -m EDB

this copies the exploit database POC to your current working directory 

you can now run the POC using either python3 or python2 

I used python2

Process

python2 <EDB-POC> <target-ip>

Result

BACKDOOR SHELL PROCESS BEGAN !!!!!

# POST-EXPLOITATION

1.ACESS GAINED

Privilege - Root 

2.System information

OS - Ubuntu Linux
Architecture - x86

3.NETWORK INFORMATION

IP Address - NIL

# END

The above exercise shows the steps taken in order to fully compromise a machine all the way from simple information gathering to the end result of exploitation. This goes to show how simple attackers can eventually gain full access to a machine with nothing but basic information.


# PROTECTIVE STEPS TO BE TAKEN

1. Remove unsupported software
2. Disable unused services
3. Restrict Network Acess
4. Use strong Authentication
5. Update or patch the software

# EPILOGUE 

Attacks like this WILL happen because of humans as the weak link . That is why we need people like us Cybersecurity Specialists to help in patching that link
