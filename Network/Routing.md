# Routing Fundamentals
## What is Routing ?
- **Routing** is the process that router determine the path that IP packets should take over a network to reach their destination.

- Router store routes to all of their known destination in a routing table.
- When router receives a packet, it looks in the routing table to find the best route to forward that packet.

## Method of Routing:
- `Dynamic Routing`: Routers use dynamic routing protocols(OSFP,...) to share routing information with each other automatically and build their routing tables.
- `Static Routing`: A network engineer manually configures routes on the router. 


## Hơw does Routing work? 
- A **route** tells the router: to send a packet to destination **X**, you should send the packet to `next-hop` **Y**(the next router in the path to the destination).
- If the destination is directly connected to the router (**connected route**), send the packet directly to the destination. Or, if the destination is the router's own IP address (**local route**), receive the packet for itself(don't forward it).
## Routing table:
- When you configure an IP address on an interface and enable the interface, two routes are automatically add to the routing table:
   - First is Connected Route (or **C** in the routing table). It is the route to the network connected to the interface.
      - For example: If the network interface's IP is **192.168.1.1./24** the route will be **192.168.1.0/24**
   - Second is Local Route (or **L** in the routing table). It is the route to the exact IP address configured on the interface.
      - For example: If the network interface's IP is **192.168.1.1./24** the route will be **192.168.1.1/32**         
- A **route matches** a destination if the packet's destination IP address is the part of the network specified in the route.
    - For example: a packet to **192.168.1.60** is matched by a route to **192.168.1.0/24** but not by a route to **192.168.0.0/24**
## Different between Router and Switch:
- If a router receives a packet and it doesn't have a route that matches the packet's destination -> It will **drop** the packet.


  -> This is different than swithes, which flood frames if they don't have a MAC table entry for the destination.

- If a router receives a packet and it has mutiple routes that match the packet's destination, it will use the **most specific**(the matching route with the longest prefix length) matching route to forward the packet.
  
  -> This is different than switches, which look for an exact match in the MAC address table to forward frames.
