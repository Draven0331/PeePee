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
EXAMPLE

    Creates 1111 on the Internet_Host mapped to the localhost port 22 of Blue_DMZ_Host-1.

    Internet_Host:
    ssh student@172.16.1.15 -L 1111:localhost:22 -NT

    or

    ssh -L 1111:localhost:22 student@172.16.1.15 -NT



