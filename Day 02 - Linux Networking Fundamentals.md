# 100 Days of DevOps Challenge

# Day 02 - Linux Networking Fundamentals

## Introduction

Today I continued my **100 Days of DevOps Challenge** by learning Linux networking fundamentals.

Networking is an important part of DevOps because applications, servers, containers, cloud services, and CI/CD systems need to communicate with each other.

Understanding Linux networking helps with:

* Server connectivity
* Troubleshooting network issues
* AWS EC2 communication
* Docker networking
* Kubernetes networking
* Application connectivity
* DNS troubleshooting
* Security and firewall configuration

---

# 1. What is Computer Networking?

Networking allows different systems to communicate with each other.

For example:

```text
Client
   |
   ↓
Internet
   |
   ↓
Load Balancer
   |
   ↓
Application Server
   |
   ↓
Database Server
```

In a DevOps environment, understanding how traffic moves between these components is very important.

---

# 2. IP Address

An IP address identifies a device or server on a network.

Example:

```bash
192.168.1.10
```

There are two common types:

```text
IPv4
IPv6
```

Private IP addresses are commonly used for communication inside private networks.

Public IP addresses allow systems to communicate over the internet.

---

# 3. Check IP Address

The `ip` command is commonly used to check network information.

```bash
ip addr
```

You can also use:

```bash
ip a
```

This displays network interfaces and their IP addresses.

Example:

```text
eth0
192.168.1.10
```

---

# 4. Check Network Interfaces

To display network interfaces:

```bash
ip link
```

This helps identify interfaces such as:

```text
eth0
ens33
lo
```

The `lo` interface is the loopback interface.

---

# 5. Check Routing Table

The routing table determines where network traffic should be sent.

Use:

```bash
ip route
```

Example:

```text
default via 192.168.1.1 dev eth0
```

The default route is used when there is no more specific route available.

---

# 6. Test Network Connectivity

## ping

`ping` is used to test connectivity between systems.

```bash
ping google.com
```

You can also test an IP address:

```bash
ping 8.8.8.8
```

If the server receives replies, network connectivity is generally working.

---

# 7. DNS

DNS stands for:

**Domain Name System**

DNS converts domain names into IP addresses.

For example:

```text
google.com
      ↓
IP Address
```

Instead of remembering an IP address, users can use a domain name.

---

# 8. Check DNS Resolution

Use:

```bash
nslookup google.com
```

Another useful command is:

```bash
dig google.com
```

These commands help troubleshoot DNS-related problems.

---

# 9. Check Open Ports

A port identifies a specific network service.

Common ports include:

| Port | Service                 |
| ---- | ----------------------- |
| 22   | SSH                     |
| 80   | HTTP                    |
| 443  | HTTPS                   |
| 3306 | MySQL                   |
| 5432 | PostgreSQL              |
| 8080 | Common application port |

To check listening ports:

```bash
ss -tuln
```

This is useful when troubleshooting whether an application is listening on the expected port.

---

# 10. Test a Specific Port

The `nc` command can be used to test connectivity to a port.

Example:

```bash
nc -zv 192.168.1.10 80
```

This can help determine whether port 80 is reachable.

For example:

```text
Connection to 192.168.1.10 80 port [tcp/http] succeeded
```

---

# 11. curl

`curl` is commonly used to communicate with web servers and APIs.

Example:

```bash
curl https://example.com
```

To check only HTTP headers:

```bash
curl -I https://example.com
```

This is very useful for testing web applications and APIs.

---

# 12. wget

`wget` can be used to download files from the internet.

Example:

```bash
wget https://example.com/file.zip
```

It is commonly used on Linux servers when downloading packages, scripts, or application files.

---

# 13. traceroute

`traceroute` shows the network path between your system and a destination.

Example:

```bash
traceroute google.com
```

On some Linux distributions, you may need to install it first.

Traceroute is useful for troubleshooting where network traffic is failing or experiencing delays.

