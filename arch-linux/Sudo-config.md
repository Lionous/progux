# Config sudo
- primero diridigirse a share como root

cd /usr/share
sudo su

mkdir zsh-sudo
chown username:username zsh

cd zsh-sudo
wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/refs/heads/master/plugins/sudo/sudo.plugin.zsh

-- reiniciar

# Fuentes
https://www.nerdfonts.com/

sudo su
cd /usr/share/fonts

mv /home/username/Downloads/Hack.zip .
unzip Hack.zip

# ZSH tambien para root
ln -s -f /home/username/.zshrc /root/.zshrc

usermod --shell /usr/bin/zsh root


# Config icons
/home/username/.local/share/icons

- con sudo
/usr/share/icons



# Para la contraseña
nano etc/sudoers
Defaults env_reset,pwfeedback


