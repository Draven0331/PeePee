## Transport to Application layer 

TCP

       1.connection oriented
       2.segments
       3.unicast traffic
       4.connection termination
              -4-way termintion
              -reset connection
UDP
      
       connection-less
       datagrams
       broadcast, multicast, or unicast traffic
       
Ports 

       0-1023 = Well known
       1024-49151 = Registered
       49152-35535 = Dynamic

## Analyze TCP and UDP headers

       great example of headers are in 3.1.4.1 and 3.1.4.2 of the FG. 

## TCP Options

       0 - End of Options
       1 - No Options (NOP)
       2 - Max segment size (MSS)
       3 - TCP Windows Scaling 
       4 - Selective ACK (SACK) permitted
       5 - SACK
       8 - TCP timestamps

## IPSEC

       Modes:Tranport or tunnel
       Headers:
              -ESP = (Protocol 50)
              -AH = (protocol number 51)
              -IKE = ()
## SOCKS 4 & 5

SOCKS 4

              -NO authentication
              -only IPV4
              -No UDP support
              -No proxy binding 
SOCKS 5

              -Various methods of authentication
              -IPV4 and IPV6 support
              -UDP support

## Network basic input output system (NETBIOS)

       -TCP 139 and UDP 137/138
       -Name Resolution (15 Characters)
       -Largely replaces DNS
SMB
       
       -rides over NETBIOS
       -Netbios Dgram service - UDP 138
       -Netbios Session Service - TCP 139
       -SAMBA and CIFS are just flavors of SMB

RPC (ANY PORT)

       -Allows a program to execute a request on a local/remote computer

       -Hides network complexities

       -XML, JSON, SOAP, and gRPC

       - Framework of rules and protocols for software components to interact.

       -Methods, parameters, and data formats for requests and responses.

       - REST and SOAP
       
       User application will:

              -Request for information from external server

              -Receives the information from the external server

              -Display collected data to User

## OSI LAYER 6 FUNCTIONS AND RESPONSIBILITIES

       **RESPONSIBILITIES**
              
              -Translation
              -Formating
              -Encoding (ASCII, EBCDIC, HEX, BASE64)
              -Encryption (Symmetric or Asymmetric)
              -Compression

## OSI LAYER 7 PROTOCOLS AND HEADERS

 TELNET (TCP 23)
             
              - remote login
              - authentication
              - clear text
SSH (TCP 22)
             
              **Messages provide**
              -Client/server authentication
              -Asymmetric or PKI for key exchange
              -Symmetric for session
              -User authentication
              -Data stream channeling

 HTTP(S) (TCP 80/443)

              -User Request methods

                     GET / HEAD / POST / PUT

              -Server response Codes

                     100, 200, 300, 400, 500
             
              -HTTP(S) VULNERABILITIES
                     
                     -Flooding
                     -Applification
                     -Low and slow
                     -Drive-By Downloads
                     -BeEF Framework

DNS (TCP/UDP 53)
       
              - DNS QUERY/RESPONSE
              - Resolves Names to IP addresses

             - Queries and responses use UDP

             - DNS response larger than 512 bytes use TCP
                    - DNS Zone Transfer
                    - DNS Security
              -DNS RECORDS
                     -A - IPv4 record
                     -AAAA - IPv6 record
                     -MX - Mail Server record
                     -TXT - Human-readable text
                     -NS - Name Server record
                     -SOA - Start of Authority
FTP(TCP 20/21)       
             
              -RFC 959
              -Port 21 open for Control
              -Port 20 only open during data transfer
              -Authentication or Anonymous
              -Clear Tex
              -Modes: (2)
                           - Active (default)
                           - Passive
              ACTIVE ISSUES
                     -NAT and Firewall traversal issues
                     -Complications with tunneling through SSH
                     -Passive FTP solves issues related to Active mode and is most often used in modern systems




## SSH ARCHITECTURE

              Client / Server / Session

              Keys:

                     User Key - Asymmetric public key used to identify the user to the server

                     Host Key - Asymmetric public key used to identify the server to the user

                     Session Key - Symmetric key created by the client and server to protect the session’s                                                  communication.


## SSH KEY CHANGE FIX

      - Copy/Paste the ssh-geygen message to remove the Host key from the known_hosts file

     ***  ssh-keygen -f "/home/student/.ssh/known_hosts" -R "172.16.82.106"   ***

      - When you re-connect it will prompt you to save the new Host key




