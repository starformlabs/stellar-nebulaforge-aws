# NebulaForge minimal-ephemeral

This [CloudFormation](https://aws.amazon.com/cloudformation/) template deploys the [stellar/quickstart](https://github.com/stellar/docker-stellar-core-horizon) 
docker image running in a non-validating, ephemeral configuration connected to the test network. The deployment uses
a single VPC subnet in a single availability zone.

Stellar-core, Horizon and Postgres are all running in the same container on the same EC2 instance. [AWS ECS](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)
is used to manage the containers, and EC2 Autoscaling will replace the instance if it crashes or is terminated but 
there is never more than one instance running at a time.


### Billable Resources
The template creates a myriad of resources but the majority of them do not attract charges. You **will** be billed for 
the following resources:
 - A single [EC2 instance](https://aws.amazon.com/ec2/pricing/on-demand/) using the instance type you select
 - [Cloudwatch logs](https://aws.amazon.com/cloudwatch/pricing/)
 - [EC2 data transfer](https://aws.amazon.com/ec2/pricing/on-demand/#Data_Transfer)


**Disclaimer:** While we attempt to provide useful and up to date information, you are responsible for your own AWS 
account and the resources that you are charged for. Always be vigilant about doubling checking to ensure that the 
resources used are what your expect.


### Prerequisites
Aside from having an AWS account, the only prerequisite for deploying this template is that you have an EC2 key pair. 
The key pair allows you to SSH into your instance. If you don't already have a key air you can [create one via the console](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair)
or upload an existing one.


### Launch
Click the links below to launch this configuration in the AWS region of your choice. If your desired region is
not listed just copy one of the urls and edit the region accordingly.

| AWS Region | Short name | | 
| -- | -- | -- |
| US East (N. Virginia) | us-east-1 | [Launch Stack :rocket:](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=stellar-minimal-ephemeral&templateURL=https://s3.amazonaws.com/public.starformlabs.io/nebulaforge/aws/minimal-ephemeral/master.yaml)
| US West (Oregon) | us-west-1 | [Launch Stack :rocket:](https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=stellar-minimal-ephemeral&templateURL=https://s3.amazonaws.com/public.starformlabs.io/nebulaforge/aws/minimal-ephemeral/master.yaml)
| EU (Ireland) | eu-west-1 | [Launch Stack :rocket:](https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=stellar-minimal-ephemeral&templateURL=https://s3.amazonaws.com/public.starformlabs.io/nebulaforge/aws/minimal-ephemeral/master.yaml)
| EU (Frankfurt) | eu-central-1 | [Launch Stack :rocket:](https://console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/new?stackName=stellar-minimal-ephemeral&templateURL=https://s3.amazonaws.com/public.starformlabs.io/nebulaforge/aws/minimal-ephemeral/master.yaml)
| Asia Pacific (Tokyo) | ap-northeast-1 | [Launch Stack :rocket:](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=stellar-minimal-ephemeral&templateURL=https://s3.amazonaws.com/public.starformlabs.io/nebulaforge/aws/minimal-ephemeral/master.yaml)
| Asia Pacific (Mumbai) | ap-south-1 | [Launch Stack :rocket:](https://console.aws.amazon.com/cloudformation/home?region=ap-south-1#/stacks/new?stackName=stellar-minimal-ephemeral&templateURL=https://s3.amazonaws.com/public.starformlabs.io/nebulaforge/aws/minimal-ephemeral/master.yaml) 




