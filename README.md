# Documentation For Cloud Coputing Web Server Infrastucture
---

## Requirements
- network.yml to create the subnets
- server.yml to create the servers with load balancer
- database.yml to create an EC2 to be used as a database
---
### Process to Complete
The three YAML scripts are templates to create the components that are going to be needed for the infrastrucure

- **netowrk.yml**: This creates a VPC for the applications which consists of 2 public and private subnets, each attached to a NAT Gateway to be able to access the internet. As well as route tables for all subnets which are seto f rules to determine where data packets traveling over the internet travels to.
- **servers.yml**: This creates a scaling group an da loadbalancer for the infrastructure. A scaling group is a group of of EC2 instances that share similar configurations, and the scaling policy is used to decide when to add or remove servers from the auto scaling group. Since running servers all day costs money, this will turn the servers off when they are not needed and turn them back on on demand. The servers will have subnet groups with an outbound and inbound traffic policies. The load balancer automatically distributes incoming application traffic accross multiple servers. Loadbalancers allow to scale the amount of servers needed thoughout the day. It requires a listen which is a process that checks for connection. As well as a target group which is a logical group of EC2 instances spannig accross numerous subnets in a given vpc.
- **database.yml**: The database is an EC2 instance with a VPC with a security group that has private subnets that way it cannot access the internet, just those that are allowed to access it. 
