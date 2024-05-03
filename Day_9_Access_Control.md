## Access Control 
NETFILTER HOOKS - > CHAIN

      -NF_IP_PRE_ROUTING → PREROUTING
      -NF_IP_LOCAL_IN → INPUT
      -NF_IP_FORWARD → FORWARD
      -NF_IP_LOCAL_OUT → OUTPUT
      -NF_IP_POST_ROUTING → POSTROUTING

## NETFILTER PARADIGM

  tables - contain chains
              
       -filter - default table. Provides packet filtering.

       -nat - used to translate private ←→ public address and ports.

       -mangle - provides special packet alteration. Can modify various fields header fields.
     
  chains - contain rules
     
    -PREROUTING - packets entering NIC before routing

    -INPUT - packets to localhost after routing

    -FORWARD - packets routed from one NIC to another. (needs to be enabled)

    -OUTPUT - packets from localhost to be routed

    -POSTROUTING - packets leaving system after routing 
     
  rules - dictate what to match and what actions to perform on packets when packets match a rule

## CHAINS ASSIGNED TO EACH TABLE
      -filter - INPUT, FORWARD, and OUTPUT

      -nat - PREROUTING, POSTROUTING, INPUT, and OUTPUT

      -mangle - All chains

## COMMON IPTABLE OPTIONS

      -t - Specifies the table. (Default is filter)
      -A - Appends a rule to the end of the list or below specified rule
      -I - Inserts the rule at the top of the list or above specified rule
      -R - Replaces a rule at the specified rule number
      -D - Deletes a rule at the specified rule number
      -F - Flushes the rules in the selected chain  (CHANGE THE DEFAULT POLICY BEFORE FLISHING WITH (-p))
      -L - Lists the rules in the selected chain using standard formatting
      -S - Lists the rules in the selected chain without standard formatting
      -P - Sets the default policy for the selected chain
      -n - Disables inverse lookups when listing rules
      --line-numbers - Prints the rule number when listing rules    

## COMMON IPTABLE OPTIONS
      
      -p - Specifies the protocol
      -i - Specifies the input interface
      -o - Specifies the output interface
      --sport - Specifies the source port
      --dport - Specifies the destination port
      -s - Specifies the source IP
      -d - Specifies the destination IP
      -j - Specifies the jump target action

## IPTABLES SYNTAX
sudo iptables -t [table] -A [chain] [rules] -j [action]
            
            Table: filter*, nat, mangle

            Chain: INPUT, OUTPUT, PREROUTING, POSTROUTING, FORWARD    

## IPTABLES RULES SYNTAX
    
      -i [ iface ]

      -o [ iface ]

      -s [ ip.add | network/CIDR ]

      -d [ ip.add | network/CIDR ]

      -p icmp [ --icmp-type type# { /code# } ]

      -p tcp [ --sport | --dport { port1 |  port1:port2 } ]

      -p tcp [ --tcp-flags SYN,ACK,PSH,RST,FIN,URG,ALL,NONE ]

      -p udp [ --sport | --dport { port1 | port1:port2 } ]
      
   -m to enable iptables extensions:

     *** -m state --state NEW,ESTABLISHED,RELATED,UNTRACKED,INVALID

         -m mac [ --mac-source | --mac-destination ] [mac]

     *** -p [tcp|udp] -m multiport [ --dports | --sports | --ports { port1 | port1:port15 } ]

         -m bpf --bytecode [ 'bytecode' ]

     ***  -m iprange [ --src-range | --dst-range { ip1-ip2 } ]  
       
## IPTABLES ACTION SYNTAX
      
      -ACCEPT - Allow the packet

      -REJECT - Deny the packet (send an ICMP reponse)

      -DROP - Deny the packet (send no response)

                  -j [ ACCEPT | REJECT | DROP ]      

## MODIFY IPTABLES
 
 Flush table

      iptables -t [table] -F

Change default policy

      iptables -t [table] -P [chain] [action]

Lists rules with rule numbers

      iptables -t [table] -L --line-numbers

Lists rules as commands interpreted by the system

      iptables -t [table] -S

Inserts rule before Rule number

      iptables -t [table] -I [chain] [rule num] [rules] -j [action]

Replaces rule at number

      iptables -t [table] -R [chain] [rule num] [rules] -j [action]

Deletes rule at number

      iptables -t [table] -D [chain] [rule num]  

