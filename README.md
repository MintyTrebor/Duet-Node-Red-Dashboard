# Duet-Node-Red-Dashboard

This is a simple mobile formatted node red dashboard that I use as a simple live status monitor for 2 3d printers. The flow achieves the following functions:  

Powers on a RPi & 3d Printer(s) via MQTT and a tasmota wifi pwr socket(s).  
Queries both 3d Printers (running Duet RepRap Firmware) for status information every 15 seconds including:  
	Current Bed Temp  
	Current HotEnd Temp  
	Current Enclousure Temp (only implemented for 1 printer)  
Displays the webcam streams montioring each printer 
Allows a target enclousure temp to be set and automatically turns on/off a heater via MQTT and tasmota wifi pwr socket.  
Safely shutsdown the RPi remotely using "sshpass" to remotely send shutdown command to the RPi (you will need to change this cmd to meet your environments details)  

Notes:  
Two different methods for getting the data from the Duet RRF are used for completeness. One method is universal the other will only work with RRF deployed with a companion SBC.
The flow to turn on/off the wifi tasmota sockets is not included as it is standard Node-Red MQTT functionality - In my implementation it is part of a larger node-red dashboard (see my other node-red dashboard repo for the full dasboard).  
Global and flow persistent variables are used to maintain system knowledge of states - incase of pwr loss / restart of node-red.  
The flow will only turn off the PI if both printers are shut down.

The flow uses the following addtional pallete nodes:  

node-red-contrib-looptimer  
node-red-dashboard  

This is a work in progress and is only provided for reference purposes.