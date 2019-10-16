# ECS_CFT
Create Following resources in AWS using cloudformation:
    Create VPC with multiple subnets. 
    In that VPC create hello world service in AWS ECS with Application load balancer. 
    Make sure we autoscale based on CPU >20%  and make sure all instances running NTP service with EST timezone. 
    It should only accessible to rfc1918 address space. 
    Also this application need to be protected from DDOS attacks.
