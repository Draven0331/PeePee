## Networking Access

## OSI Model 

-APPLICATION : provides a network interface to the software applications that communicate over the network. It supports communication services directly to end-users or applications and provides network services such as file transfers, email, and remote login.
        
       *** Protocols that operate at this layer***

        -Remote Login: SSH (Secure Shell) and Telnet

        -Web: HTTP (Hypertext Transfer Protocol) and HTTPs

        -File Transfer: FTP (File Transfer Protocol), SFTP (SSH FTP), and FTPS (FTP Secure)
    
        -Email: SMTP (Simple Mail Transfer Protocol), POP (Post Office Protocol), and IMAP (Internet Message Access           Protocol)

  -PRESENTATION : deals with the syntax and semantics of the information exchanged between systems. It translates data between the application layer and the lower layers, ensuring that the data is in a readable format. Tasks include data compression, encryption, and character set conversions. There are no protocols that operate at this layer. This layer deal more with encoding and file formatting.

-SESSION: establishes, manages, and terminates communication sessions between applications. It controls dialogues (full-duplex or half-duplex), maintains synchronization, and manages data exchange between applications. Sometimes the protocols that operate at this layer act as a "shim protocol" between various communicating devices.

    **Protocols that operate at this layer:**

    -NetBIOS (Network Basic Input/Output System)

    -RPC (Remote Procedure Call)

    -PPTP (Point-to-Point Tunneling Protocol)

    -SMB (Server Message Block) can operate like a "shim protocol" between various communicating devices.

    -SOCKS (Socket Secure)
    
TRANSPORT: ensures end-to-end communication, providing error detection, error correction, and flow control. It breaks down larger messages into smaller segments, sends them across the network, and reassembles them at the destination.

      **Protocols that operate at this layer:**

    -Transmission Control Protocol (TCP): TCP is a connection-oriented protocol that provides reliable and ordered delivery of data packets. It establishes a virtual connection between the sender and receiver, manages packet acknowledgment, retransmission, and flow control to ensure data integrity and delivery. TCP is widely used for applications that require error-free data transmission, such as web browsing, email, and file transfer.

    -User Datagram Protocol (UDP): UDP is a connectionless protocol that provides fast, but unreliable, delivery of data packets. Unlike TCP, UDP does not establish a connection or guarantee packet delivery, making it faster but less reliable. It is commonly used for real-time communication applications like video streaming, online gaming, and Voice over IP (VoIP), where occasional packet loss is acceptable.

NETWORK: is responsible for logical addressing, routing, and forwarding. It enables devices to communicate across different networks by determining the best path for data to travel from the source to the destination. IP (Internet Protocol) and IPv6 operates at this layer.

    **Protocols that operate at this layer:**

      -Internet Protocol version 4 (IPv4)
      -Internet Protocol version 6 (IPv6)
      -internet Control Message Protocol (ICMP)
      -Internet Group Management Protocol (IGMP)
      -Neighbor Discovery Protocol (NDP)
      -Open Shortest Path First (OSPF)
      -Routing Information Protocol (RIP)

DATA LINK: is responsible for creating a reliable link between two directly connected nodes. It handles issues such as framing, addressing, and error detection. It also manages access to the physical medium and controls how data is placed on the medium. 


    **Protocols that operate at this layer:**
     
      -Ethernet: 
      -IEEE 802.11 (Wi-Fi)
      -Ethernet VLAN Tagging (IEEE 802.1Q)
      -Address Resolution Protocol (ARP):
      -Reverse Address Resolution Protocol (RARP):
      -Link Layer Discovery Protocol (LLDP)

     
PHYSICAL : deals with the physical connection between devices. It defines the hardware elements, such as cables, connectors, and the transmission medium (e.g., copper wires, fiber optics). It is concerned with the raw transmission of bits over a physical medium. The protocols define the electrical, mechanical, and functional specifications for transmitting raw bit streams over physical mediums.

  

    **Protocols that operate at this layer:**


    -Ethernet Physical Layer Standards (IEEE 802.3)
    -IEEE 802.11
    -Bluetooth 

##  Network Devices

        -Hubs
        -Repeaters
        -Swithches
        -Routers

## Ethernet Timing

        
        Speed	        Bit-time
        
        10 Mbps           100ns

        100 Mbps          10ns
        
        1 Gbps            1ns

        10 Gbps           .1ns

        100 Gbps          .01ns


## Switch Operation

There are (3) Switching modes

        -cut-through mode = only examines the destination address before forwarding it to its destination segment. This is the fastest switching mode but requires the interfaces to be the same speed.
        
        -fragrmet-free mode = read at least 64 bytes of the Ethernet frame before switching it to avoid forwarding Ethernet runt frames (Ethernet frames smaller than 64 bytes). A frame should have a minimum of 46 bytes of payload plus its 18-byte frame header.
        
        -store and forward mode = accepts and analyzes the entire frame before forwarding it to its destination. It takes more time to examine the entire frame, but it allows the switch to catch certain frame errors and collisions and keep them from propagating bad frames through the network. 


## CAM Table Overflow/Media Access Control (MAC) Attack

        -sends frames with FAKE source MAC address to the switch

        -causes the switch to fill table with FAKE addresses

        -the switch will not be able to learn valid MAC addresses

## Describe MAC addressing 

        length: 48-bit | 6 byte | 12 HEX
        Format :
        Windows : 11-22-33-44-55-66  (dashed are windows)
        Linux: 12:34:56:78:91:22 (collon are linux)
        Cisco : 1234.1245.4567 (. are Cisco )

## MAC address types 

        -unicast: one to one 
                -8th bit is off
        -multicast: one to many
                -8th bit is on 
        Broadcast: one to all 
                -All bits on
## MAC spoofing 
        -could not be changed at first
        - used to be called 
                -Hardware 
                -firmware
                -burned in

## VLAN types   

        -Default-VLAN 1
        -Data - User Traffic
        -Voice - VOIP Traffic
        -Management- Switch and router management 
        -Native - Untagged swith with router traffic
        -802.Q is in the VLAN header

## ARP Types 
        
        1 = request
        2 = reply
        
        ARP (0 OP 1 and 2)
        RARP (OP 3 and 4)
        Proxy ARPO (OP 2)
        Gratuitous ARP (OP 2)

## ARP Cache

        - all resolved MAC to IP resolutions
        - If MAC is not in csche the ARP is used
        -dynamic entries last from 2-20 min

## MITM with ARP

        -poison ARP cache with : 
                -Gratuitous ARP
                -Proxy ARP
        -SCAPY example code 
    
## VLAN Trunking Protocol (VTP)

        - it is cisco proprietary 
        - it has (3) modes:
                -server
                -client
                -transparent
                        -NO VLAN traffic just gets passed through 
        -Vulnerabilities:
                -can cause switches to dump all VLAN information
                -Can cause a DOS as the switch will not support configured VLANS
## dynamic trunking protocol (DTP)

        - is a Cisco proprietary Layer 2 protocol
        -  it dynamically negotiate trunking on a link between two switches running                 VLANS
        -
        
