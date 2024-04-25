
## SOCKET TYPES

        
        -Stream Sockets - Connection oriented and sequenced; methods for connection establishment and tear-down. Used with   TCP, SCTP, and Bluetooth.

        -Datagram Sockets - Connectionless; designed for quickly sending and receiving data. Used with UDP.

        -Raw Sockets - Direct sending and receiving of IP packets without automatic protocol-specific formatting.

## USER SPACE VS. KERNEL SPACE SOCKETS

      **User Space Sockets = The most common sockets that do not require elevated privileges to perform actions on behalf of user applications

              -Stream Sockets
              -Datagram Sockets

    **Kernel Space Sockets= Attempts to access hardware directly on behalf of a user application to either prevent encapsulation/decapsulation or to create packets from scratch, which requires elevated privileges.

              -Raw Sockets  

## UNDERSTANDING PYTHON TERMINOLOGY    

    **Libraries (Standard Python Library)

        --Modules (_import module)
                
                -Functions (module.function)
                -Exceptions (try:)
                -Constants
                -Objects ()
                -List [] vs Tuple ()

        --BUILT-IN FUNCTIONS
               
                -int()
                -len()
                -str()
                -sum()
                -print()

       --BUILT-IN METHODS
             
              -my_string.upper()
              -my_string.lower()
              -my_string.split()
              -my_liSt.append()
              -my_list.insert()
      
       -- HOW IMPORTS WORK
       
            -import {module}
            -import {module} as {name}
            -from {module} import *
            -from {module} import {function}
            -from {module} import {function} as {name}

## NETWORK PROGRAMMING WITH PYTHON3  

Network sockets primarily use the Python3 Socket library and socket.socket function.

      --import socket
          s = socket.socket(socket.FAMILY, socket.TYPE, socket.PROTOCOL)
## THE SOCKET.SOCKET FUNCTION

Inside the socket.socket. function, you have these arguments, in order:

        socket.socket( *family*, *type*, *proto* )
  
              -family: AF_INET (default), AF_INET6, AF_UNIX

              -type: SOCK_STREAM (default), SOCK_DGRAM, SOCK_RAW

              -proto: 0 (default), IPPROTO_TCP, IPPROTO_UDP, IPPROTO_IP, IPPROTO_ICMP, IPPROTO_RAW

              
## Example Script 

      #!/usr/bin/python3
      import socket
      # THIS CAN ASLO BE ACCOMPLISHED BY USING S = SOCKET.SOCKET()
      s = socket.socket(socket.AF_INET, socket.SOCK_STREAM, 0)
      ip_addr = '127.0.0.1'
      port = 45678
      s.connect((ip_addr, port))
      message =(b"USMC > Navy > Space Forece > Dead\n")
      s.send(message)
      #IT IS RECCOMENDED THAT THE BUFFERSIZE USED WITH RECVFROM
      data, conn = s.recvfrom(1024)
      # IN ORDER TO RECIEVE A MESSAGE THAT IS SENT AS A BYTE-LIKE OBJECT
      print(data.decode('utf-8'))
      s.close()

