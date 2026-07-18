# System

- Host information, kernel and OS version etc: `hostnamectl`
- Shell type: `echo %0`
- Review environment variables:
  - `printenv`
  - `env`
- Reboot: `sudo reboot`
- Latest restart time: `uptime`
- All processes info: `ps -ef` or `ps aux`
- Specific process info: `ps -p <pid> -o pid,vsz=MEMORY -o user,group=GROUP -o comm,args=ARGS`
- Show the kernel message buffer since the latest reboot: `dmesg -T`
- Monitor system activity real-time: `joiurnalctl -f`
  - Monitor kernel messages: `joiurnalctl -fk`

## [systemctl](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units)

- Configuration location: `/etc/systemd/system/`
- List of units: `sudo systemctl list-units  --all`
  - Mark inactive units: `sudo systemctl list-units --all --state=inactive`

# [CPU](CPU.md)

# [Memory](Memory.md)

# [Disk](Disk.md)

# [Network](Network.md)

# Navigation and Search

- Show only directories: `ls -la | grep "^d"`
- Find file by name:
  - from current directory: `find . -name "docker-compose*"`
  - from the root: `find / -name "docker-compose*"`
- Find the program location: `which python3` or `type -a python3` or `command -v python3`
- Recursive search in files starting from current directory: `find . -name "*.ts" -exec grep -H "extends Assignable" {} +`
- Search with regular expression: `grep -iE "cpu|disk" *`

# Users and groups

- The users/groups configuration file: `/etc/group`
- List of users: `sudo cat /etc/group`
- List of groups: `groups`
- Users in a group: `grep docker /etc/group`
- Create new user: `sudo adduser andrei`
- Add user to a group: `sudo usermod -aG docker andrei`
  - Add user to the sudoers group:`sudo usermod -aG sudo andrei`
  - Confirm that the user was added to a group: `groups andrei`
- Swith to root: `su -`
- Change owner recursively: `sudo chown -R newuser:newgroup /mnt/data`
- Show currently connected users: `who`

# SSH

- Install openssh-server to allow SSH access:
  1. `sudo apt-get update`
  1. `sudo apt-get install openssh-server`
  1. Start the server `sudo service ssh start` or `sudo systemctl start ssh`
- Generate SSH key for the new user on the client machine: `ssh-keygen -t ed25519 -C "your_email@example.com"`
- Configure SSH key based authentication: run `ssh-copy-id username@host` on the client machine.

# Archiving

- Archive files: `tar -czvf archive.tar.gz file1 file2`
- Archive directory: `tar -czvf archive-name.tar.gz directory/*`
- View the archive contents: `tar -tvf archive.tar.gz`
- Test the archive:
  - zst: `zstd --test archive.tar.zst`
- Extract:
  - bz2 archive: `tar -xjf archive.tar.bz2`
  - gz archive: `tar -xvf archive.tar.gz`
  - zst archive: `tar --use-compress-program=unzstd -xvf archive.tar.zst`
- Install application from the `.deb` archive: `sudo dpkg -i your-package-name.deb`

# Symbolic Links

- Create symbolic link to file: `ln -s ~/src/cpp/common/messaging/sbe/me/me.xml .`
- Create symbolic link to directory: `ln -s /path/to/src_directory ~/symlink_directory`

# Data transfer

- Copy file from host: `scp andrei@64.233.160.01:/home/andrei/data/account_update.json .`
- Copy directory from host: `scp -r andrei@64.233.160.01:/home/andrei/data/ .`
- Copy file to network host: `scp account_update.json andrei@64.233.160.01:/home/andrei/data`
- Copy directory to network host: `scp -r data andrei@76.16.6.193:/tmp`

# Other

- Generate UNIX Timestamp: `date +%s`
- Change time zone:
  1. Check the current timezone: `timedatectl`
  1. Set timezone to UTC: `sudo timedatectl set-timezone UTC`
- Rotate logs: `logrotate /etc/logrotate.hourly.d/containers`
- Convert HEIC images to JPEG: install and use the heif-convert` converter.
- Format JSON:`jq . <SOURCE_FILE> >> <FORMATTED_FILE>`
