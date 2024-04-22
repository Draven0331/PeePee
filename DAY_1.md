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




    


