### GENERAL

#### Ethernet hand-off/ UNI
We currently support the following port sizes:
* 100M/ 1GE copper
* GE optical
* 10GE optical
* 100GE optical (future)

#### L2 MTU/ Jumbo Frames	
Our standard GDE service supports standard frame sizes as well as jumbo frames of 9000B. We can also support up to 9190B frame sizes upon customer request.

#### Multicast Traffic
Storm control options are disabled for all E-line services; hence, multicast frames will fully pass through our network without any rate limits.

For E-LAN and E-Tree services, we implement storm control to prevent BUM (Broadcast, Unknown Unicast and Multicast) traffic from unnecessarily flooding the network.  However, we can disable storm control for Multicast in E-Tree services if requested to support CATV customers.

#### Protection Mechanisms	
We use a combination of LAG and ring (ERP and/or MST-AG) protection mechanisms to achieve fast switching times of ~50ms + propagation delay. Switching occurs when an active link has any of the following:
* Alarms (LOS, LOF, LOP, AIS, RDI)
* SF due to BER of 10e-6
* Loss of 3x 802.1ag/ Y.1731 CFM frames (sent every 3.3ms)

#### LOLA latency between Singapore and Mumbai
As per the LOLA latency, Least measured RTD we can offer for this request is 49.59ms.
* Measured RTD = 48.88ms TIC + GAIL ( IM6 <> SVW ) + 0.71ms Starhub ( SVW <> SGX ).
* SLA RTD = 55.00ms TIC + GAIL ( IM6 <> SVW ) + 1.00ms Starhub (SVW <> SGX)
<br><br>

### MANAGED ETHERNET
Placeholder for general questions on Managed Ethernet.

#### Link Loss Forwarding (LLF)
Link loss forwarding (LLF) is supported by deploying Network Interface Devices (NID) at the customer premises. When a network failure is detected, the NIDs will shut down the access ports facing the CPE.

#### Customer access to NIDs
No, the end-user/ customer won't be able to communicate with our NIDs since they are in a separate management VLAN and private IP address space visible only to our OSS.

#### CFM level for service end to end monitoring
Per MEF recommendations, customers/ subscribers can use CFM MD Level 6 or 7 for end-to-end service monitoring.
<br><br>

### SECURITY
Placeholder for general questions on security for our Ethernet services.

#### MACsec Encryption
MACsec is currently not offered for GDE. However, the customer can run MACsec or IPsec on their network that we will transparently carry over our L2 network. Our GDE service is compliant to EPL option 2, which tunnels (no peering) most L2CP BPDUs.

#### EPL L2CP Disposition, Transparency or Tunnelling
Our EPL service complies with the L2CP handing requirements for EPL Option 2 per Table K of MEF 6.1.1; hence, transparently tunnels MACsec, EAPoL and LLDP frames.

#### General Data Protection Regulation (GDPR)/ Customer Data
Our GDE service offers transparent transport of customer data. We do not peer nor participate in any higher layer protocols that the customer runs on their network. We look at the Ethernet header only of the incoming frames to make forwarding decisions but never the customer data. However, it is possible for malicious parties to snoop/ intercept customer data that is in the clear when they are not using authentication/ encryption protocols such as IPsec.
