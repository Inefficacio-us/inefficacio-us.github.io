---
layout: project_single
title:  "OSCP Won't Trouble Me"
slug: "OSCP"
---
<!-- Fixing my broken vim by dropping a * up top, I guess. -->

# Learnin' How To Learn
This one will be difficult.  

# Table of Contents
1. The Course
2. The Lab
3. The Exam


# 1. The Course

# 2. The Lab
The lab contains over 70 machines. These should be approached not as individual
targets, but as a whole network, in line with the pentesting methodology
outlined in the course. Helpful (necessary?) information (including credentials)
for a box can be obtained throughout the network; these are not 70 distinct CTF
challenges, but a network of 70 related hosts.  

After completing / during completion of the course material, begin working on
some lab targets. First targets should be those included in the [Learning
Path](https://help.offensive-security.com/hc/en-us/articles/360050473812-PEN-200-Labs-Learning-Path),
which contains complete write-ups of two boxes, as well as hints for another
nine. Give them an honest shot first and utilize the assistance only after
putting some effort into them.  

Be intentional about using the lab not only to develop the technical skill set.
After completing a couple of boxes you should be building up a recognizable
routine, likely one that can be scripted. You should be building up a reporting
template along with a workflow to keep it **completely** detailed and accurate
before/during/after every move you make toward a target. This might also be
scriptable. You should have an idea of how-long-is-too-long while finding your
entry/escalation points. You should have resources, relevant TTPs, exploits,
shells, common misconfigurations, etc. readily available. Build your methodology
and be methodical.  


# 3. The Exam
The exam is a proctored, 24 hour time frame in which you are presented a private
VPN instance with 'a small number' of vulnerable machines. These are made up of
three independent machines, each with 10 points available for low-privilege
access and 10 points available for privilege escalation, for an accumlative
total of 60 points. Additionally, there will be an AD domain containing one DC
and two member-workstations. There are no points awarded for partial
exploitation of the AD environment - 40 points are awarded only for full control
of the domain.  

An overall score of at minimum 70 of the possible 100 points is required to pass
the exam. 10 bonus points are available for completion of at least 10 lab
machines, including one fully exploited AD set (XOR or SVCorp, each consisting
of 4 target hosts), along with a separately-submitted report. 'Offensive
Security Complete Guide' machines, which I hope will make sense at some future
point, will not count toward the bonus points.  

The *Exam Control Panel* will detail targets, their objectives, point values,
and other details of the exam environment. This is also where you will enter
your proof submissions and revert target hosts if necessary.  

# 3.1 The Proof
Each target machine will contain at least one flag, or 'proof' file. These
proofs must be submitted to the Exam Control Panel and included in the target's
report to get credit for that target. Screenshots must show the proof being
accessed (via `type` or `cat`) from their *original location*, meaning read
directly from an interactive shell on the target host. Web shells, exfiltrated
files, etc. will not be counted. Shells must be running as root for Linux hosts
and as either SYSTEM, Administrator, or a user with Administrator privileges for
Windows hosts.  

Proofs are named `proof.txt`, accessible only to root/Administrator under /root/
or Administrator\Desktop, and `local.txt`, accessible to unprivileged users with
no location specified. Every target will have a `proof.txt` file present, while
`local.txt` will only be available on targets specified within the Exam Control
Panel.  

# 3.2 The Reports
Reports for lab machines will not be required to include enumeration steps or
detailed command output for acceptance. These can be shorter and need only show
steps taken for exploitation.  

Exam reports, however, should detail enumeration steps as well as all commands
issued and their full output for each step of the the exploitation process.
Screenshots, links to off-the-shelf exploits used, and highlighted and annotated
code of any modified exploits should also be included.  The goal with the exam
report is to enable a 'technically comptetant' reader to follow through the
process independently and successfuly reproduce your results. An OffSec-provided
template is available
[here](https://www.offensive-security.com/pwk-online/PWKv1-REPORT.doc), and
maybe I'll get around to building out a [resources](OSCP/PWKv1-Report.docx) page for this project and
dump it in there as well.  

**NOTE:**  
In addition to submitting proofs to the exam control panel, you **must** also
include a screenshot of each target's proof within the respective report. This
screenshot should the IP address of the target as well as the contents of the
proof file, accessed through an interactive shell on the target system.  

Failure to include a screenshot of the proof in a report will result in a
0-point score for that respective target. Fortunately, OffSec was kind enough to
provide an example screenshot:  
![Valid Report Screenshot](https://help.offensive-security.com/hc/article_attachments/360085581591/proof-text.png "A valid screenshot of the proof file required within each report")  

Reports must be submitted as a PDF packed into a 7z archive. The PDF file should
be named `OSCP-OS-XXXXX-Exam-Report.pdf`, substituting in your OSID. Archive
file should be named similarly, with a `.7z` extension being the only
difference. Lab reports should be uploaded similarly, with file names matching
`OSCP-OS-XXXXX-Lab-Report`.  

# 3.3 The Tools
Limitations exist in the tools and methods used during the exam. These are
detailed as follows, which I lifted directly off of the [Exam Guide](https://help.offensive-security.com/hc/en-us/articles/360040165632-OSCP-Exam-Guide):  

- Spoofing (IP, ARP, DNS, NBNS, etc)
- Commercial tools or services (Metasploit Pro, Burp Pro, etc.)
- Automatic exploitation tools (e.g. db_autopwn, browser_autopwn, SQLmap,
   SQLninja etc.)
- Mass vulnerability scanners (e.g. Nessus, NeXpose, OpenVAS, Canvas, Core
   Impact, SAINT, etc.)
- Features in other tools that utilize either forbidden or restricted exam
   limitations

The tools noted above serve only as an example of tools disallowed for their
respective categories - any tools that support similar functionality are also
prohibited. Know a quick way to request sequential files within a web directory
in Zap? Better figure it out how to script it instead.  

Exceptions exist for Nmap, including Nmap scripts, Nikto, Dirbuster, etc. Burp
Free is also listed as an approved tool, which kind of makes me rethink the
snarky remark about ZAP and will likely cause me great anxiety on exam day of
which tools might ultimately might result in a 0-point target. So that's cool.  

The use of Metasploit/Meterpreter is limited to a single target over the course
of the exam. That is, once you have utilized any Metasploit module,
vulnerability check, or Meterpreter payload against a host, whether or not it is
ultimately successful, you may not use any Metasploit functionality against any
other target.  

The only exceptions to the Metasploit limitations are the following uses:  
- multi handler (exploit/multi/handler)
- msfvenom
- pattern_create.rb
- pattern_offset.rb

I have decided those exceptions exist because the use cases are both absolutely
guaranteed to arise on each box *and* are so unnecessary for the exam that
there's no practical benefit to using them. So I guess I'll just avoid them
entirely until immediately before the exam, when I'll absolutely shift to a
state of panic for ignoring such obviously useful tactics.  

# 3.4 The Backup Plan
Should anything go wrong (technically, that is; Offensive Security is not a
licensed counselor) seek help at the [live
chat](https://chat.offensive-security.com) or by way of email at
help@offensive-security.com.  

If I didn't include these points of contact I'd have no way of getting through
the exam without some sort of catastrophe.  


# 99. References
[OSCP Exam Guide](https://help.offensive-security.com/hc/en-us/articles/360040165632-OSCP-Exam-Guide)
