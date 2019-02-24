# Deploying to AWS Elastic Beanstalk


## With RDS database

Run: 

    eb create -d -db.engine postgres  -db.size 5 --database.instance db.t2.micro --envvars DURING_RELEASE_RUN_MIGRATIONS=enabled,LANG=en_US.UTF-8,RACK_ENV=production,RAILS_ENV=production,RAILS_LOG_TO_STDOUT=enabled,RAILS_SERVE_STATIC_FILES=enabled,SECRET_KEY_BASE=`rake secret`

# When you've got a DB already setup

Run: 

    eb create --envvars DURING_RELEASE_RUN_MIGRATIONS=enabled,LANG=en_US.UTF-8,RACK_ENV=production,RAILS_ENV=production,RAILS_LOG_TO_STDOUT=enabled,RAILS_SERVE_STATIC_FILES=enabled,SECRET_KEY_BASE=`rake secret`,DATABASE_URL=postgres://some-db-url