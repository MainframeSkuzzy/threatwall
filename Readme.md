# Threatwall

* While this application (alpha/development release at the moment) works as expected in testing,please test it well before using it in production just like any other new software.

## THREATWALL - blocks indicators of compromise (supported ones) using iptables from a git synchronized list

 THREATWALL synchrnoizes with a remote git repository which would contain a list of IP addresses,domains,urls,etc...
 iptables blocks are then placed on the system based on these indicators.
 This repository is synchronized at a configurable (default 30min) interval.
 
 The default repository is built from various open source threat intelligence sources (mainly Alienvault Threat exchange).
 
 You can maintain your own repository fed from your own threatintel sources,honeypots,fail2ban,various application logs,etc...
 
 No guarantee is made on the quality of the blocklists,a *very important* consideration would be poor quality (accidental or intentional) indicators 
 being blocked which might cause a service outage or important sites being blocked.
 
 This is designed for a low-impact system that can afford to block something like 'google.com' by accident yet contains important data.
 
 That being said, it does support whitelists for each type of indicator (e.g.: whitelist.IPv4), use this feature to whitelist all important IP addresses,URLs,domains,etc... 
  
 These considerations change if you maintain your own repository with all your important sites whitelisted(filtered out),
 which would mean only potentially malicious indicators will be blocked.
 
 
 
# Usage


```		
Usage: python2  threatwall.py  [-vhBSlTtcrfoi]  
		-i	<DROP|ACCEPT|REJECT,..> INPUT chain policy
		-o  <DROP|ACCEPT|REJECT,..> OUTPUT chain policy
		-f  <DROP|ACCEPT|REJECT,..> FORWARD chain policy
		-r  <https://url/> remote git repository that stores the indicators
		-c  <fspath> Filesystem path used to clone the remote repository to
		-t  </temporarypath/> Filesystem path used to store temporary files
		-T  <DROP|ACCEPT|REJECT,..> iptables chain 'policy' target for the THREATWALL chain
		-l  <path> Filesystem path used to store logfiles
		-S  <secs> Interval in seconds between syncing of the remote git repository
		-B  Run in background (Foreground is default)
		-v  Print this applications current version string
		-h  Display this usage instruction.

```

# Known Bugs


* none at this time (still in development)


