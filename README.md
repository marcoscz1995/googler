# googler
This is instructions to set up Googler; a keyboard shortcut in linux to Google any text you highlight.
This code was made on a somewhat fresh install of Ubuntu 18.04.
This will work for any default browser (well at least with chrome or firefox).
This shorcut is executable from anywhere in your system: terminal, any browser, any application... anywhere!
This is because xclip will autimatically set the "primary selection buffer" in the clipboard for any text selected.

1)Open the terminal and install xclip if you dont already have it
	
	$ sudo apt-get install xclip


2)create a directory for bash scripts if you dont already have one

	$ mkdir ~/scripts

3)move into the scripts folder (I assume you are at the root directory) or wherever you house your bash scripts

	$ cd ~/scripts

4)make a bash script and call it googler (or whatever you want) using your editor of choice (I prefer gedit but nano is cool too)
	
	$ gedit googler

5)add the following bash script to the file and save it

	#!/bin/bash
	search=`xclip -o`
	echo "Googling: $@"
	for term in $@; do
	search="$search%20$term"
	done
	xdg-open "http://www.google.com/search?q=$search"

6)make the file executable

	$ chmod +x googler

7)set the keyboard shortcut

go to Settings->Devices->Keyboard, then scroll to the bottom and hit the '+' icon to add new shortcut

Name the command:
	
	Name: Googler (or whatever you want to call it)

Set the path to the script:

	Command: /home/<your user name>/scripts/googler   (or the path to wherever you saved the script)

Set the shortcut:

enter the keyboard combo you desire. I chose Alt+1 so that I can highlight with my right hand on the mouse and execute with my left hand; I think this is the most efficient use of this script.

8)put it in action

just highlight any text and hit the keyboard shortcut you assigned to it and a new google chrome tab will open with your search results!

9)Enjoy your new small bump in productivity!

10)Optional step

you can change the search command in the script to search stack overflow only. This is left as an exercise to the reader ;)

