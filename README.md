# Linux-DNS-Tools
Scripts to help with altering/fixing Linux DNS issues.


These are a few simple scripts I wrote that help automate prepending/un-prepending DNS servers, fixing broken links, and displaying the DNS status.
These scripts are specifically for Debian-based Linux scripts and may not work on other Linux distributions.


### dns_prepend

Prepends DNS servers and restarts the network manager.
This script literally un-comments the prepend domain-name-servers line in dhclient.conf.
NOTE: Before running this script, you should have a list of 1-3 nameservers already listed in /etc/dhcp/dhclient.conf
(libc/glibc will not prepend more than 3 nameservers)

Example (circa line 25 in /etc/dhcp/dhclient.conf): 
  `#prepend domain-name-servers 208.67.222.222, 208.67.220.220, 8.8.8.8;`

FYI (for those that may not already know):
208.67.222.222 && 208.67.220.220 are OpenDNS nameservers.
8.8.8.8 is Google's nameserver.

### dns_original

Removes any prepended DNS servers in /etc/dhcp/dhclient.conf and restarts the network manager

### dns_status

concatenates the result /etc/resolv.conf to the terminal window

### dns_fixlink

On more than one occasion, updates to debian-based distributions have caused the link between the DNS resolver and the config file in /etc/ to break.
This can cause a lot of headaches, though it is a simple fix. 
This one-liner script exists to resolve my headaches, and prevents me from having to rememeber the exact syntax every time


It may be beneficial to create aliases out of these scripts in your .bashrc.

