# Server Configuration FreeIPA

## Static Hostname
    /etc/hostname
    
    10.0.0.1       server.ipa.test server
    
    sudo dnf install dnsmasq
    sudo nano /etc/dnsmasq.conf
    address=/onner.test/10.3.0.1
    sudo systemctl enable --now dnsmasq
    
## Install DNS freeIPA
    dnf install freeipa-server-dns
    
    ipa --version
    
## Configuration 
    ipa-server-install --setup-dns --auto-reverse
    
    
    * autenthication keros
        Directory Manager password: 1001onner
        IPA admin password : 1001@dm!n
        
