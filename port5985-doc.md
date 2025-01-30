# Steps to Resolve the Port 5985 Issue on Server

This file contains the steps to resolve the Port 5985 issue on the server.

# Steps

1. Kindly check whether onboarded device details are correct or not.
2. Initiate the PING test to the endpoint from the source server.
   ping <device ip >
3. if ping is working then initiate the PORT 5985 traffic as shown below
   telnet <device ip > 5985
4. if PING test failed from the source end need to involve device management team and firewall team
5. cross-check whether device is in active state.


# Network flow and rules

SOURCE MACHINE --->  PORT 5985  ------> DEVICE END POINT (UNI DIRECTINAL)

# Additonal settings 

Kindly verify whether psrp /winrm is enabled or not on endpoint 


# Note : Best practise is to see the rules for the working server 
