# terraform-aws-cloudfront-s3-website
Terraform 0.13.x and higher compatible module for creating a s3 static website with cloudfront distribution

The following resources will be created
  
  - S3 Bucket
  - Cloudfront distribution
  - Route53 record

  
Prerequisites:

  - Route 53 hosted zone for example.com
  - ACM certificate for *.example.com in us-east-1 region
  
### Example 1

    provider "aws" {
      region = "us-east-1"
    }
     
    module "cloudfront_s3_website" {
        source           = "twstewart42/cloudfront-s3-website/aws"
        version          = "1.2.0"
        hosted_zone      = "example.com"
        domain_name      = "test.example.com"
        aws_region       = "us-east-1"
    }

## Requirements

| Name | Version |
|------|---------|
| terraform | >= 0.13 |

## Providers

| Name | Version |
|------|---------|
| aws | n/a |
| aws.aws\_cloudfront | n/a |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| aws\_region | AWS Region to host S3 site | `string` | `"us-east-1"` | no |
| domain\_name | FQDN of cloudfront alias for the website - blog.site.com | `string` | n/a | yes |
| hosted\_zone | Root domain of website - site.com | `string` | n/a | yes |
| tags | Map of the tags for all resources | `map` | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| cloudfront\_dist\_id | n/a |
| website\_address | n/a |

### Credits
The original core 1.0.0 module was developed by [chgangaraju/terraform-aws-cloudfront-s3-website](https://github.com/chgangaraju/terraform-aws-cloudfront-s3-website)
