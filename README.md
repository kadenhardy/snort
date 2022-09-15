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
