## traffic Capture 
## commands 

    -- sudo tcpdump -i eth0 = this pulles a tcpdump from a specified interface
    
    -- sudo tcpdump -r BPFCheck.pcap = this gets a tcpdump from a pcap
   
    -- sudo tcpdump -i eth0 -w practice.pcap = this pulles a tcpdump from a specified interface, and writes it 
                                               to a pcap
   
    -- sudo tcpdump -r BPFCheck.pcap "udp portrange 1-1023" = will only display UDP ports specified
    
    -- sudo tcpdump -r BPFCheck.pcap -vn "udp portrange 1-1023" = will verbosly unset name resolution
    
    --sudo tcpdump -r BPFCheck.pcap "udp portrange 1-1023 && ip src 10.0.2.15"

## TCPDUMP PRIMITIVES 

    User friendly capture expressions

      -src or dst
      -host or net
      -tcp or udp

 ## TCPDUMP PRIMITIVE QUALIFIERS
    **type - the 'kind of thing' that the id name or number refers to

          -host, net, port, or portrange

    **dir - transfer direction to and/or from

          -src or dst

    **proto - restricts the match to a particular protocol(s)

          -ether, arp, ip, ip6, icmp, tcp, or udp


## SOCKET TYPES

    **User Space Sockets

          -Stream socket - TCP
          -Datagram socket - UDP

    **Kernel Space Sockets

          -RAW Sockets = any socket where the kernal manipulates the NIC in any way, requres elevated privileges

## CAPTURE LIBRARY

      Requires root for:

            -Promicious Mode (Listen on all NICs)

            -All captured packets are created as RAW Sockets



## BASIC TCPDUMP OPTIONS
      
      -A = print payload in ASCII

      -D = list interfaces

      -i = specify capture interface

      -e = print data-link headers

      -X or XX = print payload in HEX and ASCII

## BASIC TCPDUMP OPTIONS

    -w = write to pcap

    -r = read from pcap

    -v, vv, or vvv = verbosity

    -n = no inverse lookups

## LOGICAL OPERATORS

    Primitives may be combined using:

      -  Concatenation: 'and' ( && )

      - Alteration: 'or' ( || )

      -  Negation: 'not' ( ! )   
    
      -  < or < =

      - > or >=

      - = or !=