## Example IP RAW script 

    import socket
    import sys
    from struct import * 

    try:
              s = socket.socket(socket.AF_INET, socket.SOCK_RAW, socket.IPPROTO_RAW) 
    except socket.error as msg:
              print(msg)
              sys.exit()

      packet =  ''

     src_ip = "10.10.10.10"
     dest_ip = "20.20.20.20"

     ip_ver_ihl =  69
     ip_tos = 0
     ip_len = 0
     ip_id = 1775
     ip_frag = 0
     ip_ttl = 64
     ip_proto = 16
     ip_check = 0
     ip_srcadd = socket.inet_aton(src_ip)
     ip_dstadd = socket.inet_aton(dest_ip)

     ip_header = pack('!BBHHHBBH4s4s', ip_ver_ihl, ip_tos, ip_len, ip_id, ip_frag, ip_ttl, ip_proto, ip_check, ip_srcadd, ip_dstadd)

     message = b'Almost made it to chow'
     packet = ip_header + message 

     s.sendto(packet, (dest_ip, 0 ))


  ## Example TCP RAW script

      import socket
      import sys
      import array
      from struct import * 

      try:
              s = socket.socket(socket.AF_INET, socket.SOCK_RAW, socket.IPPROTO_RAW)
      except socket.error as msg:
              print(msg)
              sys.exit()

      packet =  ''

      src_ip = "10.10.10.10"
      dest_ip = "20.20.20.20"

      ip_ver_ihl =  69
      ip_tos = 0
      ip_len = 0
      ip_id = 1918
      ip_frag = 0
      ip_ttl = 64
      ip_proto = 6
      ip_check = 0
      ip_srcadd = socket.inet_aton(src_ip)
      ip_dstadd = socket.inet_aton(dest_ip)

      ip_header = pack('!BBHHHBBH4s4s', ip_ver_ihl, ip_tos, ip_len, ip_id, ip_frag, ip_ttl, ip_proto, ip_check, ip_srcadd, ip_dstadd)

      tcp_src = 1945
      tcp_dst = 1975
      tcp_seq = 454
      tcp_ack_seq = 0
      tcp_data_off = 5
      tcp_reserve = 0
      tcp_flags = 0
      tcp_win = 63535
      tcp_chk = 0
      tcp_urg_ptr = 0

      tcp_off_res = (tcp_data_off << 4) + tcp_reserve
  
      tcp_fin = 0
      tcp_syn = 1
      tcp_rst = 0
      tcp_psh = 0
      tcp_ack = 0
      tcp_urg = 0
      tcp_ece = 0
      tcp_cwr = 0

      tcp_flags = tcp_fin + (tcp_syn << 1) + (tcp_rst << 2) + (tcp_psh << 3) + (tcp_ack << 4) + (tcp_urg << 5) + (tcp_ece << 6) + (tcp_cwr << 7)

      tcp_hdr = pack ('!HHLLBBHHH', tcp_src, tcp_dst, tcp_seq, tcp_rst, tcp_psh, tcp_ack, tcp_urg, tcp_ece, tcp_cwr)

      user_data = b'Ann loves men'

      #pseudo header
      src_address = socket.inet_aton(src_ip)
      dst_address = socket.inet_aton(dest_ip)
      reserved = 0
      protocol = socket.IPPROTO_TCP
      tcp_length = len(tcp_hdr) + len(user_data)

      ps_hdr = pack ('!4s4sBBH', src_address, dst_address, reserved, protocol, tcp_length)
      ps_hdr = ps_hdr + tcp_hdr + user_data

      def checksum(data):
              if len(data) % 2 != 0:
                      data += b'\0'
              res = sum(array.array("H", data))
              res = (res >> 16) + (res & 0xffff)
              res += res >> 16
              return (~res) & 0xffff

      tcp_chk = checksum(ps_hdr)

      tcp_hdr =  pack ('!HHLLBBH', tcp_src, tcp_dst, tcp_seq, tcp_ack_seq, tcp_off_res, tcp_flags, tcp_win) + pack('H', tcp_chk) + pack('!H', tcp_urg_ptr)

      packet = ip_header + tcp_hdr + user_data

      s.sendto(packet, (dest_ip, 0))

## Python Hex encode script 

        #!/usr/bin/python3
        import socket
        import binascii
        # THIS CAN ASLO BE ACCOMPLISHED BY USING S = SOCKET.SOCKET()
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM, 0)
        ip_addr = '127.0.0.1'
        port = 45678
        s.connect((ip_addr, port))
        message2 = b"are you still typing"
        hidden_msg = binascii.hexlify(message2)
        #message =(b"USMC > Navy > Space Forece > Dead\n")
        s.send(hidden_msg)
        decoded_msg = binascii.unhexlify(hidden_msg)
        s.send(decoded_msg)
        #IT IS RECCOMENDED THAT THE BUFFERSIZE USED WITH RECVFROM
        data, conn = s.recvfrom(1024)
        # IN ORDER TO RECIEVE A MESSAGE THAT IS SENT AS A BYTE-LIKE OBJECT
        print(data.decode('utf-8'))
        s.close()

