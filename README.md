# Amazon EKS Cluster Deployment

## Overview

This template will help to implement the cluster deployment which is basically a technique for providing an integrated console for Kubernetes clusters. Cluster operators and application developers can use EKS as a single place to organize, visualize, and troubleshoot your Kubernetes applications running on Amazon EKS. The EKS console is hosted by AWS and is available automatically for all EKS clusters.


## Requirements

| Name      | Version |
| --------- | ------- |
| terraform | ~> 1.0  |

## Providers

| Name | Version |
| ---- | ------- |
| aws  | ~> 3.0  |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| aws_region | Name of AWS region in which you want to create resources | `string` | "" | yes |
| project | Name of the project | `string` | "" | yes |
| environment | Name of the application environment(dev/prod/qa) | `string` | "" | yes |
| username | Name of the user who is deploying the resources | `string` | "" | yes |
|cluster_version | the version of the ekS cluster |	string |"1.22"| yes|
|node_instance_type| the instance type of the worker nodes | `string`| ""| no |
fargate_memory | Required memory for the EKS task in Mib  | `number` | "" | yes |
| fargate_cpu | Required CPU units for the EKS tasks | `number` | "" | yes |
|self_managed_node_group| Node groups to automate lifecycle of nodes |  `string`| "2" | yes|
| vpc_id |VPC Id where the cluster is launched |  | `string` | "" | yes |
| subnet_ids | Private subnet id's to launch EKS clusters | `list(string)` | [""] | yes |
| health_check | health check grace period seconds | `number` | 60 | no |
| Security_Group | Security groups for the clusters  | `string` | 1 | yes |
| tls_certificate | this is different from EKS identity provider | `string` | 1 | yes |
| cluster_endpoint | Endpoint for your Kubernetes API server | `string` | 1 | yes |
| kms_key_id | The globally unique identifier for the key |  `string` | "" | yes |

## Output

 | Name             |      Description                  |     Type                    |

 | cluster_id | cluster id is created  | `string` |
 |cluster_endpoint | Endpoint for your Kubernetes API server is created | `string` |
 | cluster_status | Status of the EKS cluster. One of `CREATING`, `ACTIVE`, `DELETING`, `FAILED is shown | `string` |
 |cluster_primary_security_group_id| Cluster security group that was created by Amazon EKS for the cluster  | `string` |
 | kms_key_id | The globally unique identifier for the key is created | | `string` |
 | cluster_security_group_id| ID of the cluster security group  | `string` |
 | node_security_group_id | ID of the node shared security group | `string` |
 | cluster_iam_role_unique_id | Stable and unique string identifying the IAM role |  `string` |
 | eks_managed_node_groups | Map of attribute maps for all EKS managed node groups created  |  `string` |
 | self_managed_node_groups |  Map of attribute maps for all self managed node groups created | `string` |
 
 
 ## Initialize Terraform

To use the backend as S3 bucket, use command:

    terraform init -backend-config="bucket=BUCKET_NAME" -backend-config="region=AWS_REGION"

Instead of `BUCKET_NAME` & `AWS_REGION` write actual bucket name & aws region name. You have to create a S3 bucket for backend before using this command.




## Variable `rules`

Map of known application load balancer security group ingress rules.
The default value of variable `rules` is shown below:

                {
                    # HTTP
                    # alb_ingress_rule_name  =  [from port, to port, 'protocol', 'description']
                    http-80-tcp              =  [80, 80, "tcp", "HTTP Protocol"]
                    http-8080-tcp            =  [8080, 8080, "tcp", "HTTP Protocol"]

                    # HTTPS
                    # alb_ingress_rule_name  =  [from port, to port, 'protocol', 'description']
                    https-443-tcp            =  [443, 443, "tcp", "HTTPS Protocol"]
                }
   ### Prerequisites

- [terraform](https://learn.hashicorp.com/terraform/getting-started/install#installing-terraform)
- [aws-docs](https://docs.aws.amazon.com/eks/latest/userguide/getting-started.html)

1. Export backend variables
```
    export bucket=<bucket_name>
    export key=<key_name>
    export region=<bucket_region>
```

2. Add values infront of keys in terraform `vars.tfvars` file

                
                
                
                
                
                
                
                
                
                
                
 
 
 
 
 
 
 
 
 
























