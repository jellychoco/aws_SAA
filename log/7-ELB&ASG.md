# ELB & ASG

1. Scalability & High Availability

   - Scalability means that an application / system can handle greater loads by adapting
   - There are two kinds of scalability
     1. Vertical Scalability
     2. Horizontal Scalability (= elasticity)
   - _Scalability is linked but diffrent to high availability_

2. Vertical Scalability

## ELB

- Load Balances are servers that forward traffic to multiple servers(e.g, EC2 Instances) downstream

1. Why use a lb?

   - spread load across multiple downstream instances
   - Expose a single point of access (DNS) to your application
   - Seamlessly handle failures of downstream instances
   - Do regular health checks to your instances
   - Provide SSL termination (HTTPS) for your websites
   - High availability across zones
   - Separate public traffic from private traffic

2. Healthy Checks

   - The health check is done on a port and a route

3. Types of load balancer on AWS

- type of load balancer
  1. Classic Load Balancer (2009, aka CLB): HTTP, HTTPS, TCP, SSL
  2. Application Load Balancer (2016, aka ALB): HTTP, HTTPS, Websocket
  3. Network Load Balancer (2017, NLB): TCP, TLS, UDP
  4. Gateway Load Balancer (2020, GWLB): operates at layer 3 (network protocol) - IP Protocol
- Some load balancers can be setup as private or public ELBs

4. Tips
   - Not allow instance access directly, block instance security group, setup security group to elb


### 

1. Application Load balancer
   - layer 7 http only
   - load balancing to multiple http applications across machines(target groups)
   - lb to multiple app on the same machine (containers)
   - Support for http/2 and websocket
   - Support redirects (from http to https as a example)
   - Routing tables to diffrent target groups:
   - Routing based on path in URL 
   - ALB are a great fit for micro services & container-based app (docker & ecs)
   - Has a port mapping feature to redirect to a dynamic port in ECS
   - CLB vs ELB
     - CLB need per app
     - ELB need only one 
   ![alt text](../assets/11.png)

2. Target Groups
   - EC2 instances (can be managed by Auto Scaling Group) - http
   - ECS tasks 
   - Lambda functions
   - IP addresses - must be private IPs
   - ALB can route to multiple target groups
   - Health checks are at the target group level
  