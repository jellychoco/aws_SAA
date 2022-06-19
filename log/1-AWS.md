# 1. AWS CLOUD HISTORY


- 2004: First service is SQS
- 2006: SQS, S3 & EC2 
- skip 

# 2. AWS Regions


- AWS has Regions all around the world
- Names can be us-east-1 etc..
- A region is a cluster of data centers
- **Most Aws services are region-scoped**

# 3. How to choose an AWS Region?
  1. Compliance with data governance and legal requirements: data nver leaves a region without your explict permission

  2. Proximity to customers: reduced latency

  3. Available services within a region: new services and new features aren't available in every region

  4. Pricing: pricing varies region to region and is transparent in the service pricing page


# 4. AWS Availability Zones
- Each region has many availability zones
  - usually 3, min is 2, max is 6
  - example: 
    - ap-southeast-2a
    - ap-southeast-2b
    - ap-southeast-2c
  - Each availability zone is one or more discreate data centers with redundant power, networking, and connectivity
  - They're separate from each other, so that they're isolated from disaters 
  
# 5. AWS Points of Presence (Edge Locations)

- Amazon has 216 Points of Presence (205 Edge locations & 11 regional caches) in 84 cities across 42 countries
- Content is devliered to end users with lower latency