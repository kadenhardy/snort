# Testing Snort Rules
Brian Busco, Ethan Thach, Kaden Makechnie-Hardy, Justin Mott, Quincy Taylor

## Outline
Snort is an open source tool for intrusion detection and intrusion prevention. Snort rules can inspect and analyze real time traffic. Our project's example rule detects packets with a SQL injection payload.

## Files

### rules.sqli
The Snort rule catches a packet with any source and any destination that contains a single quote in the payload. Snort flags this as a possible SQL injection attempt.
```
alert tcp any any -> any 80 (msg: "Form Based SQL Injection Detected"; content: "%27" ; sid:1000003; )
```
### .pcap

This packet's payload contains a single quote, which triggers the Snort rule above.


## How to Apply the Rule

STEP 1: Download Snort version 2.9.7 for your client [Snort Downloads](https://www.snort.org/downloads#snort-downloads).

STEP 2: Download Scapy (https://scapy.net/) or use `$ pip install --pre scapy[basic]` to download it in your Linux Subsystem (https://scapy.readthedocs.io/en/latest/installation.html).

STEP 3: Add the rule to a text file. `alert tcp any any -> any 80 (msg: "Form Based SQL Injection Detected"; content: "%27" ; sid:1000003; )`

STEP 4: Open Scapy and implement the command as seen below. Run `injection=IP(src="[IP address of source]")/TCP(dport=80)/"%27"` in Scapy to build the packet capture file. Next run the command `wrpcap("injection.pcap", injection)`. Then, `exit` scapy.

STEP 5: Run `snort -r injection.pcap -K none -A console -q -c sqli.rules`

![Command Screenshots](snort.PNG)
