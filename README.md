Understanding Cisco DMVPN (Dynamic Multi-point VPN)

Dynamic multi-point VPN is a cost-effective solution for interconnecting lots of branch offices together with ease of configuration and security. 
It reduces the configuration complexity and increases flexibility and scalability.

With DMVPN a central hub router in the head office manages all the spoke location router with the dynamic IP address and can access company 
resources anywhere from the locations.

DMVPN utilizes mGRE tunnels, NHRP, and IPSec encryption to interconnect spoke and hub routers together without compromising security and 
flexibility.

DMVPN Components

 mGRE tunnels

  Next hop Resolution Protocol (NHRP)

   Routing Protocols
    Dynamic IPSec encryption

mGRE Tunnels

   No need to configure the Tunnel destination.
    Mapping is through NHRP Protocol.

   Endpoints are configured as mGRE tunnels

   Only needed tunnel source and mode to mGRE for enable configuration.

NHRP Next hop resolution Protocol

   Map the tunnel with the NBMA address.

   Building Dynamic database of spoke address with dynamic public IP addresses

   Routers can be configured as 

Next hop server NHS

Next hop clients NHC

   NHS act as a mapping agent store all registered mapping.

   NHC sent a query to NHS if they want to communicate with another NHC

   NHS reply with specific info to NHC

NHRP Messages

   NHRP Registration request

Spoke registered with public IP and tunnel IP to NHS.

Required to build spoke to hub tunnel.

  NHRP Request

Spoke request for NBMA and tunnel IP of other spokes.

Required to build spoke to spoke tunnels

  NHRP Redirect

Required to build spoke to spoke tunnel.

NHS answers with spoke to spoke info in it.

 

DMVP operation

 

   A permanent      IPSec tunnel has been build between all Spoke and hub location

   Hub router is the NHRP server      (NHS) and all the spoke will register to NHS with their public IP address

   When a spoke needs to send a      packet to another location it queries the NHRP server for the real public IP of the destination spoke.

  After obtaining the target public IP the of spoke can initiate a dynamic IPSec tunnel with spoke.

  The spoke to spoke tunnel is      built over mGRE tunnels

   All the traffic from source to destination in went through the GRE tunnel are encrypted by IPSec protocol.

See the below sample diagram for the configuration of a DMVPN
