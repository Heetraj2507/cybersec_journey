# Wireshark Lab 9– Analyze a Complete Web Visit

## Objective

In this lab, you will analyze a complete web visit from start to finish using Wireshark. Based on the concepts we have learned so far, you will identify and analyze the different protocols and network activities that occur when a webpage is loaded.

**You will examine the following:**

1. ARP (if required)
2. DNS Query
3. DNS Response
4. TCP Three-Way Handshake
5. TLS Handshake
6. HTTPS Request
7. Data Transfer
8. TCP Connection Close (FIN/ACK)

The goal of this lab is to understand how different networking protocols work together when you open a website. You will use Wireshark display filters to identify each stage and create a timeline showing the complete communication between your computer and the web server.

---

## Useful Display Filters Cheat Sheet

| Purpose | Wireshark Display Filter |
|---|---|
| DNS | `dns` |
| TCP | `tcp` |
| UDP | `udp` |
| HTTP | `http` |
| HTTPS/TLS | `tls` |
| Ping/ICMP | `icmp` |
| ARP | `arp` |
| Your laptop | `ip.addr == YOUR_IP` |
| Port 80 | `tcp.port == 80` |
| Port 443 | `tcp.port == 443` |
| Retransmissions | `tcp.analysis.retransmission` |
| TCP Resets | `tcp.flags.reset == 1` |

---
