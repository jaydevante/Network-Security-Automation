Port Scanning

# create a new socket
# set the timeout for the socket to 1 second
#   add the current port to the open_ports list
#  close the socket
#  ignore the error and continue to the next port

import socket

def port_scan(target_host, start_port, end_port):
    open_ports = []
    for port in range(start_port, end_port+1):
        try:
            sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            sock.settimeout(1)
            result = sock.connect_ex((target_host, port))
            if result == 0:
                open_ports.append(port)
            sock.close()
        except socket.error:
            pass
    return open_ports

    The `port_scan` function takes three parameters: `target_host`, `start_port`, and `end_port`. It performs a port scan on the specified range of ports for the given `target_host`.

Inside the function, an empty list called `open_ports` is created to store the ports that are found to be open. A loop is then used to iterate through each port in the range from `start_port` to `end_port`.

For each port, a new socket is created, and the timeout for the socket is set to 1 second. The `connect` function is called to connect to the `target_host` on the current port. If the result of the connection is 0, it means that the connection was successful, and the current port is added to the `open_ports` list.

After checking each port, the socket is closed. If there is any error during the connection attempt, such as a socket error, it is caught and ignored, allowing the loop to continue to the next port.

Finally, the `open_ports` list is returned, containing all the ports that were found to be open.



Packet Sniffing 

# run the command "sudo ifconfig interface promisc”
# enable Promiscuous mod

def prevent_packet_sniffing(interface):
    try:
        subprocess.call(["sudo", "ifconfig", interface, "promisc"])
        print(f"Promiscuous mode enabled on {interface}")
    except subprocess.CalledProcessError:
        print(f"Failed to enable promiscuous mode on {interface}”)


        The `prevent_packet_sniffing` function takes one parameter: `interface`, which represents the network interface on which promiscuous mode needs to be enabled.

Inside the function, an attempt is made to run the command "sudo ifconfig interface promisc" to enable promiscuous mode on the specified `interface`. If the command runs successfully, a message is printed indicating that promiscuous mode has been enabled on the interface. If there is any error during the execution of the command, a message is printed indicating that the attempt to enable promiscuous mode failed.






        
