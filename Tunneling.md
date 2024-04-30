## SSH PORT FORWARDING
    -Creates channels using SSH-CONN protocol
    -Allows for tunneling of other services through SSH
    -Provides insecure services encryption  

SSH OPTIONS
      
      ** -L - Creates a port on the client mapped to a ip:port via the server  (allows the client to connect to the server)

      ** -D - Creates a port on the client and sets up a SOCKS4 proxy tunnel where the target ip:port is specified dynamically

      ** -R - Creates the port on the server mapped to a ip:port via the client     (allows the server to connect to the client)

      -NT - Do not execute a remote command and disable pseudo-tty (will hang window)

 ##  SSH ARCHITECTURE

Client vs Server vs Session

    Keys:

    User Key - Asymmetric public key used to identify the user to the server

    Host Key - Asymmetric public key used to identify the server to the user

    Session Key - Symmetric key created by the client and server to protect the session’s communication.       
     
## SSH LOCAL PORT FORWARDING
Syntax

        ssh -p <optional alt port> <user>@<pivot ip> -L <local bind port(you make this up)>:<tgt ip>:<tgt port> -NT

        or (just demonstrating that you can do differnt things)

        ssh -L <local bind port>:<tgt ip>:<tgt port> -p <alt port> <user>@<pivot ip> -NT

## SSH KEY CHANGE FIX

    ssh-keygen -f "/home/student/.ssh/known_hosts" -R "172.16.82.106"
    
    Copy/Paste the ssh-geygen message to remove the Host key from the known_hosts file
EXAMPLE
        
        Creates 1111 on the Internet_Host mapped to Blue_INT_DMZ_Host-1 port 22 thru Blue_DMZ_Host-1.

    Internet_Host:
    
    ssh student@172.16.1.15 -L 1111:172.16.40.10:22 -NT

    or

    ssh -L 1111:172.16.40.10:22 student@172.16.1.15 -NT
 EXAMPLES FOR DIFFERENT PORTS
     
     Internet_Host:

    ssh student@172.16.1.15 -L 1112:172.16.40.10:80 -NT
    firefox localhost:1112
    
    ssh student@172.16.1.15 -L 1113:172.16.40.10:23 -NT
    telnet localhost 1113

    ssh student@172.16.1.15 -L 1113:172.16.40.10:3389 -NT
    xfreerdp /v:localhost:1113 /u:student /p:password

## SSH DYNAMIC PORT FORWARDING

    ssh -D <port> -p <alt port> <user>@<pivot ip> -NT
    
    -Proxychains default port is 9050
    -Creates a dynamic socks4 proxy that interacts alone, or with a previously established remote or local port forward.
    -Allows the use of scripts and other userspace programs through the tunnel.
    
  ## SSH DYNAMIC PORT FORWARDING 1-STEP
    Internet_Host:

    ssh student@172.16.1.15 -D 9050 -NT

    proxychains ./scan.sh
    proxychains nmap -Pn 172.16.40.0/27 -p 21-23,80
    proxychains ssh student@172.16.40.10
    proxychains telnet 172.16.40.10
    proxychains wget -r http://172.16.40.10
    proxychains wget -r ftp://172.16.40.10  

## SSH DYNAMIC PORT FORWARDING 2-STEP
    Internet_Host:
   
    ssh student@172.16.1.15 -L 1111:172.16.40.10:22 -NT
    ssh student@127.0.0.1 -p 1111 -D 9050 -NT

    proxychains ./scan.sh
    proxychains nmap -Pn 172.16.82.96/27 -p 21-23,80
    proxychains ssh student@172.16.82.106
    proxychains telnet 172.16.82.106
    proxychains wget -r http://172.16.82.106
    proxychains wget -r ftp://172.16.82.106

## SSH REMOTE PORT FORWARDING

    Syntax

    ssh -p <optional alt port> <user>@<remote ip> -R <remote bind port>:<tgt ip>:<tgt port> -NT

    or

    ssh -R <remote bind port>:<tgt ip>:<tgt port> -p <alt port> <user>@<remote ip> -NT
