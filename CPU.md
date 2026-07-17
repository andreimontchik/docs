# Tuning
* Check the CPU frequency scaling: `cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor | sort -u`
* Switch the CPU Governor to the "performance" mode for all CPUs: `echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor`

# Stress Testing
* Use [stress-ng](https://wiki.ubuntu.com/Kernel/Reference/stress-ng)

# CLI
* CPU info: `cat /proc/cpuinfo`
* Current frequency per core: `cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq`
* Monitor the cores frequency: `watch -n 1 "grep 'cpu MHz' /proc/cpuinfo"`
* `cpufreq-info` - CPU information
  1. `sudo apt install cpufrequtils` 
  1. `cpufreq-info -c 27`
