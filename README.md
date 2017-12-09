# Rails Elastic Beanstalk Boilertemplate
This is Rails on Elastic Beanstalk boilertemplate.  
Rails new command here.  
```bash
$ bundle exec rails new -d mysql --skip-sprockets --skip-coffee --skip-turbolinks --webpack .
```

## Constitution
Rails 5.1 + webpacker + sidekiq(optional)  
**Do not support Docker**

### Services

- puma
- sidekiq(Optional)

## Ruby version
2.4.2

## Environment variables
See [.ebextensions/environmentvariables.config](.ebextensions/environmentvariables.config)

## Initialize EB
Run this:

1. Create EB application

```bash
$ eb init rails
```

2. Create a new environment

```bash
# DB connection fails for the first run
$ eb create production
$ eb create staging
```

3. Add data tier

Add RDS manually from the management console. And must to create rails database.

4. Set environment variables

Add environment variables manually from the management console.

- SECRET_KEY_BASE
- REDIS_URL
- RAILS_DATABASE_HOST
- RAILS_DATABASE
- RAILS_DATABASE_USER
- RAILS_DATABASE_PASSWORD

## Deployment instructions
Run this:

```bash
$ eb deploy production
$ eb deploy staging
```

## Delete environment
Run this:

```bash
$ eb terminate production
$ eb terminate staging
```

## For local environment
### Database initialization
Run this:

```bash
$ bundle exec rails db:create
$ bundle exec rails db:migrate
$ bundle ecec rails db:seed
```
