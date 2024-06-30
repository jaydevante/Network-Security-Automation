# Network-Security-Automation
A set of network security tools to assist in port scanning and preventing packet sniffing.
Port Scanning Tool:
   - Develop a function `port_scan` that takes a target host, start port, and end port as input.
   - The function will perform a port scan on the specified range of ports for the given target host.
   - It will create a socket for each port and check if the connection is successful.
   - Ports that are found to be open will be stored in a list and returned.
   - The function will handle any errors that occur during the connection attempt.
     
Packet Sniffing Prevention Tool:
   - Develop a function `prevent_packet_sniffing` that takes a network interface as input.
   - The function will enable promiscuous mode on the specified network interface.
   - It will execute a command to enable promiscuous mode using the `sudo ifconfig` command.
   - The function will handle any errors that occur during the execution of the command.
     
