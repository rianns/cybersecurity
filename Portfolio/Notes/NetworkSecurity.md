## Checklist

### Part 1: Provide a summary of the problem found in the DNS and ICMP traffic log

The UDP protocol reveals that:

- udp port 53 is unreachable
- all 3 tries were unreachable
- DNS server is down

The is based on the result of the network analysis, which shows that the ICMP echo reply returned the error message:

```
udp port 53 is unreachable
```

The port noted in the error message (port 53) is used for communication between DNS client and server.

The most likely issue is that the DNS server is unable to respond to the DNS request.

### Part 2: Explain your analysis of the data and provide at least one cause of the incident

- The incident occured at 1:24pm (36.09564s).

- The IT team became aware of the incident when several customers contacted the company to report that they are unable to access the company website www.yummyrecipesforme.com, receiving the error "destination port unreachable" after waiting for the page to load.

- The IT department initially attempted to visit the website and received the same error as the reports.

- tcpdump was loaded to analyse the traffic. The analyser shows that when UDP packets were sent, an ICMP response was returned to the hose with the error message "udp port 53 unreachable"

- the DNS server might be down due to a Denial of Service attack or a system failure/error
