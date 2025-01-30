# Steps to Resolve the Port Issue on Server

This file contains the steps to resolve the POrt issue on the server.

# Steps

1. Kindly check whether onboarded device details are correct or not.
2. Initiate the PING test to the endpoint from the source server.
   ping <device ip >
3. if ping is working then initiate the PORT 22 traffic as shown below
   telnet <device ip > 22
4. if PING test failed from the source end need to involve device management team and firewall team
5. cross-check whether device is in active state.


# Network flow and rules

SOURCE MACHINE --->  PORT 22  ------> DEVICE END POINT (UNI DIRECTINAL)

# Note : Best practise is to see the rules for the working server 
