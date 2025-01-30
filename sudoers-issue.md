sudo configuration with normal sudo commands

# download the sudoers file from the sharepoint 

Collect the below configuration backup.

cp /etc/sudoers /etc/sudoers_bkp

Implementation plan:
1. Login to the server as superuser  and open two sessions with root.Please start implementing change in one session and run top command in another session . 
2. Use visudo command to open the sudo file
3. Add the below command
##############################################################################################
#Do not delete for DA use

#Set host alias as below:
#=========================
Host_Alias    IBM_AE_HOSTS = ALL

#Set User Alias as below:
#=========================
User_Alias     IBM_AE_BAU = %automata


#Set command alias as below:
#============================
Cmnd_Alias  IBM_UNIX_AE_BAU_CMDS =  /usr/bin/su -, /bin/su -, /usr/bin/su -root, /bin/su -root, /bin/sh


#Set Rule Specification as below:
#================================
IBM_AE_BAU  IBM_AE_HOSTS =  NOPASSWD:ALL,IBM_UNIX_AE_BAU_CMDS 

      4.Verify  if there is no error .
        visudo -cf /etc/sudoers
        You shouldn’t see any error.
  If you find any error .Please resolve the issue and reachout SME if any help needed.

 5.Please logout from this session and login again .Now you should able to sudo su – without any issue.



