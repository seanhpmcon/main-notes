### Definitions
Technical Report 069 (TR-069) is a technical specification of the Broadband Forum that defines an application layer protocol for remote management and provisioning of customer-premises equipment (CPE) connected to an Internet Protocol (IP) network. TR-069 uses the CPE WAN Management Protocol (CWMP) which provides support functions for auto-configuration, software or firmware image management, software module management, status and performance managements, and diagnostics.

The CPE WAN Management Protocol is a bidirectional SOAP- and HTTP-based protocol, and provides the communication between a CPE and auto configuration servers (ACS). The protocol addresses the growing number of different Internet access devices such as modems, routers, gateways, as well as end-user devices which connect to the Internet, such as set-top boxes, and VoIP-phones.

TR-069 was first published in May 2004, with amendments in 2006, 2007, 2010, July 2011 (version 1.3), and November 2013 (version 1.4 am5)

Other technical initiatives, such as the Home Gateway Initiative (HGI), Digital Video Broadcasting (DVB) and WiMAX Forum endorsed CWMP as the protocol for remote management of residential networking devices and terminals.

CWMP is a text based protocol. Orders sent between the device (CPE) and auto configuration server (ACS) are transported over HTTP (or more frequently HTTPS). At this level (HTTP), the CPE acts as client and ACS as HTTP server. This essentially means that control over the flow of the _provisioning session_ is the sole responsibility of the device.

Resource -> https://en.wikipedia.org/wiki/TR-069