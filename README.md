# Multi-Region Disaster Recovery Architecture in AWS
The architecture consists of two AWS regions (us-east-1 and us-east-2) where the web application is hosted using EC2 instances with Auto Scaling and Elastic Load Balancer (ELB). The primary database (MySQL RDS) is deployed in the first region and continuously replicates data to a cross-region read replica in the second region.
AWS Route 53 is used for traffic routing and failover. If the primary region fails, Route 53 redirects traffic to the secondary region, ensuring business continuity.
