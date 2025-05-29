## Nueva configuracion de Kitty
## cd /home/username/.config/kitty/
## s4vitar.github.io/bspwm-configuration-files
## crear directorio "kitty.conf" y el tema "ayu_mirage.conf"

# Config kitty

shell /usr/bin/zsh

# Config s4vitar

enable_audio_bell no

# Include themes color
include ayu_mirage.conf

font_family     NotoSansMono-Regular
font_family     HackNerdFont
font_size 11

disable_ligatures never

url_color #61afef

url_style curly

map ctrl+left neighboring_window left
map ctrl+right neighboring_window right
map ctrl+up neighboring_window up
map ctrl+down neighboring_window down

map f1 copy_to_buffer a
map f2 paste_from_buffer a
map f3 copy_to_buffer b
map f4 paste_from_buffer b

cursor_shape beam
cursor_beam_thickness 1.8

# Windows

mouse_hide_wait 3.0
detect_urls yes

repaint_delay 10
input_delay 3
sync_to_monitor yes

map ctrl+shift+z toggle_layout stack
tab_bar_style powerline

inactive_tab_background #e06c75
active_tab_background #98c379
inactive_tab_foreground #000000
tab_bar_margin_color black

# Map directory actual
map ctrl+shift+enter new_window_with_cwd
map ctrl+shift+t new_tab_with_cwd

# OPACITY
background_opacity 0.97

#padding
window_margin_width 3
window_padding_width 3

# Border
hide_window_decorations yes
placement_strategy center

shell zsh

