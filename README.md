# Wireshark Labs

## Overview

This repository contains my hands-on Wireshark labs for learning packet capture, traffic filtering, protocol analysis, and basic network investigation skills.

The labs are beginner-friendly and focus on practical cybersecurity tasks using Wireshark, TShark, Linux commands, packet captures, display filters, capture filters, TCP streams, DNS analysis, HTTPS traffic detection, and evidence extraction.

I created this repository as part of my cybersecurity learning portfolio to document what I practiced, what tools I used, and what I learned from each lab.

## Repository Purpose

The purpose of this repository is to:

- Practice using Wireshark for network traffic analysis
- Learn how to capture and inspect packets
- Understand common network protocols such as HTTP, HTTPS, DNS, TCP, UDP, and TLS
- Practice using Wireshark capture filters and display filters
- Learn how to follow TCP streams
- Identify exposed information in packet captures
- Extract useful evidence from network traffic
- Practice using TShark from the Linux command line
- Build a cybersecurity portfolio with clear documentation and screenshots

## Tools Used

- Wireshark
- TShark
- Ubuntu Linux
- Linux terminal
- Nano text editor
- LabEx virtual machine
- Packet capture files
- Git and GitHub

## Skills Practiced

- Packet capture analysis
- Wireshark installation verification
- HTTP traffic inspection
- HTTPS traffic filtering
- DNS traffic filtering
- TCP stream analysis
- Clear-text credential discovery
- Wireshark coloring rules
- TShark command-line analysis
- DNS query extraction
- Evidence file creation
- Linux command pipelines
- GitHub documentation

## Labs

| Lab | Title | Main Focus |
|---|---|---|
| Lab 01 | Verify Wireshark Installation | Confirm Wireshark works and capture basic HTTP traffic |
| Lab 02 | Filter Encrypted Web Traffic | Filter HTTPS/TLS traffic using Wireshark |
| Lab 03 | Find Exposed Login Credentials | Search packet contents and identify clear-text credentials |
| Lab 04 | Filter DNS Communications | Capture DNS traffic using `udp port 53` |
| Lab 05 | Create HTTPS Traffic Detector | Create a Wireshark coloring rule for HTTPS traffic |
| Lab 06 | Extract Web Traffic Evidence | Use TCP stream analysis to save web traffic evidence |
| Lab 07 | Uncover Suspicious DNS Queries | Use TShark to extract DNS query names from a capture file |

## Repository Structure

```text
wireshark-labs/
├── README.md
└── labs/
    ├── 01-verify-wireshark-installation/
    │   ├── README.md
    │   └── screenshots/
    ├── 02-filter-encrypted-web-traffic/
    │   ├── README.md
    │   └── screenshots/
    ├── 03-find-exposed-login-credentials/
    │   ├── README.md
    │   └── screenshots/
    ├── 04-filter-dns-communications/
    │   ├── README.md
    │   └── screenshots/
    ├── 05-create-https-traffic-detector/
    │   ├── README.md
    │   └── screenshots/
    ├── 06-extract-web-traffic-evidence/
    │   ├── README.md
    │   └── screenshots/
    └── 07-uncover-suspicious-dns-queries/
        ├── README.md
        └── screenshots/
```

## Lab 01: Verify Wireshark Installation

In this lab, I verified that Wireshark was installed and working correctly.

I practiced capturing basic HTTP traffic and confirming that packets appeared in Wireshark. This helped me understand the Wireshark interface and basic packet capture workflow.

Main skills practiced:

- Opening Wireshark
- Starting a packet capture
- Generating HTTP traffic
- Applying a basic display filter
- Confirming captured packets

Folder:

```text
labs/01-verify-wireshark-installation/
```

## Lab 02: Filter Encrypted Web Traffic

In this lab, I practiced filtering encrypted web traffic in Wireshark.

The focus was on HTTPS and TLS traffic. I used Wireshark filters to identify encrypted connections and understand how secure web traffic appears during packet analysis.

Main skills practiced:

- Filtering HTTPS traffic
- Identifying TLS packets
- Understanding encrypted web communication
- Using Wireshark display filters

Folder:

```text
labs/02-filter-encrypted-web-traffic/
```

## Lab 03: Find Exposed Login Credentials

In this lab, I analyzed a packet capture file to find login credentials transmitted in clear text.

I used a Wireshark display filter to search packet contents, followed a TCP stream, and documented the exposed username and password.

Main skills practiced:

- Searching packet contents
- Using `tcp contains`
- Following TCP streams
- Identifying clear-text credentials
- Understanding why unencrypted credentials are dangerous

Folder:

```text
labs/03-find-exposed-login-credentials/
```

## Lab 04: Filter DNS Communications

In this lab, I captured DNS traffic using Wireshark.

I used the capture filter:

```wireshark
udp port 53
```

This allowed Wireshark to capture only DNS traffic. I verified that DNS packets were captured and documented the result with screenshots.

Main skills practiced:

- Using capture filters
- Capturing DNS traffic
- Understanding UDP port 53
- Comparing capture filters and display filters
- Reviewing DNS query and response packets

