# Docs
* The onload user guide: http://www.smallake.kr/wp-content/uploads/2015/12/SF-104474-CD-20_Onload_User_Guide.pdf

# Security
## ufw
* Check all installed firewall related packages: `dpkg -l | grep firewall`
* Check the `ufw` (Uncomplicated Firewall) status: `sudo ufw status`
* Configure `ufw`: 
  1. Confirm the SSH port: 
     1. Run the `sudo netstat -tulna` command and locate the line about tcp connection between the Host and Workstation IPs, something like this: `tcp        0      0 162.250.126.142:22      76.16.6.193:37418       ESTABLISHED`. The Hosts port is an SSH port, usually it is 22.
  1. Add the allow SSH rule to: `sudo ufw allow ssh`
  1. Add the deny incoming rule: `sudo ufw default deny incoming`
  1. Add the allow outgoing rule: `sudo ufw default allow outgoing`
  1. Confirm that the rule is added to `/etc/ufw/user.rules` and `/etc/ufw/user6.rules`
  1. Enable `ufw`. Note, that if SSH access is misconfigured, the SSH connectivity will be lost!: `sudo ufw enable`
  1. Confirm that `ufw` is enabled: `sudo ufw status`.
  1. Check the `/var/log/ufw.log` `ufw` log for errors.

## Fail2Ban
1. Install: `sudo apt install fail2ban`
1. Create the config file. Use `/etc/fail2ban/jail.conf` as reference 
   1. `sudo touch /etc/fail2ban/jail.local`
   1. Add the following to configuration to `jail.local`to evaluate SSH connections:
    ```
    [DEFAULT]
    ignoreip = 127.0.0.1/8 ::1 <WORKSTATION_IP>
    bantime  = 10m
    findtime  = 10m
    maxretry = 10
    banaction = ufw
    banaction_allports = ufw

    [sshd]
    enabled = true
    port    = ssh
    logpath = %(sshd_log)s
    backend = %(sshd_backend)s
      ```
    1. Start the fail2ban service: `sudo systemctl start fail2ban`
    1. Enable fail2ban: `sudo systemctl enable fail2ban`
    1. Check `/var/log/fail2ban.log` for errors.
    1. Check the fail2ban status and the list of banned IPs: `sudo fail2ban-client status sshd`

# Util
## iftop
The console app to visualize network bandwidth. [Documentation](https://www.linuxjournal.com/content/sysadmins-toolbox-iftop)
* Install:
  1. `sudo apt update; sudo apt install iftop`
* Run: `sudo iftop`
  * press `p` to display ports
  * press `n` to disable/enable DNS resolution
  * press `t` to toggle between transmitted only / received only and bi-directional traffic        
  * columns on the right are 2, 10 and 40 sec averages, press `1`, `2` or `3` to sort by them

## [net-tools](https://www.geeksforgeeks.org/netstat-command-linux/)
Collection of networking tools.
### netstat
* Install: `sudo apt install net-tools`
* List of network interfaces: `netstat -i`
* Review routing table: `netstat -nr`
* Review multicast groups: `netstat -g`
* Find out which apps are using the specific port: 
  * `sudo netstat -tuanp | grep 8003`
  * `ss -tuanp | grep 8003` 
  * `lsof -i -P -n | grep LISTEN`

### [netcat](https://phoenixnap.com/kb/nc-command)
Sends and receives data between two computers/netwioks via TCP or UDP.
* Install: `apt-get install netcat`
* Check connectivity: `netcat -vz <ip or hostname> port`

### [tcpdump](https://opensource.com/article/18/10/introduction-tcpdump)
Captures network traffic.
* List of available interfaces: `tcpdump -D`
* Capture 5 packets from all NICs from the specific host and port and print the ASCII content of a packet:
      `tcpdump -i any -nn -c 5 -A host <hostname> and port <port>`
* Capture packets on the mutlicast enabled `core` NIC and UDP port :`tcpdump -i core -vv  udp port <udp port>`

### ethtool
Check for dropped packets.
* Run `/sbin/ethtool -S s1p1 | grep drop`
  * `rx_noskb_drops` -  number of packets dropped when there are no further socket buffers to use.
  * `port_rx_nodesc_drops` - number of packets dropped when there are no further descriptors in the rx ring buffer to receive them.
  * `port_rx_dp_di_dropped_packets` - number of packets dropped because filters indicate the packets should be dropped. This can happen when packets don’t match any filter or the matched filter indicates the packet should be dropped.
* The Ethernet bonding driver level: `cat /proc/net/bonding/core`

# Tuning
## Increase UDP r/w buffers size
* Check: 
```
sysctl net.core.rmem_default; \
sysctl net.core.rmem_max; \
sysctl net.core.wmem_default; \
sysctl net.core.wmem_max;
```
* Update until the next reboot:
```
sudo sysctl -w net.core.rmem_default=134217728 \
sudo sysctl -w net.core.rmem_max=134217728; \
sudo sysctl -w net.core.wmem_default=134217728; \
sudo sysctl -w net.core.wmem_max=134217728;
```
* Reload the sysctl service to pick up the change: `sudo sysctl -p`
* To update permanently add the following to `/etc/sysctl.conf`:
```
net.core.rmem_default = 134217728
net.core.rmem_max = 134217728
net.core.wmem_default = 134217728
net.core.wmem_max = 134217728
```

## [Increase number of allowed open file descriptors](Disk.md#increase-number-of-allowed-open-file-descriptors)

# CLI
* Show list of all NICs: `ip a` or `ifconfig`
* Show routing table: `netstat -rn`
* Show current connection status of NICs: `nmcli device status`
* Show local IP: `hostname -I`
* Show public IP from external source: `curl ifconfig.me`
* Turn WIFI on/off: `sudo nmcli radio wifi [on|off]`

