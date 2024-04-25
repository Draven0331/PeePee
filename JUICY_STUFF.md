
## DAY 1 (Network Access)

 ## Protocol data unit (PDU)

    session -> application = data
    Transport = segment/datagram
    Network = Packet
    Data-link = frame
    physical= bi

## Day 1 (Network Layer)

 ## IPV4 Fragmentation
     - breakes up packets from  higher MTU to lower MTU network
     - performed by routers
     - MF flg is on from 1st until 2nd to last
     - Offser is on from the 2nd until the last
     - offset = (MTU -(IHLx4))/8

 ## DSCP CONVERSION

     if you are trying to figutrr out DSCP, multiply the number thry give you by 4
