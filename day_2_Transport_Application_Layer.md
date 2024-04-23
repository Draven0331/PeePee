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
