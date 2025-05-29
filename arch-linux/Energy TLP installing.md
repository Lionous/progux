# Energy TLP
# installing
sudo pacman -S tlp

# Ruta
sudo nano /etc/default/tlp

# Configuracion
CPU_SCALING_GOVERNOR="performance"
CPU_SCALING_GOVERNOR="ondemand"
CPU_SCALING_GOVERNOR="schedutil"
CPU_SCALING_GOVERNOR="powersave"

# reboot
sudo systemctl restart tlp

# status
tlp-stat -s
