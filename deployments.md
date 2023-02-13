# Deployments

## Basic Concepts

**Article:** [What Django Deployment is Really About](https://james.walters.click/what-django-deployment-is-really-about.html)

Covers the 4 main concerns of Django deployments:
1. Static Files
2. Database
3. WSGI Server
4. Web Server

## Deployment Checklist

Django official [Deployment Checklist](https://docs.djangoproject.com/en/4.1/howto/deployment/checklist/).

```python manage.py check --deploy```

## Hosts

### Platform as a Service (PaaS)

The provider configures a web server for you.

PaaS *"allows developers to build, test, run and scale applications more quickly."* ([source](https://www.parallels.com/blogs/ras/iaas-vs-paas/))

- [PythonAnywhere](https://www.pythonanywhere.com/) has a free-tier ([Tutorial by DjangoGirls](https://tutorial.djangogirls.org/en/deploy/))
- [Heroku](https://www.heroku.com/) used to be very popular but have recently removed their free tier. ([Tutorial by MeetGor](https://mr-destructive.github.io/techstructive-blog/django-deploy-heroku/))
- [Railway](https://railway.app/) is relatively new and hyped. Reportedly quick and easy to set up and has a free tier. ([Video Tutorial by Dennis Ivy](https://www.youtube.com/watch?v=do0otUW7454))
- [AWS Elastic Beanstalk](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/Welcome.html) allows developers to *"quickly deploy and manage applications in the AWS Cloud without having to learn about the infrastructure that runs those applications."*


### Virtual Machines

Cheaper but has a longer setup process. Expect to spend more time setting up and maintaining the environment.

- [Linode](https://www.linode.com/)