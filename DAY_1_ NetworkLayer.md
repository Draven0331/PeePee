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
        
        - evil twin = 
        
        - DHCP starvation = When a malicious user has to compete with the legitimate               DHCP server for address assignments, the attacker can flood the DHCP server              with several bogus DHCP requests
        
