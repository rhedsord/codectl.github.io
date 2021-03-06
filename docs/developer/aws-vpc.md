---
layout: default
title: AWS Development VPC
parent: Platform DevKit
nav_order: 1
---

# [Sparta AWS Devkit VPC]
## Requirements
  - Provisioned [AWS SSH Key]
  - Valid AMI (and ami ids) for RHEL8 & CoreOS
                                                                             
-----------------------------------------------------------------------------
### Build Devkit VPC
  1. Clone Repo
```
  git clone --branch 4.6.1 https://github.com/CodeSparta/devkit-vpc.git && cd devkit-vpc
```
  2. Configure variables
```
  vi variables.tf
```
  4. Exec into Konductor IaC Runtime
```
  ./devkit-build-vpc.sh -vv -e aws_cloud_region=us-gov-west-1 \
      -e aws_access_key=xxxxxxxxxxxxx -e aws_secret_key=XXXXXXXXXXXXXXXXX
```
-----------------------------------------------------------------------------

### Destroy Devkit VPC
  X. Exececute Teardown Script
```
  ./devkit-destroy-vpc.sh
```

[Sparta AWS Devkit VPC]:https://github.com/CodeSparta/devkit-vpc
[AWS SSH Key]:https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#how-to-generate-your-own-key-and-import-it-to-aws
