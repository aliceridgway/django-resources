# AWS Elastic Beanstalk

[AWS Elastic Beanstalk](https://docs.aws.amazon.com/elastic-beanstalk/index.html) is a **Platform as a Service (PaaS)** to deploy applications without in-depth knowledge of the infrastructure that runs them.

## Terminology

### Application Version
> *refers to a specific, labeled iteration of deployable code for a web application.*

It points to an AWS S3 object that contains deployable code.

### Environment
> *A collection of AWS resources running an application version.*

### Environment Tier
The environment tier determines what resources your environment will provision.

For example, the [web server environment tier](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts-webserver.html) includes an **Elastic Load Balancer (ELB)**, an Auto Scaling group and at least one **Elastic Compute Cloud (EC2)** instance.

A [worker environment tier](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features-managing-env-tiers.html) are used to offload long running tasks (think [Celery](https://docs.celeryq.dev/en/stable/getting-started/introduction.html)). The process is run on an EC2 instance and requests to the worker are queued using **SQS (Simple Queue Service)**.

### Environment Configuration

The collection of settings that define how the environment behaves.

### Platform

Comprises of:
- Operating system
- Programming language runtime
- Web server
- Application server
- Elastic Beanstalk components


