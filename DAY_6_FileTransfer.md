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
    
