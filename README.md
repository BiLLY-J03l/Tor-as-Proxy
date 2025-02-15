# Tor-as-Proxy
This repo showcases the process of installing Tor and configuring it as a proxy for your linux machine

-We will use obfs4proxy as our Pluggable Transports (PT) which will help us bypass censorship against our beloved Tor

-you can learn more about Pluggable Transports from here https://2019.www.torproject.org/docs/pluggable-transports#user

-you cal learn more about obfs4proxy from here https://github.com/Yawning/obfs4/blob/master/doc/obfs4-spec.txt

## Update the machine

    sudo su
    apt update; apt full-upgrade -y; apt autoremove -y

## Install Tor

    sudo su
    apt install tor -y

## Install obfs4proxy

    apt install obfs4proxy -y

## Configure the /etc/tor/torrc config file, and add these lines:

    UseBridges 1
    ClientTransportPlugin obfs4 exec /usr/bin/obf4proxy

## Navigate to bridges.torproject.org, and get yourself some juciy bridges

![image](https://github.com/user-attachments/assets/f64bdb42-1ccf-407c-ba1b-e920c28208d0)
![image](https://github.com/user-attachments/assets/1ecb2e5f-b08a-480a-9122-b8df1ceb5e9e)
![image](https://github.com/user-attachments/assets/6e84fa3f-0ffc-4a0a-8225-f55034e9b7d9)

## Copy all and add them in the torrc config file like so:

    bridge obfs4 178.17.170.33:4444 07D619A6011501CC892FAA78D182F0B20C826145 cert=DdnwQv/dJBh2aeW+PQWPHKZMijhEOy593n87dKKEBb6T7DWEIZOk3LdNOOH0sRoZsDdefw iat-mode=0
    bridge obfs4 94.209.56.85:8443 1656E92FCAEF320F77A5D0EE2DC1002198DCDEF0 cert=j2Zb2539coGCVDD7B0EctUWFYN2BQflpnLTVN9kx4bT6Y9m8b8J5JTBwlB9lIYEJs+W2Mg iat-mode=0

## Save the changes and disable/stop the Tor service, as we will turn it on manually

    systemctl stop tor
    systemctl disable tor

![image](https://github.com/user-attachments/assets/896613f5-903d-45af-9acb-edc1df8fe188)

## Now we test the changes

## enter tor in the terminal and see the magic happens

    tor

### **Proxychains4**:

    vim /etc/proxychains4.conf
    
![image](https://github.com/user-attachments/assets/46057dbf-6670-4b3f-bd9a-88b32bb098f8)


### **FoxyProxy**:

