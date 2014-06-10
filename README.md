DWP
===
Deployment of Web Projects

# Creating Basic Server


## Setting Up Server
1. Login as root
	ssh root@[ipAddress]

2. Add user
	adduser [userName]
	adduser [userName] sudo

3. Logout of root and login with new user
	exit
	ssh [userName]@[ipAddress]

4. Update and Upgrade Package System
	sudo apt-get update
	sudo apt-get upgrade

Update package system after upgrade
	sudo apt-get update

4. Install Apache2
	sudo apt-get install apache2

Update package system
	sudo apt-get update

5. Install Git
	sudo apt-get install git-core

Update package system
	sudo apt-get update

Add git username and email
	git config --global user.name "username"
	git config --global user.email "email@email.com"

6. Change permissions to /var/www directory
	sudo chown [userName] /var/www

7. Create a new server and repeat steps 1-6 for that server


## Creating Git Hook
1. Switch to beginning of file system
	cd /

2. Create directory for repos
	sudo mkdir /var/repos

3. Change permissions to /var/repos directory
	sudo chown [userName] /var/repos

4. Switch to repos directory and make a new directory for the page created
	cd /var/repos
	mkdir [pageName].git

5. Switch to hooks directory; separate working tree and git directory locations
	cd [pageName].git/hooks
	nano post-receive

Write in editor
	#!/bin/sh
	GIT_WORK_TREE=/var/www git checkout -f

Save file

6. Change permissions to post-receive
	chmod +x post-receive


## Pushing to Server
Inside local git directory (where all files for page are)

1. Make sure you are in master branch
	git checkout master

2. Add Stage Server remote
	git remote add [stageServerName] ssh://[userName]@[ipAddress]/var/repos/[pageName].git

3. Add Production Server remote
	git remote add [productionServerName] ssh://[userName]@[ipAddress]/var/repos/[pageName].git

4. Check status of files ready to be committed
	git status

5. Add all files to be committed later
	git add -A

6. Commit all files
	git commit -m '[Enter message of changes made]'

7. Push to stage server
	git push [stageServerName] master

8. Make sure everything is working fine in stage server, test everything, once everything has been tested push to production server
	git push [productionServerName] master