## Network Security: Analyse network layer communication

[x] Part 1: Provide a summary of the problem found in the DNS and ICMP traffic log

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

[x] Part 2: Explain your analysis of the data and provide at least one cause of the incident

- The incident occured at 1:24pm (36.09564s).

- The IT team became aware of the incident when several customers contacted the company to report that they are unable to access the company website www.yummyrecipesforme.com, receiving the error "destination port unreachable" after waiting for the page to load.

- The IT department initially attempted to visit the website and received the same error as the reports.

- tcpdump was loaded to analyse the traffic. The analyser shows that when UDP packets were sent, an ICMP response was returned to the hose with the error message "udp port 53 unreachable"

- the DNS server might be down due to a Denial of Service attack or a system failure/error

## Network Security: Analyse network attacks

[] Section 1: Identify the types of attack that may have caused this network interruption

One potential explanation for the website's connection timeout error message is the server being overwhelmed and unable to function correctly. The logs show that there is a large number of TCP SYN requests coming from an unfamiliar IP address. This event could be a SYN flood attack.

[] Section 2: Explain how the attack is causing the website to malfunction

When website visitors try to establish a connection with the web server, a three-way
handshake occurs using the TCP protocol. Explain the three steps of the handshake:

1. The device sends a synchronised request to the server
2. The server responds with a SYN/ACK packet to acknowledge the receipt of the device's request and leaves a port open for next step
3. Once the server receives the final ACK packet from the device, a TCP connection is established

Explain what happens when a malicious actor sends a large number of SYN packets all at
once:

- If the number of SYN requests is larger than the number of available ports on the server, the server will be overwhelmed and unable to function

Explain what the logs indicate and how that affects the server:

- The logs indicate that there is a large number of TCP SYN requests coming from an unfamiliar IP address. The large number of requests has caused the server to be overwhelmed and unable to function correctly causing the website's connection timeout error message.

Notes:

### Step 3

What do you currently understand about network attacks?

- Networks are always susceptible to attacks from malicious actors. There a few different attacks suhc as Denial of Service (DoS) attacks, Distributed Denial of Service (DDoS) attacks, On-path attacks, SYN flood attacks, an IP Spoofing, to name a few.

Which type of attack would likely result in the symptoms described in the scenario?

- In this scenario, the attack is likely due to a SYN flood attack. An unfamiliar IP address has been detected sending a large number of TCP SYN requests to the website's server, eventually overwhelming the server causing it to return a connection timeout error message to all following requests after all the available ports on the server has been exhausted.

What is the difference between a denial of service (DoS) and distributed denial of service (DDoS)?

- A Denial of Service (DoS) attack targets a network server and floods it with network traffic by sending so much information that the server crashes causing the business to conduct their normal operations. A Distributed Denial of Service (DDoS) attack is a kind of DoS attack that makes use of multiple devices or servers in different locations to flood the target network with unwanted traffic. Use of numerous devices makes it more likely that the total amount of traffic sent will overwhelm the target server.

Why is the website taking a long time to load and reporting a connection timeout error?

- The website will continue to work as intended while there are still available ports in the server. While there are still ports available to do the three-step handshake to establish a TCP connection between device and a server, the website will continue working as intended. As it progresses, the server will be unable to keep up with the overwhelmingly large amount of requests its getting, at this time, it will then report a connection timeout error.

### Step 4

Describe the attack. What are the main symptoms or characteristics of this specific type of attack?

- The large number of SYN requests coming in to the server.
- ACK responses unable to keep up with the requests

Explain how it affected the organization’s network. How does this specific network attack affect the website and how it functions?

- The website is able to accept requests from both visitor and employee alike. The server continues accepting requests from either sources until it no longer is able to accept any more causing the connection timeout error.

Describe the potential consequences of this attack and how it negatively affects the organization.

- The server treated the the SYN flood attack as normal visitor traffic, however as it time went on and it became more overwhelming, legitimate employee requests are failing the handshake as the server is no longer able to keep up with the flooded SYN requests

Optional: Suggest potential ways to secure the network so this attack can be prevented in the future.

- Have a separate route for visitor requests and a more secure employee server.
- Stricter visitor access

## Network Security: Apply OS hardening techniques
