# Credential Harvester
## Victim Setup
This script will open up a new google search. However, the script changes the hosts file on the windows machine it runs on to redirect the request to google.com to the ip address it has listed (currently 172.0.0.1). From this the victim machine is ready for the social engineering attack.
## Server Setup
From SEToolkit, utilizing the website cloning method and the _website templates_ that are built in, SEToolkit will copy a login page for google.com. After selecting the google template, make sure that the IP address selected matches the one in the script above. From this, if the computers are on the same network (or the attacker has a public IP), the victim will be directed to the attackers computer which is a fake sign in page. 
