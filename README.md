# Testing Snort Rules
Brian Busco, Ethan Thach, Kaden Makechnie-Hardy, Justin Mott, Quincy Taylor

## Outline
Snort is an open source tool for intrusion detection and intrusion prevention. Snort rules can inspect and analyze real time traffic. Our project's example rule detects packets with a SQL injection payload.

## Files

### rules.sqli
This is the Snort rule we are working with. The rule catches a packet with any source and any destination that contains a single quote in the payload. This might be a SQL injection attempt.
  alert tcp any any -> any 80 (msg: "Form Based SQL Injection Detected"; content: "%27" ; sid:1000003; )
  
### .pcap

This is the packet we designed. It contains a single quote in the payload.
