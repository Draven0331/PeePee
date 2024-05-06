## SYNTAX TO CREATE ACCESS LISTS
    Demo> enable #enter privileged exec mode
    
    Demo# configure terminal #enter global config mode
    
    Demo(config)# access-list 37 ... (output omitted) ...
    
    Demo(config)# ip access-list standard block_echo_request
    
    Demo(config)# access-list 123  ... (output omitted) ...
   
    Demo(config)# ip access-list extended zone_transfers


## STANDARD NUMBERED ACL SYNTAX
    router(config)# access-list {1-99 | 1300-1999}  {permit|deny}  {source IP add} {source wildcard mask}
   
    router(config)#  access-list 10 permit host 10.0.0.1
   
    router(config)#  access-list 10 deny 10.0.0.0 0.255.255.255
    
    router(config)#  access-list 10 permit any

    
## STANDARD NAMED ACL SYNTAX
    router(config)# ip access-list standard [name]
   
    router(config-std-nacl)# {permit | deny}  {source ip add}  {source wildcard mask}
   
    router(config)#  ip access-list standard CCTC-STD
  
    router(config-std-nacl)#  permit host 10.0.0.1
    
    router(config-std-nacl)#  deny 10.0.0.0 0.255.255.255
    
    router(config-std-nacl)#  permit any

## EXTENDED NUMBERED ACL SYNTAX
    router(config)# access-list {100-199 | 2000-2699} {permit | deny} {protocol}
                {source IP add & wildcard} {operand: eq|lt|gt|neq}
                {port# |protocol} {dest IP add & wildcard} {operand: eq|lt|gt|neq}
                {port# |protocol}
    
    router(config)# access-list 144 permit tcp host 10.0.0.1 any eq 22
    
    router(config)# access-list 144 deny tcp 10.0.0.0 0.255.255.255 any eq telnet
    
    router(config)# access-list 144 permit icmp 10.0.0.0 0.255.255.255 192.168.0.0 0.0.255.255 echo
   
    router(config)# access-list 144 deny icmp 10.0.0.0 0.255.255.255 192.168.0.0 0.0.255.255 echo-reply
    
    router(config)# access-list 144 permit ip any any


## EXTENDED NAMED ACL SYNTAX
     router(config)# ip access-list extended  [name]
     router(config-ext-nacl)# [sequence number] {permit | deny} {protocol}
                         {source IP add & wildcard} {operand: eq|lt|gt|neq}
                         {port# |protocol} {dest IP add & wildcard} {operand:
                         eq|lt|gt|neq} {port# |protocol}
    
     router(config)# ip access-list extended CCTC-EXT

     router(config-ext-nacl)# permit tcp host 10.0.0.1 any eq 22
    
     router(config-ext-nacl)# deny tcp 10.0.0.0 0.255.255.255 any eq telnet
     
     router(config-ext-nacl)# permit icmp 10.0.0.0 0.255.255.255 192.168.0.0
                         0.0.255.255 echo
    
     router(config-ext-nacl)# deny icmp 10.0.0.0 0.255.255.255 192.168.0.0
                         0.0.255.255 echo-reply
     
     router(config-ext-nacl)# permit ip any any

## APPLY AN ACL TO AN INTERFACE OR LINE
    router(config)#  interface {type} {mod/slot/port}
   
    router(config)#  ip access-group {ACL# | name} {in | out}
    
    router(config)#  interface s0/0/0
    
    router(config-if)#  ip access-group 10 out
    
    router(config)#  interface g0/1/1
    
    router(config-if)#  ip access-group CCTC-EXT in
   
    router(config)#  line vty 0 15
    
    router(config)#  access-class CCTC-STD in     

    
## This will run snort as a Daemon 

    sudo snort -D -l /var/log/snort -c /etc/snort/snort.conf
## This will run snort as a pcap

    sudo snort -c /etc/snort/rules/file.rules -r file.pcap

    














## APPLY AN ACL TO AN INTERFACE OR LINE

      router(config)#  interface {type} {mod/slot/port}
      
      router(config)#  ip access-group {ACL# | name} {in | out}
      
      router(config)#  interface s0/0/0
      
      router(config-if)#  ip access-group 10 out
      
      router(config)#  interface g0/1/1
      
      router(config-if)#  ip access-group CCTC-EXT in
     
      router(config)#  line vty 0 15
     
      router(config)#  access-class CCTC-STD in

      
