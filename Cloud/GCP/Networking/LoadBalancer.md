# Cloud Load Balancing
A Load Balancer distributes user traffic across multiple instances of your applications. By spreading the load, load balancing reduces the risk that your applications experience performace issues.

Cloud Load Balancer is a fully distributed, software-defined managed service. It isn't hardware-based, so you don't need to manage a physical load balancing infrastructure.

It supports 1 million + querries per second with consistent high performance and low latency.

Cloud Balancer Features:
- **Single anycast Ip address:** All you traffic for multiple instance will have a single Ip and help in failover for the unhealthy instance or unhealthy regions.

- **Software-defined load balancing:** Cloud Load Balancing is a fully distributed and software-defined managed service for all your trafic.

- **Seamless autoscaling:** Cloud Load Balancing can scale as your users and traffic grow, including easily headling huge, unexpected and instaneous spikes by diverting traffic to other regions in the world that can take traffic. 

Autoscaling does not require pre-warming: you can scale from zero to full traffic in a matter of seconds.

- **Layer 4 and Layer 7 load Balancing:** Layer 4 for TCP,UDP,ESP,or ICMP trafic. Layer 7 for HTTP header and the uniform resource identifier.

- **External and internal load Balancing:** external load Balancer for user reaching from internet and internal load balancer for clients which are inside the Google Cloud.

- **Global and regional load Balancing:** Distribute your load-balanced resources in signle or multiple regions, to terminate connections close to your users, and meet your high availability requirements.


# Seven Layers of Networking / OSI Model (Open System Interconnection Model):
- 


- **Advanced feature support:** Advances Features such as :
    - GLB supports IPv6
    - WebSockets
    - user-defined request headers
    - Integration with Cloud CDN for cached Content Delivery
    - Integeration with Cloud Armor to protect your infra from distributed denial-of-service(DDoS)attacks and other targeted application attacked

## Type of Load Balancers in GCP:
1. Global External HTTP(S) Load Balancing - 
2. External HTTP(S) Load Balancing (classic)
3. SSL Proxy Load Balancing
4. TCP Proxy Load Balancing
5. Regional External HTTP(S) Load Balancing
6. Internal HTTP(S) Load Balancing
7. Internal TCP/UDP Load Balancing
8. External TCP/UDP Network Load Balancing

## Underlying Technologies of Google CLoud Load Balancers:
- Google Front Ends (GFEs)
- Andromeda
- Maglev
- Envoy Proxy

| Load Balancer Type                            | Underlying Techonology |
| ----------------------------------------------| ---------------------- |
| Global external HTTP(S) load Balancer         | GFEs, Envoy |
| Global external HTTP(S) load Balancer(classic)| GFEs        |
| Regional external HTTP(S) load Balancer | Envoy, Maglev       |
| Internal HTTP(S) load Balancer | Andromeda, Envoy       |
| External TCP/UDP network Load Balancer | Maglev  |
| Internal TCP/UDP network Load Balancer | Andromeda  |
| TCP proxy load balancer | GFEs  |
| SSL proxy load Balancer | GFEs  |


Global | Regional
Type of traffic: UDP|TCP|HTTP(S) | ESP or ICMP





## Internal HTTP(s)Load Balancing:
This load balancer is built on the Andromeda network virtualization stack and is a managed service based on the open source Envoy proxy.

Provides internal proxy-based layer 7 application data.

We can specify the URL map as well as internal IP, That acts as the frontend to your backends.

## External HTTP(S) Load Balancing:
- Global External HTTP(S) load Balancer
- Global external HTTP(S) load Balancer (classic)
- Regional Extrenal HTTP(S) load Balancer
External load balancer are the load balancers which have public IP and split traffic on our backend servers.

## Internal TCP/UDP Load Balancing
Its a Load balancers which works on UDP/TCP traffic and as its a internal Load Balancer so ti doesn't have public IP and can not route traffic from outside or from internet.

## External TCP/UDP Network Load Balancing
Its same as that of Internet TCP/UDP load balancer but its facing internet traffic and have public IP.

## SSL Proxy Load Balancing
SSL proxy Load Balancing is a reverse proxy load balancer that distributes SSL traffic comming from the internet to virtual machine (VM) instances in your google Cloud VPC network.

When using SSL proxy Load Balancing for your SSL traffic, user SSL (TLS) connections are terminated at the load balancing layer, and then proxied to the closet available backend instances by using either SSL (recommended) or TCP. 

With the **Premium** Tier, SSL proxy load balancer can be used as **Global**.

With **Standart** Tier, SSL proxy load balancer will be **Regional**.

**InShort:**

In coming traffic ssl connection will break and ssl proxy laod balancer create a new ssl connection for further propogation.

[Example Image](https://cloud.google.com/load-balancing/images/ssl-lb-overview.svg)
[Reference Article Link](https://cloud.google.com/load-balancing/docs/ssl)

### Benefits:
- IPv6 termination
- Intelligent routing
- Better utilization of backend
- Certificate Management
- Security patching
- Support for the following well-known ports
    - 25
    - 43
    - 110
    - 143
    - 195
    - 443
    - 465
    - 587
    - 700
    - 993
    - 995
    - 1883
    - 3389
    - 5222
    - 5432
    - 5671
    - 5672
    - 5900
    - 5901
    - 6379
    - 8085
    - 8099
    - 9092
    - 9200
    - 9300
- SSL Policies
- Geographic control over when TLS is terminated
- Integration with Google CLoud Armor

## TCP Proxy Load Balancing
TCP proxy load balancing is a reverse proxy load balancer that distributes TCP traffic coming from the internet to virtual machine (VM) instances in your Google CLoud VPC network.

WHen using TCP Proxy Load Balancing , traffic coming over a TCP connection is terminated at the load balancing layer, and then forwarded to the closest available backend using TCP or SSL.

TCP Proxy Load Balancing lets you use a single IP address for all users worldwide. 

The TCP proxy load balancer automatically routes traffic to the backends that are closest to the user.

With **Premium** Tier, TCP Proxy Load Balancer can be configured as a **global load balancing service**.

With **Standard** Tier, TCP Proxy Load Balancer is configured **regionally**

**Benefits**

- IPv6 termination
- Intelligent routing
- Security patching
- Support for the following well-known TCP ports:
    - 25
    - 43
    - 110
    - 143
    - 195
    - 443
    - 465
    - 587
    - 700
    - 993
    - 995
    - 1883
    - 3389
    - 5222
    - 5432
    - 5671
    - 5672
    - 5900
    - 5901
    - 6379
    - 8085
    - 8099
    - 9092
    - 9200
    - 9300
- Integration with Google Cloud Armor

# Refenece
[Google Load Balancer Docs ](https://cloud.google.com/load-balancing/docs)
[Google Load Balancer Overview](https://cloud.google.com/load-balancing/docs/load-balancing-overview)

