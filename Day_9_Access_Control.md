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


