### So how does an application on the computer know how to route information through the computer's NIC?

Applications on a computer do not directly handle the routing of information through the computer's NIC (Network Interface Card). Routing is managed by the operating system and network protocols rather than individual applications.

When an application wants to send data, it communicates with the operating system through network APIs (Application Programming Interfaces) provided by the operating system. The application specifies the destination IP address and port number it wants to send the data to, along with the data itself.

The operating system's network stack takes over from there and determines how the data should be routed through the computer's NIC. It examines the destination IP address and consults the routing table to determine the appropriate network interface (which may correspond to the NIC) through which the data should be sent. The routing table contains information about various network destinations and associated network interfaces.

Once the appropriate network interface (NIC) is identified, the operating system encapsulates the data into packets at the network layer (IP layer), adds the necessary headers (such as IP headers), and sends the packets to the NIC for transmission over the physical network.

In summary, applications rely on the operating system's network stack and APIs to handle the routing of information through the computer's NIC. The operating system determines the appropriate route based on the destination IP address and manages the transmission of data through the network interfaces. Applications focus on specifying the destination and content of the data, leaving the routing details to the underlying network infrastructure provided by the operating system.