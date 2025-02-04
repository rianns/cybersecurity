# Cybersecurity Incident Report: Network Traffic Analysis

## Part 1: Provide a summary of the problem found in the DNS and ICMP traffic log

The UDP protocol reveals that the DNS server is unreachable. This is based ont he result of the network analysis, which shows that the ICMP returned the error message "udp port 53 unreachable". The port noted in the error message (port 53) is used for communication between DNS client and server. The most likely issue is that the DNS server is unable to respond to the DNS request.

## Part 2: Explain your analysis of the data and provide at least one cause of the incident

The incident occured at 1:24pm. The IT team became aware of the incident when several customers contacted to company to report that they are unable to access the website "www.yummyrecipesforme.com", receiving the error "destination port unreachable". Network security professionals are currently investigating the incident. In our investigation, we conducted packet sniffing tests using tcpdump which shows that when UDP packets were sent, an ICMP response was returned to the hose with the error message "udp port 53 unreachable". The DNS server might be down due to a Denial of Service attack or a system failure/error.
