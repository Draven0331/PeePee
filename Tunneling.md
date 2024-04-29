## SSH PORT FORWARDING
    -Creates channels using SSH-CONN protocol
    -Allows for tunneling of other services through SSH
    -Provides insecure services encryption  

SSH OPTIONS
      
      -L - Creates a port on the client mapped to a ip:port via the server

      -D - Creates a port on the client and sets up a SOCKS4 proxy tunnel where the target ip:port is specified dynamically

      -R - Creates the port on the server mapped to a ip:port via the client

      -NT - Do not execute a remote command and disable pseudo-tty (will hang window)

      
