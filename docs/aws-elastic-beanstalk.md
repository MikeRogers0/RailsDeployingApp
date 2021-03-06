# Deploying to AWS Elastic Beanstalk

## Install AWS CLI && EB CLI

    brew install awscli awsebcli

## Creating App

Create your application here https://eu-west-2.console.aws.amazon.com/elasticbeanstalk/home?region=eu-west-2#/applications

    eb use RailsDeployingApp

### With RDS database

Run: 

    eb create RailsDeployingApp-production --instance_type t2.small -db.engine postgres  -db.size 5 --database.instance db.t2.micro --envvars DURING_RELEASE_RUN_MIGRATIONS=enabled,LANG=en_US.UTF-8,RACK_ENV=production,RAILS_ENV=production,RAILS_LOG_TO_STDOUT=enabled,RAILS_SERVE_STATIC_FILES=enabled,SECRET_KEY_BASE=`rake secret`

### When you've got a DB already setup

Run: 

    eb create RailsDeployingApp-production --instance_type t2.small --envvars DURING_RELEASE_RUN_MIGRATIONS=enabled,LANG=en_US.UTF-8,RACK_ENV=production,RAILS_ENV=production,RAILS_LOG_TO_STDOUT=enabled,RAILS_SERVE_STATIC_FILES=enabled,SECRET_KEY_BASE=`rake secret`,DATABASE_URL=postgres://some-db-url

## Deploying

    eb deploy
