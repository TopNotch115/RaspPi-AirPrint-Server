#The Operating system I'm using: Raspbian 
#First we need to make sure our Raspberry Pi is up-to-date. 
sudo apt-get update
sudo apt-get upgrade

#Install CUPS | This will take up to 20 minutes. 
sudo apt-get install cups

#Now we need to add the pi user the lpadmin group. 
sudo usermod -a -g lpadmin pi 

#CUPS is default set to block any non-localhost traffic. #Accept all incoming trafic by running the following:
sudo cupsctl --remote-any 
sudo systemctl restart cups

#Get your Pi's local IPv4 address
hostname -I 

#Connect via web browser to your CUPS URL with port 631
"https://192.168.2.99:631"

#Install SAMBA if you're planning on printing from a Windows device. 
sudo apt-get install samba

#open the smb.conf file on your Raspberry Pi to make a few edits. 
sudo nano /etc/samba/smb.conf


#Edit the file to match the following: 
"
# CUPS printing.  
[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
guest ok = yes
read only = yes
create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = no
guest ok = no
"

#Save the file by pressing CTRL + X and then pressing Y and then ENTER.

#Restart SAMBA once the file is saved:
sudo systemctl restart smbd

#Navigate to the CUPS webpage 
 "https://192.168.2.99:631" #(Using your Pi's IPv4 address
     #Click "Administration" at the top of the menu.
     #Click "Add Printer"
     #Select your Printer model you're using then "Continue"
     #The rest is is pretty simple. Complete addiing your printer(s) before moving on.

#On your Windows device, add the printer to your workstation and install the correct drivers. Print docs to test the success. 