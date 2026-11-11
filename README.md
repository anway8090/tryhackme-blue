# tryhackme-blue
Completed TryHackMe Blue Room using Kali Linux Practiced Nmap scanning SMB enumeration MS17-010 EternalBlue vulnerability identification Metasploit exploitation Meterpreter sessions Windows privilege inspection and NTLM hash analysis using John the Ripper Gained practical beginner-level experience in Windows penetration testing and CTF flag hunting
# TRYHACKME – BLUE ROOM
### Practical Penetration Testing Lab (Kali Linux)

**Level:** Beginner  
**Platform:** TryHackMe  
**Target OS:** Windows  
**Tools:** Kali Linux, Nmap, Metasploit Framework, Meterpreter, John the Ripper

## Project Overview

Completed the Blue Room practical lab on TryHackMe to understand Windows penetration testing and SMB vulnerability exploitation in an authorized lab environment.

The main objective was to identify open ports, discover vulnerabilities, gain access to the target Windows machine, inspect system privileges, analyze password hashes, and locate three CTF flags.

## 1. Network Reconnaissance

Started by checking network interfaces using `ip -br addr`. Identified the TryHackMe VPN interface (`tun0`) and obtained the local VPN IP address.

Used Nmap to scan the target machine:

`nmap -sV -sC -p- <TARGET_IP>`

Identified open ports and running services.

## 2. SMB Vulnerability Identification

Performed an SMB vulnerability scan on port 445 using:

`nmap -p445 --script smb-vuln-ms17-010 <TARGET_IP>`

Identified the MS17-010 vulnerability, also known as EternalBlue, associated with Windows SMB.

## 3. Exploitation Using Metasploit

Launched Metasploit Framework and searched for the MS17-010 exploit module.

Configured the target IP, Kali VPN IP, and Meterpreter reverse TCP payload.

Successfully established a Meterpreter session with the target Windows machine in the authorized lab.

## 4. Post-Exploitation

Used Meterpreter commands to inspect the compromised system:

- `getuid` – Identify the current user.
- `sysinfo` – Retrieve system information.
- `getprivs` – Inspect available privileges.
- `hashdump` – Extract Windows password hashes.
- `background` – Background the Meterpreter session.

## 5. Password Hash Analysis

Used John the Ripper to perform offline NTLM password hash analysis with the RockYou wordlist.

Commands included:

- `john --format=NT --wordlist=rockyou.txt jon.hash`
- `john --show --format=NT jon.hash`

## 6. CTF Flag Hunting

Explored Windows directories through Meterpreter and investigated three flag locations:

1. `C:\flag1.txt`
2. `C:\Windows\System32\config\flag2.txt`
3. `C:\Users\Jon\Documents\flag3.txt`

## Skills Learned

- Network reconnaissance
- Nmap scanning and enumeration
- SMB vulnerability assessment
- MS17-010 / EternalBlue concepts
- Metasploit Framework
- Meterpreter basics
- Windows privilege inspection
- NTLM hash analysis
- John the Ripper
- CTF flag discovery

**Project Status:** Meterpreter access successfully established. Password cracking, privilege escalation, and all three flag submissions require separate verification.

**Learning Outcome:** Gained practical beginner-level experience with Windows penetration testing workflows using Kali Linux in a controlled TryHackMe environment.
