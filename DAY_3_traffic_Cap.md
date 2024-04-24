## traffic Capture 
## commands 

    -- sudo tcpdump -i eth0 = this pulles a tcpdump from a specified interface
    
    -- sudo tcpdump -r BPFCheck.pcap = this gets a tcpdump from a pcap
   
    -- sudo tcpdump -i eth0 -w practice.pcap = this pulles a tcpdump from a specified interface, and writes it 
                                               to a pcap
   
    -- sudo tcpdump -r BPFCheck.pcap "udp portrange 1-1023" = will only display UDP ports specified
    
    -- sudo tcpdump -r BPFCheck.pcap -vn "udp portrange 1-1023" = will verbosly unset name resolution
    
    --sudo tcpdump -r BPFCheck.pcap "udp portrange 1-1023 && ip src 10.0.2.15"

    -- sudo tcpdump -r BPFCheck.pcap "udp portrange 1-1023 && (tcp port 21 || udp port 69)"
    
    -- tcpdump -i eth0 'ether[12:2] = 0x0806'

    -- tcpdump -i eth1 'ip[9] = 0x06'
    
    -- tcpdump -i eth0 'tcp[0:2] = 53 || tcp[2:2] = 53'
    
    -- tcpdump 'ether[12:2] = 0x0800 && (tcp[2:2] != 22 || tcp[2:2] != 23)'
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
## BERKLEY PACKET FILTER (BPF)

        -Similar in function to primitives
        -Reduces redudant computations
        -More complex expressions

syntax:
            
            tcpdump {A} [B:C] {D} {E} {F} {G}

        A = Protocol (ether | arp | ip | ip6 | icmp | tcp | udp)
        B = Header Byte offset
        C = optional: Byte Length. Can be 1, 2 or 4 (default 1)
        D = optional: Bitwise mask ( & )
        E = Operator ( = | == | > | < | <= | >= | != | () | << | >> )
        F = Result of Expression
        G = optional: Logical Operator ( && || ) to bridge expressions
BPF EXAMPLES

    tcpdump -i eth0 'ether[12:2] = 0x0806'
    tcpdump -i eth1 'ip[9] = 0x06'
    tcpdump -i eth0 'tcp[0:2] = 53 || tcp[2:2] = 53'
    tcpdump 'ether[12:2] = 0x0800 && (tcp[2:2] != 22 || tcp[2:2] != 23)'

BITWISE MASKING

    - BPFs can read 1 (byte), 2 (half-word) or 4 (word)

    - BPFs alone will only filter to the byte level

    - Bit-wise masking allow filtering precision to the bit level

    - Binary (0) to ignore bit

    - Binary (1) to match bit

BITWISE MASKING EXAMPLES

    tcpdump 'ether[12:4] & 0xffff0fff = 0x81000abc'
            - f = BIT TIRNED ON/NEEDS TO MATCH
            - 0 = BIT TURNED OFF/ DOESNT NEED TO MATCH 
            - LOOKS FOR 81000abc
            
    tcpdump 'ip[1] & 252 = 32'
            - 252 is the decimal of 0xffffff00
            - looks at the IP header length and only shows the position of where 32 is in the 0xff_fff00.

    tcpdump 'ip[6] & 224 != 0'
    
    tcpdump 'tcp[13] 0x11 = 0x11'
    
    tcpdump 'tcp[12] & 0xf0 > 0x50'

    
