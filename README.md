- [What are the key considerations when writing highly scalable software components?](#what-are-the-key-considerations-when-writing-highly-scalable-software-components)
- [What are the key considerations when writing highly concurrent software components?](#what-are-the-key-considerations-when-writing-highly-concurrent-software-components)
- [From a security point of view what are some of the key configuration points that can really tighten up an organisation's internet presence?](#from-a-security-point-of-view-what-are-some-of-the-key-configuration-points-that-can-really-tighten-up-an-organisations-internet-presence)


# What are the key considerations when writing highly scalable software components?

Let's start by defining what scalable software means. Scalable software refers to applications or systems that can effectively handle increasing workloads, user demands, and data volumes without compromising performance or requiring a complete redesign.

When designing scalable, concurrent software components, the primary consideration is understanding the product's current and intended usage patterns. This insight helps prioritize which components need scaling efforts. Some factors to consider include:
- Read vs. write intensity of operations
- Load patterns (e.g., consistent or with periodic spikes)
- Specific high-load scenarios (e.g., sales events)

However, before scaling, it is useful to exhaust other performance optimization options to minimize added complexity. Consider: 
- Optimizing algorithms and data structures
- Improving database query efficiency by optimising the query or adding indexes
- Implementing caching mechanisms
- Asynchronous processing

Cost is an important aspect of selecting a solution to handle scale. You'd typically want to choose the least costly solution that also allows you to work most effectively. An example of where this is important is when thinking about using a managed cloud service (more costly but let's you focus more on development) or an unmanaged one.

If scaling by distributing your system is your chosen way to go, some strategies include:
- Using microservices to reduce the size of each part of your application.
- Horizontally scaling to reduce the load on a single component in the system. Also consider data partitioning if you have very large volumes of data. A load balancer may be required to direct traffic to the correct horizontally scaled service.
- Setting up auto scaling to detect and respond to load changes.

It is crucial to monitor your application with logs, alerts and metrics to understand usage patterns and resource utilisation so that you can prepare to scale rather than dealing with software failure before scaling.

# What are the key considerations when writing highly concurrent software components?

The main considerations when working with concurrent software are to make sure to have adequate logging to understand what your application is doing. Debugging without logging is difficult in a concurrent system as the timing of execution isn't deterministic.

Use of synchronisation mechanisms such as locks and atomic operations is advised to prevent race conditions and ensure data consistency. Testing would be beneficial here too.

# From a security point of view what are some of the key configuration points that can really tighten up an organisation's internet presence?

Some patterns to tighten up an organisation's internet presence are:
- Applying the principle of least privilege to not give an person or machine more access to system components than they need in case of a breach.
- Requiring strong passwords and multi factor authentication to login to company services.
- Keeping software used up to date to have the latest security vulnerabilities patched.
- Properly protecting secret data such as connection strings by storing them in a secure key management service like Azure Key Vault. To go further, consider provisioning managed identities when giving something access to a resource as this removes the need to store a secret key at all.
- Encrypting data sent over the internet by using TLS 1.3.
- Setting up firewall rules to lock down inbound and outbound traffic rules. E.g. You may require employees to access a resource only via a VPN so you can only permit the IP of the VPN to access the resource.
- Segmenting a network so that resources that don't need to be public aren't made public and so if a breach happens in one network, it is isolate to that network.
- Adequate monitoring and logging to detect abnormal behaviour so that it be can handled.
- Using web based headers in HTTP responses such as HSTS to enforce HTTPS in browser connections.