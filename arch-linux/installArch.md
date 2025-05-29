# Installation ARCH LINUX UEFI
### Verificacion del teclado
  loadkeys es
### verificacion de internet
  ping -c 1 google.es
  ip link
  ping archlinux.org
  
  # actializacion del reloj del sistemas
  timedatectl
### seleccionar el tipo de particiones
  cfdisk  -> GPT
  fdisk -l
  lsblk   -> ver las particiones realizadas.
### formatear particiones
 1. mkfs.fat -F 32 /dev/sda1   :: /boot or /efi
 2. mkswap /dev/sda2            :: swap
 2. mkfs.btrfs /dev/sda3         :: /
 3. mkfs.btrfs /dev/sda4         :: /home
 
    swapon /dev/sda2            :: activar swap
    
### Montar los sistemas de archivos
    mount /dev/sda3 /mnt           # Montar la raíz /
    
    mkdir /mnt/boot/efi
    mount /dev/sda1 /mnt/boot/efi      # Montar /boot
    
    mkdir /mnt/home
    mount /dev/sda4 /mnt/home      # Montar /home
    
### Instalar paquetes esenciales

  pacstrap /mnt base base-devel linux linux-headers linux-firmware mkinitcpio            # general
  pacstrap /mnt amd-ucode      # amd
  pacstrap /mnt intel-ucode         # intel
  
### Definir un archivo fstab que contienen las informacion concerniente a las particiones
    
    genfstab -U /mnt >> /mnt/etc/fstab
  
### Chroot
    ::: para entrar en modo root
    arch-chroot /mnt
    
----------------------------------------------------------------------------------------
### Instalar paquetes adicionales
    pacman -S networkmanager grub wpa_supplicant
    pacman -S vim
    pacman -S sudo
    pacman -S nano
    
### Configuracion de teclados
    nano /etc/vconsole.conf
    :: KEYMAP=es
    
### Creacion de usuarios
    passwd
    ls /home/
    useradd -m lion
    passwd lion
    
### Añadir a un grupo el usuario creado
    usermod -aG wheel lion
    groups lion
    
### configuracion de sudoers
    nano /etc/sudoers
    :: %wheel ALL=(ALL:ALL) ALL
    
### Zona horaria
    ln -sf /usr/share/zoneinfo/America/Lima /etc/localtime
    hwclock --systohc
### Configuracion de las regiones
    nano /etc/locale.gen
    ::en_US.UTF-8 UTF-8     ->referencia al idioma ingles
    ::es_PE.UTF-8 UTF-8     ->referencia al idioma español
    locale-gen
    
    
### Configurar el nombre de la maquina
    cat /etc/hostname
    echo aspire > /etc/hostname
    
### Configurcion del Host
    nano /etc/hosts
    :: 127.0.0.1    localhost
    :: ::.1         localhost
    :: 127.0.0.1    aspire.localhost aspire
    
### Install GRUB BootLoader
    :: EFI
    pacman -S grub os-prober efibootmgr
    grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=Arch
    grub-install --target=x86_64-efi --efi-directory=/boot/efi --removable

    :: edit grub
    nano /etc/default/grub
    
    :: BIOS
    pacman -S grub os-prober
    grub-install /dev/sda
    
    grub-mkconfig -o /boot/grub/grub.cfg

### Desmontar
    umount /dev/sda1
    swapoff /dev/sda2
    umount /dev/sda3
    umount /dev/sda4
    
## reboot now or poweroff ---------------------------------------------

### Activar servicios
    systemctl enable NetworkManager
    systemctl start NetworkManager
    
    nmtui
    
    systemctl start wpa_supplicant.service
    systemctl enable wpa_supplicant.service
    
### Install AUR
    pacman -S git
    :c: dirigirse al usuario personal
    mkdir -p Desktop/lion/repos     <-
    git clone https://aur.archlinux.org/paru-bin.git
    :c: dirigirse a la carpeta de descarga
    makepkg -si

### Interfaz gráfica -----------------------------------------
    pacman -S xorg xorg-server
    pacman -S gnome
    
    systemctl start gdm.service
    systemctl enable gdm.service
    
### Install PAMAC
    sudo pacman -S pacman
    
    git clone https://aur.archlinux.org/pamac-aur.git
    
    makepkg -si
