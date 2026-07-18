# Common Setup

1. Install Ubuntu.
1. Update apt: `sudo apt update`
1. Update the system kernel: `sudo apt upgrade` then `reboot`.
1. Install vim: `sudo apt install vim`
1. Terminal improvements:
   - Update the configured alias for `ls` in `.bashrc` - add the `--group-directories-first` param to the `alias ls` configuration.
   - Install Tilix:
     1. `sudo apt install tilix`
     1. Configure to run as login shell: Preferences -> Default -> Command -> check `Run command as login shell`.
     1. Configure the `Copy on Select` for mouse: Preferences -> Global -> check `Automatically copy text to clipboard when selecting`.
     1. Configure theme: Preferences -> Appearance -> Theme variant -> Dark. Also check the `Use a wide handle for splitters` checkbox.
1. Install htop: `sudo apt install htop`
1. [Install iftop](../../public/wiki/network#iftop)
1. [Install net-tools](../../public/wiki/network#net-tools)
1. [Install iostat](../../public/wiki/disk#iostat)
1. Install curl: `sudo apt install curl`

# Workstation

1. Configure keyboard and mouse. Apple Magic Keyboard and Logitech Mx Master 3S connected via Bluetooth.
1. Attach and configure additional monitor:
   Linux: \* Scale 200%
1. Install Chrome:
   1. Download from https://www.google.com/chrome
   1. `sudo apt install <chrome .deb file>`
   1. Disable running in background and graphics acceleration in Chrome: Settings -> System
1. Install additional fonts:
   - Linux:
     1. `sudo apt install fonts-roboto fonts-cascadia-code fonts-firacode`
     1. Install Google Fonts. Needed for VSCode and Chrome.
        1. [Download the fonts archive](https://github.com/google/fonts/archive/main.zip)
        1. `unzip fonts-main.zip -d google_fonts`
        1. Copy fonts to the system fonts directory:
           ```
           sudo cp fonts-main/ufl/ubuntu/*.ttf /usr/share/fonts/;
           sudo cp fonts-main/ufl/ubuntucondensed/*.ttf /usr/share/fonts/;
           sudo cp fonts-main/ufl/ubuntumono/*.ttf /usr/share/fonts/
           ```
     1. Update the system fonts cache: `sudo fc-cache -f -v`
   - MacOS: Instal FiraCode fonts: https://github.com/tonsky/FiraCode/releases
1. rkhunter - audit rootkits: tbd
1. ClamAV - the Malware/virus scanner
   ```
   sudo apt install clamav
   sudo freshclam          # Update definitions
   sudo clamscan -r /home  # Scan recursively
   ```
1. Sublime:
   1. Download the `.deb` archive from https://www.sublimetext.com/download
   1. `cd ~/Downloads`
      - Linux: `dpkg -i sublime-text_build-xxx.deb`
      - MacOS: extract the archive and move `sublime` in the `Application` directory.
   1. Add Sublime to shell .`.zshrc` or `.bashrc`: `alias subl='/opt/sublime_text/sublime_text'`
1. SSH
   1. Generate SSH keypair: `ssh-keygen -t ed25519 -C "andrei@montchik.net"`
      - choose the default location in the `~\.ssh` directory
      - keep the password empty
   1. Add pubkey to GitHub account: https://github.com/settings/keys
   1. Restart terminal session before using the newly created and registered keypair.
1. [Install Git](../../public/wiki/Git#install).
1. [Increase swap file](../../public/wiki/memory#swap-file) in case if short on memory.
1. [Install Rust and set up Solana Dev env-t](solana/Solana-Development-Resources.md#setup-local-dev-env-t)
1. [Install VS Code](../../public/wiki/vscode)

# Server

1. Update the `root` password.
1. [Switch to UTC](../../public/wiki/linux#other)
1. Complete the [Common Setup](Provisioning#common-setup) steps.
1. Check out the host hardware:
   - CPU: `cat /proc/cpuinfo | grep "model name" | head -1`
   - Memory: `cat /proc/meminfo | grep "Mem"`
   - Disks: `sudo lsblk`
   - Network:
     1. Identify the network NIC: `ip a`
     1. Install the `ethtool`: `sudo apt install ethtool`
     1. `sudo ethtool <NIC> | grep Speed`
1. Confirm that the system clock is synchronized: `timedatectl status`. If not install ntp.
1. [Create the `andrei` user and add it to the `sudo` and `systemd-journal` groups](../../public/wiki/Linux#users-and-groups)
1. Re-login as `andrei`.
1. Restrict user access to specific users or groups.
1. Install or update SSH agent:
   - [Install SSH](../../public/wiki/linux#ssh)
   - Update SSH:
     1. Check the SSH server version: `sshd -V 2>&1 | grep "OpenSSH"`
     1. `sudo apt install --only-upgrade openssh-server`
     1. `sudo systemctl restart ssh`
     1. Check the SSH server version: `sshd -V 2>&1 | grep "OpenSSH"`
1. Disable root access:
   1. Create the `99-sandbox-init.conf` file in the `/etc/ssh/sshd_config.d/` directory.
   ```
   PermitRootLogin no
   ```

   1. Restart SSH server: `sudo systemctl restart ssh`.
   1. Confirm that root cannot login.
1. Enable SSH key authentication.
   1. Propagate the Workstation's SSH key: run `ssh-copy-id andrei@<server ip>` on Workstation.
   1. Add the `PubkeyAuthentication yes` parameter to the `/etc/ssh/sshd_config.d/99-sandbox-init.conf` file.
   1. Restart SSH server: `sudo systemctl restart ssh`.
   1. Confirm that the SSH key authentication works.
1. [Configure the ufw firewall](../../public/wiki/network#firewall).
1. Disable password authentication:
   1. Add the `PasswordAuthentication no` parameter to the `/etc/ssh/sshd_config.d/99-sandbox-init.conf` file.
   1. Restart SSH server: `sudo systemctl restart ssh`.
1. [Install and configure fail2ban](../../public/wiki/Network#fail2ban)
1. [Install and configure git](../../public/wiki/git)
1. [Install Rust](../../public/wiki/rust)
1. [Install Solana CLI](../../research/wiki/install-solana)
