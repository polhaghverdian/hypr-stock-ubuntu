# hypr-stock-ubuntu

## Quick Start

1. Install the packages:
```sh
sudo apt update && sudo apt install hyprland hypridle hyprlock hyprpaper hyprpolkitagent hyprpicker waybar wofi swayosd wlsunset jq kitty fonts-font-awesome brightnessctl playerctl wl-clipboard uwsm git ubuntu-wallpapers bluetooth network-manager-iwd
```

2. Disable waybar,hyprpaper and wpa_supplicant (replaced with iwd) from starting with systemd:
```
systemctl --user --global disable waybar.service
systemctl --user --global disable hyprpaper.service
systemctl disable wpa_supplicant.service 
```

3. Clone this repo to bring in copies of the needed config files and scripts:
```sh
git clone https://github.com/polhaghverdian/hypr-stock-ubuntu.git
```

4. Copy the files into their canonical paths:
```sh
cd hypr-stock-ubuntu/dotfiles
mkdir -p ~/.local/bin
mkdir -p ~/.config
cp -i bin/* ~/.local/bin
cp -ir foot hypr waybar wofi ~/.config
```

5. Add following at the end of the .bashrc file
```
if uwsm check may-start && uwsm select; then
	exec uwsm start default
fi
```
## Packages and how each one is used

| Package | Description |
| :--- | :--- |
| `hyprland` | The compositor; the star of the show. |
| `hypridle` | Manages timers for when to dim the screen, lock the session, and suspend the machine when the user is idle. It also talks with `systemd` to make sure the session is locked when the machine is suspended. |
| `hyprlock` | Screen-lock app. It locks the session and displays an authentication prompt to unlock it. |
| `hyprpaper` | Manages the background wallpaper. |
| `hyprpolkitagent` | Shows an authentication pop-up dialog box when root privilege is needed. |
| `hyprpicker` | Used with keybinding for copying pixel hex colors. |
| `waybar` | Displays a status bar across the top of the screen. |
| `wofi` | Displays menus for things like launching applications. |
| `swayosd` | Shows an on-screen-display for things like brightness and volume. |
| `kitty` | Terminal program which works well with Hyprland; e.g. no title bar. |
| `wlsunset` | Changes the color temperature of the display; i.e. a night light. |
| `jq` | Parses the output from Hyprland tools inside some of the included scripts. |
| `fonts-font-awesome` | Provides icons for Waybar and the system menu. |
| `brightnessctl` | Used with keybindings to control display brightness. |
| `playerctl` | Used with keybindings to control media playback. |
| `wl-clipboard` | Wayland clipboard CLI. Used with the screenshot keybinding. |
| `git` | Only needed to clone this repo. |

## Scripts and how each one is used

| Script | Description |
| :--- | :---|
| `hyprland-keybinds` | Shows a dynamic menu of keybindings based on the running Hyprland config. |
| `hyprland-logout` | Tries to gracefully shutdown session processes in the right order on logout.
| `hyprland-window-pop` | Manages the logic of popping out windows (`SUPER + O`).
| `nightlight-status` | Tells the nightlight icon in the Waybar whether the nightlight is on or off. |
| `nightlight-toggle` | Toggles the nightlight on/off. Used by the Waybar and in a keybinding.
| `system-menu` | Shows a menu of actions like lock, suspend, reboot, etc.