## BASE64 ENCODING AND DECODING


        #!/usr/bin/python3
        import socket
        import binascii
        import base64
        # THIS CAN ASLO BE ACCOMPLISHED BY USING S = SOCKET.SOCKET()
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM, 0)
        ip_addr = '127.0.0.1'
        port = 45678
        s.connect((ip_addr, port))
        message2 = b"are you still typing"
        hidden_msg = base64.b64encode(message2)
        #message =(b"USMC > Navy > Space Forece > Dead\n")
        s.send(hidden_msg)
        decoded_msg = base64.b64decode(hidden_msg)
        s.send(decoded_msg)
        #IT IS RECCOMENDED THAT THE BUFFERSIZE USED WITH RECVFROM
        data, conn = s.recvfrom(1024)
        # IN ORDER TO RECIEVE A MESSAGE THAT IS SENT AS A BYTE-LIKE OBJECT
        print(data.decode('utf-8'))
        s.close()

## TCP_RAW_Encoded W/ base64

        import socket
        import sys
        import array
        import base64
        from struct import * 

        try:
                s = socket.socket(socket.AF_INET, socket.SOCK_RAW, socket.IPPROTO_RAW)
        except socket.error as msg:
                print(msg)
                sys.exit()

        packet =  ''

        src_ip = "10.10.0.40"
        dest_ip = "172.16.1.15"

        ip_ver_ihl =  69
        ip_tos = 0
        ip_len = 0
        ip_id = 2020
        ip_frag = 0
        ip_ttl = 64
        ip_proto = 6
        ip_check = 0
        ip_srcadd = socket.inet_aton(src_ip)
        ip_dstadd = socket.inet_aton(dest_ip)

        ip_header = pack('!BBHHHBBH4s4s', ip_ver_ihl, ip_tos, ip_len, ip_id, ip_frag, ip_ttl,             ip_proto, ip_check, ip_srcadd, ip_dstadd)

        tcp_src = 54321
        tcp_dst = 1234
        tcp_seq = 90210
        tcp_ack_seq = 30905
        tcp_data_off = 5
        tcp_reserve = 0
        tcp_flags = 0
        tcp_win = 63535
        tcp_chk = 0
        tcp_urg_ptr = 0

        tcp_off_res = (tcp_data_off << 4) + tcp_reserve

        tcp_fin = 0
        tcp_syn = 1
        tcp_rst = 0
        tcp_psh = 0
        tcp_ack = 0
        tcp_urg = 0
        tcp_ece = 0
        tcp_cwr = 0

        tcp_flags = tcp_fin + (tcp_syn << 1) + (tcp_rst << 2) + (tcp_psh << 3) + (tcp_ack << 4) + (tcp_urg << 5) + (tcp_ece << 6) + (tcp_cwr << 7)

        tcp_hdr = pack ('!HHLLBBHHH', tcp_src, tcp_dst, tcp_seq, tcp_rst, tcp_psh, tcp_ack, tcp_urg, tcp_ece, tcp_cwr)

        user_data = b'Griffith'
        hidden_msg = base64.b64encode(user_data)

        #pseudo header
        src_address = socket.inet_aton(src_ip)
        dst_address = socket.inet_aton(dest_ip)
        reserved = 0
        protocol = socket.IPPROTO_TCP
        tcp_length = len(tcp_hdr) + len(hidden_msg)

        ps_hdr = pack ('!4s4sBBH', src_address, dst_address, reserved, protocol, tcp_length)
        ps_hdr = ps_hdr + tcp_hdr + hidden_msg

        def checksum(data):
                if len(data) % 2 != 0:
                        data += b'\0'
                res = sum(array.array("H", data))
                res = (res >> 16) + (res & 0xffff)
                res += res >> 16
                return (~res) & 0xffff

        tcp_chk = checksum(ps_hdr)

        tcp_hdr =  pack ('!HHLLBBH', tcp_src, tcp_dst, tcp_seq, tcp_ack_seq, tcp_off_res, tcp_flags, tcp_win) + pack('H', tcp_chk) + pack('!H', tcp_urg_ptr)

        packet = ip_header + tcp_hdr + hidden_msg

        s.sendto(packet, (dest_ip, 0))



               
