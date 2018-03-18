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

More documentation to come...