Folder:

```text
labs/04-filter-dns-communications/
```

## Lab 05: Create HTTPS Traffic Detector

In this lab, I created a custom Wireshark coloring rule to highlight HTTPS traffic.

The rule was named:

```text
Secure Web Traffic
```

The filter expression used was:

```wireshark
tcp.port == 443
```

This made HTTPS traffic easier to identify visually in Wireshark.

Main skills practiced:

- Opening Wireshark Coloring Rules
- Creating a custom coloring rule
- Using `tcp.port == 443`
- Highlighting HTTPS traffic
- Exporting Wireshark rules

Folder:

```text
labs/05-create-https-traffic-detector/
```

## Lab 06: Extract Web Traffic Evidence

In this lab, I used Wireshark to find and save web traffic evidence from a packet capture file.

I used the display filter:

```wireshark
tcp contains "labex"
```

Then I followed a TCP stream and saved the stream data as an evidence file.

Main skills practiced:

- Searching TCP packet contents
- Filtering traffic by text
- Following TCP streams
- Saving TCP stream data
- Practicing basic network investigation steps

Folder:

```text
labs/06-extract-web-traffic-evidence/
```

## Lab 07: Uncover Suspicious DNS Queries

In this lab, I used TShark to extract DNS query names from a packet capture file.

I used a Linux command pipeline to filter DNS traffic, extract domain names, sort the results, remove duplicates, and save the final output to a text file.

Main command used:

```bash
cat /home/labex/project/capture.pcapng | tshark -r - -Y "dns" -T fields -e dns.qry.name | sort | uniq > /home/labex/project/domains.txt
```

Main skills practiced:

- Using TShark
- Reading packet captures from the command line
- Extracting DNS query names
- Using Linux pipes
- Sorting output
- Removing duplicates
- Saving command output to a file

Folder:

```text
labs/07-uncover-suspicious-dns-queries/
```

## Key Wireshark Filters Used

| Filter | Purpose |
|---|---|
| `http` | Shows HTTP traffic |
| `tls` | Shows TLS traffic |
| `dns` | Shows DNS traffic |
| `udp port 53` | Capture filter for DNS traffic |
| `tcp.port == 443` | Shows TCP traffic using port 443 |
| `tcp contains "labex"` | Searches TCP packet contents for the text `labex` |
| `tcp contains "&pass"` | Searches TCP packet contents for password-related data |

## Key Commands Used

| Command | Purpose |
|---|---|
| `wireshark` | Opens Wireshark from the terminal |
| `tshark` | Runs Wireshark-style packet analysis from the command line |
| `sort` | Sorts command output alphabetically |
| `uniq` | Removes duplicate lines |
| `cat` | Displays file contents |
| `head` | Shows the first lines of output |
| `nano` | Edits text files in the terminal |
| `git add` | Stages files for Git |
| `git commit` | Saves repository changes locally |
| `git push` | Uploads commits to GitHub |

## Important Concepts Learned

### Packet Capture

A packet capture is a saved record of network packets. It allows analysts to review traffic after it has been captured.

### Capture Filter

A capture filter decides what packets Wireshark records before the capture starts.

Example:

```wireshark
udp port 53
```

### Display Filter

A display filter decides what packets Wireshark shows after traffic has already been captured.

Example:

```wireshark
dns
```

### TCP Stream

A TCP stream is a full conversation between two systems using TCP. Following a TCP stream helps analysts view the communication in a more readable format.

### DNS Analysis

DNS analysis helps identify domain names that systems are trying to contact. Suspicious DNS queries may indicate malware, command-and-control communication, or data exfiltration attempts.

### HTTPS and TLS

HTTPS is secure web traffic. TLS is the encryption protocol commonly used by HTTPS. In Wireshark, HTTPS traffic often appears as TLS traffic.

### TShark

TShark is the command-line version of Wireshark. It is useful for extracting packet data quickly from the terminal.

## Privacy and Security Notes

Some labs use packet capture files. Packet captures can contain sensitive information such as IP addresses, domain names, hostnames, cookies, credentials, or other network details.

For privacy and security reasons:

- I do not include unnecessary original packet capture files in this public repository.
- I include screenshots and documentation for portfolio purposes.
- Any sensitive details in screenshots may be blurred or removed.
- All labs were completed in controlled educational environments or on systems where I had permission.

Packet capture and traffic analysis should only be performed on networks where permission is given. Capturing or inspecting traffic without authorization can be illegal and unethical.

## What I Learned Overall

Through these labs, I learned how Wireshark can be used to inspect network traffic and support basic cybersecurity investigations.

I practiced capturing packets, applying filters, following TCP streams, identifying DNS and HTTPS traffic, creating coloring rules, finding clear-text credentials, and using TShark to extract DNS query names from packet captures.

These labs helped me build practical beginner-level skills in network traffic analysis, packet inspection, and cybersecurity documentation.

## Author

Created by Anastasiia Yurchenko as part of my cybersecurity learning portfolio.
