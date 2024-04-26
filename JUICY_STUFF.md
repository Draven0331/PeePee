
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

     if you are trying to convert DSCP, multiply the number they give you by 4.

     ex)
        DSCP = 24 

          24 * 4 = 96
  
  ## NETCAT - TCP SCAN SCRIPT

    #!/bin/bash
    echo "Enter network address (e.g. 192.168.0): "
    read net
    echo "Enter starting host range (e.g. 1): "
    read start
    echo "Enter ending host range (e.g. 254): "
    read end
    echo "Enter ports space-delimited (e.g. 21-23 80): "
    read ports
    for ((i=$start; $i<=$end; i++))
    do
        nc -nvzw1 $net.$i $ports 2>&1 | grep -E 'succ|open'
    done

## NETCAT - UDP SCAN SCRIPT

    ## #!/bin/bash
    echo "Enter network address (e.g. 192.168.0): "
    read net
    echo "Enter starting host range (e.g. 1): "
    read start
    echo "Enter ending host range (e.g. 254): "
    read end
    echo "Enter ports space-delimited (e.g. 21-23 80): "
    read ports
    for ((i=$start; $i<=$end; i++))
    do
        nc -nvzw1 $net.$i $ports 2>&1 | grep -E 'succ|open'
    done  
    
  ## NETCAT - BANNER GRABBING
Find what is running on a particular port

    nc [Target IP] [Target Port]
    nc 172.16.82.106 22
    nc -u 172.16.82.106 53
          
                -u : To switch to UDP   
 
  ##  NATIVE HOST TOOLS

Show TCP/IP network configuration

    Windows: ipconfig /all
    Linux: ip address (ifconfig depreciated)
    VyOS: show interface

Show DNS configuration

    Windows: ipconfig /displaydns
    Linux: cat /etc/resolv.conf

 Show ARP Cache

    Windows: arp -a
    Linux: ip neighbor (arp -a depreciated)  

    Show network connections

    Windows: netstat
    Linux: ss (netstat depreciated)

    Example options useful for both netstat and ss: -antp
     
      a = Displays all active connections and ports.
      n = No determination of protocol names. Shows 22 not SSH.
      t = Display only TCP connections.
      u = Display only UDP connections.
      p = Shows which processes are using which sockets.   

Services File

      Windows: %SystemRoot%\system32\drivers\etc\services
      Linux/Unix: /etc/services     

OS Information

    Windows: systeminfo
    Linux: uname -a and /etc/os-release  
 Show Running Processes

    Windows: tasklist
    Linux: ps or top

        Example options useful for ps: -elf
        e = Show all running processes
        l = Show long format view
        f = Show full format listing  

 Routing Table

    Windows: route print
    Linux: ip route (netstat -r deprecated)
    VyOS: show ip route

  
File search

    find / -name hint* 2> /dev/null
    find / -iname flag* 2> /dev/null  <---- iname is case sensitive

 
    
  
