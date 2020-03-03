#Name: Donny Kell
#CSCI 4950: Senior Project

# ***VERY IMPORTANT***: Since SNORT has several dependencies packages associated with it that are not included within the source file, I am including a link with a step-by-step guide on how to download and set-up SNORT. This is to minimize both the size of the artifact file, but more importantly, to ensure that SNORT is properly installed; all that is required is to copy the commands and paste them onto the command lines with minimum alterations.

# INSTALLING SNORT

# Please follow the link and follow the guide to install SNORT on your IDS: https://blog.rapid7.com/2017/01/11/how-to-install-snort-nids-on-ubuntu-linux/

# IMPORTANT: The current SNORT release is 2.9.15.

# IMPORTANT: Please add the following touch commands when creating the rules files:
# 	touch /etc/snort/rules/dos.rules
#	touch /etc/snort/rules/scan.rules
#	touch /etc/snort/rules/ftp.rules
#	touch /etc/snort/rules/snmp.rules
#	touch /etc/snort/rules/shellcode.rules

# Please stop after executing the following step on the listed guide: 
# cp -avr *.conf *.map *.dtd /etc/snort/

# Please execute the following commands to replace the snort.conf file with the one configured file located in the misc file.
#	cd /etc/snort ; sudo rm snort.conf
#	cd ~/Downloads/artifacts/misc ; cp snort.conf /etc/snort

# CHARON REQUIREMENTS/SET-UP

# In order to use Charon correctly, several directories will need to be made in your home directory.
# Please copy and paste the following commands to set up those directories:
#	cd ; mkdir Charon ; cd Charon ; mkdir Scripts
#	cd ; mkdir snort_logs

# Please use the following commands while in your download folder to move the scripts to the correct place:
#	cd ~/Downloads/artifacts ; cp -r ./src ~/Charon/Scripts 

# Please use the following commands to ensure that the scripts have the proper permissions:
#	cd ~/Charon/Scripts ; chmod 755 Log_Sort.txt ; chmod 755 Log_Filer ; chmod 755 Sniff_Script.txt ; chmod 755 Rule_Creation.txt


# RECREATING EXPERIMENT

# Simple use the following command on the directory named "2019_12_03" located in the artifacts/data directory.
#       cd ~/Downloads/artifacts/data ; cd -r 2019_12_03 ~/snort_logs

# From there simply execute the following command:  ~/Charon/Scripts/Sniff_Script
# When prompted for the date: enter 2019_12_03
# The output will be located in the snort/etc/rules/dos.rules file.
# To get there simply type the following command:
#       cd /etc/snort/rules ; vi dos.rules


# USING SNORT (For general use)

# Please be sure to start SNORT with root privileges (sudo). Failure to do so will most likely result in a failure and cause SNORT to exit with an error.

# Use the following command to start SNORT in packet logging mode:
#	sudo snort -d -l ~/snort_logs

# IMPORTANT: To exit out of SNORT please use CTRL + C

# The snort log will be located in the snort_logs directory, if you're unsure which log file is the most recent, please use the ls -l command while in the snort_logs directory and look at the time stamp.
# IMPORTANT: You MUST convert the snort log into a tcpdump file using the following command before executing CHARON on the log file.
#	tcpdump -n -tttt -r ~/snort_logs/snortLogFileName > ~/snort_logs/anyName.txt
#	NOTE: The file name can be anything that you'd like to name it.

# USING CHARON (For general use)

# After executing the tcpdump command, you will execute CHARON in the following order:
# 	~/Charon/Scripts/Log_Sort.txt anyName.txt
#	cd ~/snort_logs ; ls -l ; cd (the directory will be named by date) ; ls -l
#	~/Charon/Scripts/Log_Filer.txt dated_file.txt ip_address_list.txt
#	NOTE: The "master" sorted log file will be named after the date so for example: 2019_12_03.txt
#	~/Charon/Scripts/Sniff_Script.txt
#	Follow the prompt.	


