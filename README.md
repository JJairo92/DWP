DWP
===

Deployment of Web Projects

## Git Server Installation

Download and install git

	sudo apt-get install git-core

Update your recent packages

	sudo apt-get update

Add git username and email to gitconfig file

	git config --global user.name "username"
	git config --global user.email "email@email.com"

## Clone Repository to Server

	git clone [github]

If a folder already exists, remove it, then add the repository again
	
	rm -rvf [folderName]
	git clone [github]