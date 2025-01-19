#Synology
#Self-Hosted
#Docker
Sure! Open the docker app on your synology and move to network. Expand the network where your have wallabag set up. Normally you have bridge/host etc. Check the section Container if you have multiple networks and don't know where wallabag is. Look up the subnet, e.g. 172.17.0.1, and write it down.

Now move to your active firewall profile under security (control panel), click edit and add a new entry within your current profile. Select an interface you want to add, e.g. all interfaces (right top corner).

Section Ports: Select all  
Section Source IP: Select Specific and edit. Click Subnet and enter the subnet you have written down under IP address, e.g. 172.17.0.1. Enter your subnet mask in the box below, e.g. [255.255.255.0](https://255.255.255.0/). Click OK.  
Section Action: Select allow

Place the new entry at the top of all firewall rules, but above entries you denied access.