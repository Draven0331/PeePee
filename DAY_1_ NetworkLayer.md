## Network Layer 
    - addressing scheme for network (logical addressing)
    - routing 
    - Encapsulation
    - IP fragmentation and reassembly
    - error handling and diagnostics

## describe classfull IPV4 addressing and subnetting 

    -Class A (0 to 127)
    -Class B (128 to 191)
    -Class C (192 to 223)
    -Class D (224 to 239) Multicast
    -Class E (240 to 255)
    
## IPV4 Address scopes

    - public
    - private (RFC 1918)
    - Loopback (127.0.0.0/8)
    - Link Local (APIPA) -> 169.254.0.0/16
    - multicast (class D)

## IPV4 Fragmentation
     - breakes up packets from  higher MTU to lower MTU network
     - performed by routers
     - MF flg is on from 1st until 2nd to last
     - Offser is on from the 2nd until the last
     - offset = (MTU -(IHLx4))/8

## IPV4 Auto Configuration Vulnerabiility 

        - rouge DHCP = A malicious person can setup a Rougue DHCP server to assign                   addresses for a particular network. In these configurations the attacker can             assign whatever they want for the Gateway, DNS suffix and DNS server                     addresses
        
        - evil twin = cant find info on FG probably didnt need to type this..
    
        
        - DHCP starvation = When a malicious user has to compete with the legitimate               DHCP server for address assignments, the attacker can flood the DHCP server              with several bogus DHCP requests


## ICMPV4 Traceroute

        - Identifies hops between the source and the destination
        - usues incrementing TTLs
        - Hops return an ICMP Type 11 Time exceeded message when TTL reaches Zero
        - continues until it reaches target or 30 hops
    
## ICMPV4 Attacks 

        - firewalking 
        - oversized ICMP messages 
        - ICMP redirects
        - SMURF attack
        - Map networrk w/ IP unrechables 
        - ICMP Covert Channels 

## IPV6 Neighbor Discovery Protocol (NDP)

    - Router solicitation = type 133
    - router advertisement = Type 134
    - neighbor solicitation = Type 135
    - neighbor advertisement = Type 136
    - redirect = Type 137

# Administrative Disance 
helps the router determine the best route to take

    connected =    0
    static =       1
    external BGP = 20
    EIGRP =        90
    OSPF =         110
    IS-IS =        115
    RIP =          120


    
    

