  ## Service and Network Discovery

 ## RECONNAISSANCE STAGES
      -Passive External
      -Active External
      -Passive Internal
      -Active Internal

## RECONNAISSANCE STEPS
    -Network Footprinting
            
        --Collect information relating to target

                  -Network
                  -Systems
                  -Organizationcanning
       
        --Network Enumeration
                  -Network Resource and shares
                  -users and Groups
                  -Routing tables
                  -Auditing and Service settings
                  -Machine names
                  -Applications and banners
                  -SNMP and DNS details
                  -Other common services and port
    
    -Vulnerability Assessment

## IDENTIFYING CONTENT OF INTEREST
      -/etc/passwd and /etc/shadow or SAM database
      -Configuration files
      -Log files
      -Backup files
      -Test pages
      -Client-side code      

## DIG VS WHOIS
Whois - queries DNS registrar over TCP port 43

      -Information about the owner who registered the domain
      -whois <websitr.com>
      
      (EX.)
         
         whois zonetransfer.me
Dig - queries DNS server over UDP port 53

      -Name to IP records
      -  dig <whateverwebsite.com> <server>
         
         (EX.)
         
         dig zonetransfer.me A
         dig zonetransfer.me AAAA
         dig zonetransfer.me MX
         dig zonetransfer.me TXT
         dig zonetransfer.me NS
         dig zonetransfer.me SOA

    -ZONE TRANSFER
          --Between Primary and Secondary DNS over TCP port 53
          -- dir axfr <@soa.server> <target-site>
          
          (EX.)

              dig axfr @nsztm1.digi.ninja zonetransfer.me

## PASSIVE OS FINGERPRINTER (P0F)

p0f: Passive scanning of network traffic and packet captures.

    (EX.)
    
      more /etc/p0f/p0f.fp
      sudo p0f -i eth0
      sudo p0f -r test.pcap

 ## NMAP - scanning 
      
      -Broadcast Ping/Ping sweep (-sP, -PE)
    **-SYN scan (-sS)
    **-Full connect scan (-sT)
      -Null scan (-sN)
      -FIN scan (-sF)
      -XMAS tree scan (-sX)
    **-UDP scan (-sU)
    **-Idle scan (-sI)  (aka zombie)

      -ACK/Window scan (-sA)
      -RPC scan (-sR)
      -FTP scan (-b)
      -Decoy scan (-D)
      -OS fingerprinting scan (-O)
      -Version scan (-sV)
      -Protocol ping (-PO)
      
  ## NMAP - OTHER OPTIONS

      -PE - ICMP Ping
    **-Pn - No Ping
    
          Discovery probes (-PE, -PP, -PM)

## NMAP - TIME-OUT
    
        -T0 - Paranoid - 300 Sec
        -T1 - Sneaky - 15 Sec
        -T2 - Polite - 1 Sec
        -T3 - Normal - 1 Sec
      **-T4 - Aggresive - 500 ms
        -T5 - Insane - 250 ms

# Netcat- Scanning 

   syntax: nc [Options] [Target IP] [Target Port(s)]
    
    -z : Port scanning mode i.e. zero I/O mode

    -v : Be verbose [use twice -vv to be more verbose]

    -n : do not resolve ip addresses

    -w1 : Set time out value to 1
  
    -u : To switch to UDP

    (EX.)
      
      nc -zvn -w1 172.16.82.106 21-23


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

##   CURL AND WGET
    
    -Both can be used to interact with the HTTP, HTTPS and FTP protocols.

    ** -Curl - Displays ASCII
    
    (EX.)
    
      curl http://172.16.82.106
      curl ftp://172.16.82.106
    
  
    ** -Wget - Downloads (-r recursive)

    (EX.)
    
          wget -r http://172.16.82.106
          wget -r ftp://172.16.82.106
          wget -r ftp://172.16.82.106:80         <----- you can add ports to the end

 ## Connecting to an FTP server

    syntax : ftp <IP>

    commands : 
    
    passive = will put it in passive mode, you have to be in this mode to use 'get' command.
    get = will take that file and put it in your home directory, must be in passive mode 
    ls - list directory 
    cd - change directory
    
    
    
      
