# Synology WebDAV for Joplin
#software/NAS #software/productivity
So just to recap, and anyone can correct me if I’m wrong; to get WebDAV synchronisation working on a synology NAS:
1-Create a Joplin shared folder at the highest level in File Station.
2-Download WebDAV server from the Package Center.
3-Enable HTTP/HTTPS.
4-Under External Access in Control Panel, select Add under DDNS to create a registered hostname.
5-Under Router Configuration, select Create to add port forwarding rules for the ports used in the WebDAV server application (the default 5005,5006 were used in this case).
6-Go to your Router and open the same ports. In my case, I have a Lynksis router and it was under Security->Apps and Gaming->Port Range Forwarding.
7-Go back to Router Configuration under External Access and test the connection. Should result in “ok” in the Connection Test Result column.
8-I would suggest manually backing up your notes to the Joplin folder and to another folder on your desktop or a drive in case synchronisation tries to delete your notes.
9-Under the Synchronisation section of Joplin:
-use http://[local IP address]:5005/joplin/ for the desktop version
-use https://*.synology.me:5006/joplin/ for the mobile version. In this case, this address needs to be the same one you created in STEP 4.
10-Enter the login credentials under WebDAV username/password for your Synology NAS.
11-Select “Check synchronisation configuration”. Should result in “Success! Synchronisation configuration appears to be correct.”
12-Now you can select Synchonise in the main tab and you’re done!