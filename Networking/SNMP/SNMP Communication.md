### What protocol does an SNMP server use to get information from SNMP devices in a network or how does those devices make a connection and send updates to the SNMP sever?
An SNMP (Simple Network Management Protocol) server uses the SNMP protocol to get information from SNMP devices in a network. SNMP is an application-layer protocol that enables the management and monitoring of network devices and systems. The SNMP server acts as a central management station, and the SNMP devices (often referred to as agents) are the network devices being managed.

Here's how the SNMP server communicates with SNMP devices to get information:

1. **SNMP Requests from Server to Devices**:
   The SNMP server sends SNMP requests (GET, GETNEXT, or GETBULK) to the SNMP devices. These requests are used to retrieve specific information from the devices, such as system status, network interface statistics, or other data.

2. **SNMP Responses from Devices to Server**:
   Upon receiving an SNMP request, the SNMP devices process the request and respond back to the SNMP server with the requested information. The responses typically include the requested data or status values.

3. **SNMP Traps and Notifications**:
   SNMP devices can also send unsolicited messages called SNMP traps or notifications to the SNMP server. Traps are used to report important events, such as system failures, link status changes, or environmental alerts. These traps are sent asynchronously when specific events occur, and the SNMP server can act on them accordingly.

4. **Management Information Base (MIB)**:
   SNMP devices have a Management Information Base (MIB), which is a database that contains the hierarchical structure of variables and data accessible via SNMP. Each variable in the MIB is uniquely identified by an Object Identifier (OID), and the SNMP server uses these OIDs to reference the desired information in SNMP requests.

5. **Community Strings**:
   SNMP devices and servers use community strings as a simple form of authentication to control access to the devices. There are two types of community strings: read-only (often called "public") and read-write (often called "private"). The SNMP server must provide the appropriate community string when sending SNMP requests to the devices.

6. **Version Compatibility**:
   SNMP comes in multiple versions, such as SNMPv1, SNMPv2c, and SNMPv3. The SNMP server and devices must use compatible SNMP versions for successful communication. SNMPv3 provides additional security features like authentication and encryption.

Overall, the SNMP server communicates with SNMP devices by sending requests to fetch specific information and receives responses from the devices with the requested data. Additionally, the SNMP devices can send unsolicited traps or notifications to the server to report important events. This exchange of information allows network administrators to monitor and manage devices across the network using the SNMP protocol.