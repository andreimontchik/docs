## Configure Swap
* Review: `sudo swapon --show`
* Resize:
  1. disable: `sudo swapoff /swap.img`
  1. resize: `sudo fallocate -l 32G /swap.img`
  1. mark the file as swap: `sudo mkswap /swap.img`
  1. enable swap file: `sudo swapon /swap.img`
* Adjust swappiness:
  1. Check the current swappiness: `cat /proc/sys/vm/swappiness`
  1. Temporarily deprioritize swappiness: `sudo sysctl -w vm.swappiness=10`
  1. Permanently deprioritize swappiness: 
     1. Add `vm.swappiness = 10` to `/etc/sysctl.conf`
     1. Reload the configuration: `sudo sysctl -p`
     1. Confirm that the swap is active: `swapon --show` 
* Disable:
  1. Identify the swap file `sudo swapon --show`.
  1. Disable swapping until the next reboot: `sudo swapoff <SWAP_FILE>`.
  1. Comment out the swap configuration line in `/etc/fstab` to permanently disable swapping.
* Clear swap manually:
  1. `sudo swapoff -a`
  1. `sudo swapon -a`
  1. Check the swap status, it should on bu empty. In case if it is off, re-enable: `sudo swapon /swap.img`

## Memory mapped files limit
* Check the current limit: `sysctl vm.max_map_count`
* Increase:   
  1. Search for the `vm.max_map_count` parameter the sysctl configuration files:
     * `sudo grep max_map_count /etc/sysctl.conf`
     * `sudo grep max_map_count /etc/sysctl.d/*`
  1. Update the existing or insert the new map count parameter to `/etc/sysctl.conf`: `vm.max_map_count = 1000000`
  1. Reload the sysctl service: `sudo sysctl -p`
  1. Confirm that the files limit was updated: `sysctl vm.max_map_count`

# Stress Testing
* Use [stress-ng](https://wiki.ubuntu.com/Kernel/Reference/stress-ng)

# CLI
* Free memory: `free -th` or `cat /proc/meminfo | grep MemFree`
  * refresh every second: `free -th -s 1`
* Top 10 processes that use most memory: `ps aux --sort=-%mem | head -10`