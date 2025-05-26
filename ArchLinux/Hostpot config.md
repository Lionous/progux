# Hostpot config

    iw list | grep -A 10 "Supported interface modes"
    
    * AP

*No todas las tarjetas Wi-Fi soportan "Access Point" (modo AP). Usa este comando para verificar:*
    
# Intalacion **dnsmasq**

    sudo pacman -S dnsmasq


# Puedes hacerlo manualmente

    nmcli dev wifi hotspot ifname wlan0 ssid MiHotspot password 12345678

*Reemplaza wlan0 por el nombre de tu dispositivo Wi-Fi (lo puedes ver con ip a o nmcli device). ejemplo*

    nmcli dev wifi hotspot ifname wlp4s0 ssid ACER-ASPIRE password 123456789

# Verificar si re reinicio correctamte...

    sudo systemctl restart NetworkManager
    
*tambien verifiucar si dhcpcd este isntalado y corriendo correcntamente*

# Firewall

 *Desactivar el firewall si es que no funciona correctamente el Hostpot*


