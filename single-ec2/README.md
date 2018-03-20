# NebulaForge single-ec2

This [CloudFormation](https://aws.amazon.com/cloudformation/) template deploys a [trio of docker images](https://github.com/starformlabs/stellar-nebulaforge-aws/tree/master/docker-images) 
running in a non-validating, ephemeral configuration connected to the test network. The deployment uses
a single VPC subnet in a single availability zone.

Stellar-core, Horizon and PostgreSQL are all running in separate containers on the same EC2 instance. [AWS ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)
is used to manage the container, and EC2 Autoscaling will replace the instance if it crashes or is terminated, but 
there is never more than one instance running at a time.

The main difference between this template and the quickstart is that we follow the best practice of splitting 
Core, Horizon and PostgreSQL into separate containers, and that logs are automatically sent to AWS CloudWatch
allowing user to review logs directly from a web browser.


## Prerequisites
Aside from having an AWS account, the only prerequisite for deploying this template is that you have an EC2 key pair. 
The key pair allows you to SSH into your instance. If you don't already have a key pair you can [create one via the console](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair)
or upload an existing one.


## Launch
Click the links below to launch this stack in the AWS region of your choice. If your desired region is
not listed, just copy one of the URLs and edit the region accordingly.

| AWS Region | Short name | | 
| -- | -- | -- |
| US East (N. Virginia) | us-east-1 | [Launch Stack :rocket:](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=stellar-single-ec2&templateURL=https://s3.amazonaws.com/public.starformlabs.io/nebulaforge/aws/single-ec2/master.yaml)
| US West (Oregon) | us-west-1 | [Launch Stack :rocket:](https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=stellar-single-ec2&templateURL=https://s3.amazonaws.com/public.starformlabs.io/nebulaforge/aws/single-ec2/master.yaml)
| EU (Ireland) | eu-west-1 | [Launch Stack :rocket:](https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=stellar-single-ec2&templateURL=https://s3.amazonaws.com/public.starformlabs.io/nebulaforge/aws/single-ec2/master.yaml)
| EU (Frankfurt) | eu-central-1 | [Launch Stack :rocket:](https://console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/new?stackName=stellar-single-ec2&templateURL=https://s3.amazonaws.com/public.starformlabs.io/nebulaforge/aws/single-ec2/master.yaml)
| Asia Pacific (Tokyo) | ap-northeast-1 | [Launch Stack :rocket:](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=stellar-single-ec2&templateURL=https://s3.amazonaws.com/public.starformlabs.io/nebulaforge/aws/single-ec2/master.yaml)
| Asia Pacific (Mumbai) | ap-south-1 | [Launch Stack :rocket:](https://console.aws.amazon.com/cloudformation/home?region=ap-south-1#/stacks/new?stackName=stellar-single-ec2&templateURL=https://s3.amazonaws.com/public.starformlabs.io/nebulaforge/aws/single-ec2/master.yaml)

## Cost
The template creates a number of resources but the majority of them do not attract charges. You *will* be billed for 
the following resources:
 - [A single EC2 instance](https://aws.amazon.com/ec2/pricing/on-demand/)
 - [CloudWatch Logs](https://aws.amazon.com/cloudwatch/pricing/)
 - [Data transfer](https://aws.amazon.com/ec2/pricing/on-demand/#Data_Transfer)

Any potential charges for data transfer will likely minimal or covered by the free teir.

**Disclaimer:** While we attempt to provide useful and up to date information, you are responsible for your own AWS 
account and the resources that you are charged for. Always be vigilant about doubling checking to ensure that the 
resources used are what your expect.
<br />
<br />

## Create Complete

Once the deployment is done the status will be CREATE_COMPLETE. Switch to the **Outputs** tab to see the relevant URLs
- The AutoScalingGroup link will take you to a page that has a direct link to the instance. You can use this to 
find the instance IP.
- The LogGroup link will take you to a CloudWatch page with separate log streams for core, horizon and postgres.
- The ECS link will show you information about the state of the cluster.

More documentation to come...