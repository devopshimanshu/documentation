# Cloud NAT

## What is NAT?
**Network Address Translation (NAT)**

To access the Internet, one public IP address is needed, but we can use a private IP address in our private network. 

The idea of NAT is to allow multiple devices to access the Internet through a single pulic address.

To achieve this, the translation of a private IP address to a public IP address is required.

NAT is a process in which one or more local IP address is translated into one or more Global IP address and vice versa in order to provide Internet access to the local host.

Also, it does the translation of port numbers i.e. masks the port number of the host with another port number, in the packet that will be routed to the destination.

It then makes the corresponding entries of IP address and port number in the NAT table.

NAT generally operates on a router or firewall.

## Network Address Translation (NAT) working - 
Generally, the border router is configured for NAT i.e the router which has one interface in the local (inside) network and one interface in the global (outside) network.

When a packet traverse outside the local(inside ) network, then NAT converts that local (private) IP address to a global (public) IP address. 

When a packet enters the local network, the global (public)IP address is converted to a lcoal(private) IP address.

If NAT runs out of addresses, i.e., no address is left in the pool configured then the packets will be drpoped and an Internet Control Message Protocol (ICMP) host unreachable packet to the destination is sent.

## NAT Types:
1. Static NAT
2. Dynamic NAT
3. Port Address Translation (PAT)


# What is CLoud NAT in GCP?
Cloud NAT (network address translation) lets certian resources without external IP address create outbound connections to the internet.

Cloud NAT provides outgoing connectivity for the following resources:
- Compute Engine machines
- Private GKE
- CLoud Run instance
- Cloud Function instance
- App Engine standard environment instance


Cloud NAT is a region resource.

We just need to create a Cloud NAT in a region and all the instances can use it automatically.

# Benefits of Cloud NAT:
- Security
- Avalibility
- Scalability
- Perfomance


For More we can dive into 

# Cloud NAT rules

# Organisation policy



# Refenece
[NAT](https://www.geeksforgeeks.org/network-address-translation-nat/)
[Cloud NAT Docs](https://cloud.google.com/nat/docs)
[Cloud NAT Overview](https://cloud.google.com/nat/docs/overview)
