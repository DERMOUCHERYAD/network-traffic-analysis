 # Network Traffic Analysis

## Overview
Analyze DNS and ICMP traffic using tcpdump to diagnose a network protocol issue affecting website access.

## Scenario
- Clients report errors accessing `www.yummyrecipesforme.com` with the message "destination port unreachable."
- Analysis shows UDP requests to DNS server return ICMP error: "udp port 53 unreachable."

## Tcpdump Logs
-Capturing data packets using a network analyzer tool:'Tcpdump'
- The first two lines of the log file show the initial outgoing request from your computer to the DNS server requesting the IP address of yummyrecipesforme.com. This request is sent in a UDP packet.
- The third and fourth lines of the log show the response to your UDP packet. In this case, the ICMP 203.0.113.2 line is the start of the error message indicating that the UDP packet was undeliverable to port 53 of the DNS server.
- In front of each request and response, you find timestamps that indicate when the incident happened. In the log, this is the first sequence of numbers displayed: 13:24:32.192571. This means the time is 1:24 p.m., 32.192571 seconds.
- After the timestamps, you will find the source and destination IP addresses. In the first line, where the UDP packet travels from your browser to the DNS server, this information is displayed as: 192.51.100.15 > 203.0.113.2.domain. The IP address to the left of the greater than (>) symbol is the source address, which in this example is your computer’s IP address. The IP address to the right of the greater than (>) symbol is the destination IP address. In this case, it is the IP address for the DNS server: 203.0.113.2.domain. For the ICMP error response, the source address is 203.0.113.2 and the destination is your computer's IP address 192.51.100.15.
- After the source and destination IP addresses, there can be a number of additional details like the protocol, port number of the source, and flags. In the first line of the error log, the query identification number appears as: 35084. The plus sign after the query identification number indicates there are flags associated with the UDP message. The "A?" indicates a flag associated with the DNS request for an A record, where an A record maps a domain name to an IP address. The third line displays the protocol of the response message to the browser: "ICMP," which is followed by an ICMP error message.
- The error message, "udp port 53 unreachable" is mentioned in the last line. Port 53 is a port for DNS service. The word "unreachable" in the message indicates the UDP message requesting an IP address for the domain "www.yummyrecipesforme.com" did not go through to the DNS server because no service was listening on the receiving DNS port.
- The remaining lines in the log indicate that ICMP packets were sent two more times, but the same delivery error was received both times.

![Tcpdump Logs](https://github.com/DERMOUCHERYAD/network-traffic-analysis/blob/main/image.png)

## Files
- `Cybersecurity incident report network traffic analysis DERMOUCHE.pdf`
- `The Exemplar Explained - Cybersecurity Incident Report_ Network Traffic Analysis.pdf`
- `image.png`
