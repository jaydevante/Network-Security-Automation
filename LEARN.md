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


Packet Sniffing 

# run the command "sudo ifconfig interface promisc”
# enable Promiscuous mod

def prevent_packet_sniffing(interface):
    try:
        subprocess.call(["sudo", "ifconfig", interface, "promisc"])
        print(f"Promiscuous mode enabled on {interface}")
    except subprocess.CalledProcessError:
        print(f"Failed to enable promiscuous mode on {interface}”)
