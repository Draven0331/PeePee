1.What is the Berkeley Packet Filter, using tcpdump, to capture all packets with a ttl of 64 and less, utilizing the IPv4 or IPv6 Headers? There should be 8508 packets

        sudo tcpdump -r BPFCheck.pcap 'ip[8] <= 64 || ip6[7] <= 64' | wc -l

2.What is the Berkeley Packet Filter, using tcpdump, to capture all IPv4 packets with at least the Dont Fragment bit set? There should be 2321 packets.

      sudo tcpdump -r BPFCheck.pcap 'ip[6] & 64 = 64' | wc -l

3. What is the Berkeley Packet Filter, using tcpdump, to capture traffic with a Source Port higher than 1024, utilizing the correct Transport Layer Headers? There should be 7805 packets.

        sudo tcpdump -r BPFCheck.pcap 'tcp[0:2] > 1024 || udp[0:2] > 1024' | wc -l
4. What is the Berkeley Packet Filter, using tcpdump, to capture all Packets with UDP protocol being set, utilizing the IPv4 or IPv6 Headers? There should be 1277 packets.

        sudo tcpdump -r BPFCheck.pcap 'ip[9]=0x11 || ip6[6]=0x11' | wc -l

5. What is the Berkeley Packet Filter, using tcpdump, to capture only packets with the ACK/RST or ACK/FIN flag set, utilizing the correct Transport Layer Header? There should be 1201 packets.

        sudo tcpdump -r BPFCheck.pcap 'tcp[13] = 20 || tcp[13] = 17' | wc -l
6. What is the Berkeley Packet Filter, using tcpdump, to capture all packets with an IP ID field of 213? There should be 10 packets.

        sudo tcpdump -r BPFCheck.pcap 'ip[4:2]=213' | wc -l
7. What is the Berkeley Packet Filter, using tcpdump, to capture all traffic that contains a VLAN tag? There should be 182 packets.

           sudo tcpdump -r BPFCheck.pcap 'tcp[0:2]=53 || tcp[2:2]=53 || udp[0:2]=53 || udp[2:2]=53' | wc -l
8. What is the Berkeley Packet Filter, using tcpdump, to capture the initial packets from a client trying to initiate a TCP connection? There should be 3447 packets

           sudo tcpdump -r BPFCheck.pcap 'tcp[13]=2' | wc -l
9. What is the Berkeley Packet Filter, using tcpdump, to capture the response packets from a server listening on an open TCP ports? There should be 277 packets

           sudo tcpdump -r BPFCheck.pcap 'tcp[13]=18' | wc -l
10. What is the Berkeley Packet Filter, using tcpdump, to capture the response packets from a server with closed TCP ports There should be 17 packets

            sudo tcpdump -r BPFCheck.pcap 'tcp[13]=4' | wc -l
11. What is the Berkeley Packet Filter, using tcpdump, to capture all TCP and UDP packets sent to the well known ports? There should be 3678 packets

             sudo tcpdump -r BPFCheck.pcap 'tcp[2:2]< 1024 || udp[2:2]< 1024' | wc -l
12. What is the Berkeley Packet Filter, using tcpdump, to capture all HTTP traffic? There should be 1404 packets

           sudo tcpdump -r BPFCheck.pcap 'tcp[0:2]=80 || tcp[2:2]=80' | wc -l
    
14. What is the Berkeley Packet Filter, using tcpdump, to capture all telnet traffic? There should be 62 packets

            sudo tcpdump -r BPFCheck.pcap 'tcp[0:2]=23 || tcp[2:2]=23' | wc -l
16. What is the Berkeley Packet Filter, using tcpdump, to capture all ARP traffic? There should be 40 packets

          sudo tcpdump -r BPFCheck.pcap 'ether[12:2]=0x0806' | wc -l

17. What is the Berkeley Packet Filter, using tcpdump, to capture if the "Evil bit" is set? There should be 197 packets

           sudo tcpdump -r BPFCheck.pcap 'ip[6] & 128 = 128' | wc -l
  
18.  What is the Berkeley Packet Filter, using tcpdump, to capture any packets containing the CHAOS protocol within an IPv4 header? There should be 139 packets

            sudo tcpdump -r BPFCheck.pcap 'ip[9] = 16' | wc -l
19. What is the Berkeley Packet Filter, using tcpdump, to capture all IPv4 packets with the DSCP field of 37? There should be 42 packets.

          sudo tcpdump -r BPFCheck.pcap 'ip[1]>> 2=37' | wc -l

20. What is the Berkeley Packet Filter, using tcpdump, to capture all IPv4 packets targeting just the beginning of potential traceroutes as it's entering your network. This can be from a Windows or Linux machine using their default settings? There should be 83 packets.

        sudo tcpdump -r BPFCheck.pcap 'ip[8]=1 && (ip[9]=1 || ip[9]=17)' | wc -l
22. What is the Berkeley Packet Filter, using tcpdump, to capture all packets where the URG flag is not set and URG pointer has a value? There should be 43 packets

          sudo tcpdump -r BPFCheck.pcap 'tcp[13]&32=0 && tcp[18:2]>0' | wc -l

23. What is the Berkeley Packet Filter, using tcpdump, to capture a TCP null scan to the host 10.10.10.10? There should be 19 packets

          sudo tcpdump -r BPFCheck.pcap 'tcp[13]=0x0 && ip[16:4]=0x0a0a0a0a' | wc -l

24.  What is the Berkeley Packet Filter, using tcpdump, to capture an attacker using vlan hopping to move from vlan 1 to vlan 10? There should be 15 packets

          sudo tcpdump -r BPFCheck.pcap 'ether[12:4] & 0xffff0fff = 0x81000001 && ether[16:4] & 0xffff0fff = 0x8100000a' | wc -l