---

# 14. hostname

The `hostname` command displays the server hostname.

```bash
hostname
```

To display detailed hostname information:

```bash
hostnamectl
```

Example:

```text
Static hostname: devops-server
```

Hostnames are useful for identifying servers in large environments.

---

# 15. Check Network Configuration

A useful command for checking network-related information is:

```bash
ip addr
```

You can also check the default route:

```bash
ip route
```

And DNS configuration:

```bash
cat /etc/resolv.conf
```

---

# 16. Important Network Configuration Files

Some important Linux networking files include:

```text
/etc/hosts
/etc/resolv.conf
```

## /etc/hosts

The `/etc/hosts` file can map hostnames to IP addresses locally.

Example:

```text
192.168.1.20 app-server
192.168.1.30 db-server
```

Now the hostname can be used instead of the IP address.

---

# 17. Practical DevOps Troubleshooting Example

Imagine an application running on an AWS EC2 Linux server is not accessible.

The first step is to check whether the server has network connectivity.

### Step 1: Check IP

```bash
ip addr
```

### Step 2: Check Route

```bash
ip route
```

### Step 3: Test Internet Connectivity

```bash
ping 8.8.8.8
```

### Step 4: Test DNS

```bash
nslookup google.com
```

### Step 5: Check Listening Ports

```bash
ss -tuln
```

### Step 6: Test Application

```bash
curl http://localhost:8080
```

### Step 7: Test Remote Port

```bash
nc -zv <server-ip> 8080
```

This step-by-step approach helps identify whether the problem is related to:

```text
Network
DNS
Port
Application
Firewall
Security Group
```

---

# 18. Linux Networking Commands Learned

| Command                | Purpose                             |
| ---------------------- | ----------------------------------- |
| `ip addr`              | Show IP addresses                   |
| `ip link`              | Show network interfaces             |
| `ip route`             | Show routing table                  |
| `ping`                 | Test connectivity                   |
| `nslookup`             | Check DNS resolution                |
| `dig`                  | Query DNS information               |
| `ss`                   | Check network connections and ports |
| `curl`                 | Test HTTP/API connectivity          |
| `wget`                 | Download files                      |
| `nc`                   | Test network ports                  |
| `traceroute`           | Trace network path                  |
| `hostname`             | Show hostname                       |
| `hostnamectl`          | Manage hostname                     |
| `cat /etc/hosts`       | View local hostname mappings        |
| `cat /etc/resolv.conf` | Check DNS configuration             |

---

# 19. Why Networking is Important for DevOps

Networking knowledge is required when working with:

* AWS VPC
* EC2
* Load Balancers
* Security Groups
* Docker
* Kubernetes
* Jenkins
* Web Servers
* Databases
* APIs
* CI/CD pipelines

For example, when an application cannot connect to a database, a DevOps Engineer needs to understand IP addresses, ports, DNS, routing, and firewall rules to troubleshoot the issue.

---

# 20. Key Takeaways

From Day 2, I learned:

1. Basic Linux networking concepts
2. IP addresses and network interfaces
3. Routing and default gateways
4. DNS and hostname resolution
5. Network ports
6. Connectivity testing using ping
7. Port testing using nc
8. HTTP testing using curl
9. Checking listening services using ss
10. Basic network troubleshooting

These concepts will help me understand AWS networking, Docker networking, Kubernetes networking, and production troubleshooting.

---

# Day 2 Completed

## Linux Networking Fundamentals

Today I strengthened my Linux networking knowledge and learned how to troubleshoot basic connectivity, DNS, port, and application communication issues.

The next step is to continue building these fundamentals and connect them with real-world AWS and DevOps scenarios.

**Day 2 Completed — Learning DevOps one day at a time.**

---

## Tags

#DevOps #Linux #Networking #AWS #CloudComputing #DevOpsEngineer #CloudEngineer #LinuxCommands #100DaysOfDevOps
