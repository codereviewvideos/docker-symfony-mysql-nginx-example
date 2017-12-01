# docker-symfony-mysql-nginx-example
An example of Docker with Symfony, nginx, and MySQL

## Instructions for use

``` language-shell
git clone https://github.com/codereviewvideos/docker-symfony-mysql-nginx-example.git
cd docker-symfony-mysql-nginx-example

# docker user will run as www-data, a member of the www-data group
sudo chown -R $(whoami):1000 app

# bring up the environment
# this creates a ./volumes directory in the project root
make dev

# we need to sort out some permissions still, so down the environment momentarily
docker-compose down

# make the required permissions change to the php volume
sudo chown -R 1000:1000 volumes/php

# bring the environment back up
make dev

# get a terminal session open to the php container
docker-compose exec php /bin/bash
```

From here, you should be able to `composer install`:

```
www-data@49454f3566f0:~/dev$ composer install
Cannot create cache directory /var/www/.composer/cache/repo/https---packagist.org/, or directory is not writable. Proceeding without cache
Cannot create cache directory /var/www/.composer/cache/files/, or directory is not writable. Proceeding without cache
Loading composer repositories with package information
Installing dependencies (including require-dev) from lock file
Package operations: 38 installs, 0 updates, 0 removals
  - Installing doctrine/lexer (v1.0.1): Downloading (100%)         
  - Installing doctrine/annotations (v1.2.7): Downloading (100%)         
  - Installing twig/twig (v1.34.4): Downloading (100%)         
  - Installing symfony/polyfill-util (v1.4.0): Downloading (100%)         
  - Installing paragonie/random_compat (v2.0.10): Downloading (100%)         
  - Installing symfony/polyfill-php70 (v1.4.0): Downloading (100%)         
  - Installing symfony/polyfill-php56 (v1.4.0): Downloading (100%)         
  - Installing symfony/polyfill-mbstring (v1.4.0): Downloading (100%)         
  - Installing symfony/symfony (v3.3.6): Downloading (100%)         
  - Installing symfony/polyfill-intl-icu (v1.4.0): Downloading (100%)         
  - Installing psr/simple-cache (1.0.0): Downloading (100%)         
  - Installing psr/log (1.0.2): Downloading (100%)         
  - Installing psr/link (1.0.0): Downloading (100%)         
  - Installing psr/container (1.0.0): Downloading (100%)         
  - Installing psr/cache (1.0.1): Downloading (100%)         
  - Installing fig/link-util (1.0.0): Downloading (100%)         
  - Installing doctrine/inflector (v1.1.0): Downloading (100%)         
  - Installing doctrine/collections (v1.3.0): Downloading (100%)         
  - Installing doctrine/cache (v1.6.2): Downloading (100%)         
  - Installing doctrine/common (v2.6.2): Downloading (100%)         
  - Installing jdorn/sql-formatter (v1.2.17): Downloading (100%)         
  - Installing doctrine/doctrine-cache-bundle (1.3.0): Downloading (100%)         
  - Installing doctrine/dbal (v2.5.13): Downloading (100%)         
  - Installing doctrine/doctrine-bundle (1.6.8): Downloading (100%)         
  - Installing doctrine/instantiator (1.0.5): Downloading (100%)         
  - Installing doctrine/orm (v2.5.6): Downloading (100%)         
  - Installing incenteev/composer-parameter-handler (v2.1.2): Downloading (100%)         
  - Installing composer/ca-bundle (1.0.7): Downloading (100%)         
  - Installing sensiolabs/security-checker (v4.1.1): Downloading (100%)         
  - Installing sensio/distribution-bundle (v5.0.20): Downloading (100%)         
  - Installing sensio/framework-extra-bundle (v3.0.26): Downloading (100%)         
  - Installing monolog/monolog (1.23.0): Downloading (100%)         
  - Installing symfony/monolog-bundle (v3.1.0): Downloading (100%)         
  - Installing symfony/polyfill-apcu (v1.4.0): Downloading (100%)         
  - Installing swiftmailer/swiftmailer (v5.4.8): Downloading (100%)         
  - Installing symfony/swiftmailer-bundle (v2.6.3): Downloading (100%)         
  - Installing sensio/generator-bundle (v3.1.6): Downloading (100%)         
  - Installing symfony/phpunit-bridge (v3.3.6): Downloading (100%)         
paragonie/random_compat suggests installing ext-libsodium (Provides a modern crypto API that can be used to generate random bytes.)
doctrine/doctrine-cache-bundle suggests installing symfony/security-acl (For using this bundle to cache ACLs)
sensio/framework-extra-bundle suggests installing symfony/psr-http-message-bridge (To use the PSR-7 converters)
monolog/monolog suggests installing aws/aws-sdk-php (Allow sending log messages to AWS services like DynamoDB)
monolog/monolog suggests installing doctrine/couchdb (Allow sending log messages to a CouchDB server)
monolog/monolog suggests installing ext-amqp (Allow sending log messages to an AMQP server (1.0+ required))
monolog/monolog suggests installing ext-mongo (Allow sending log messages to a MongoDB server)
monolog/monolog suggests installing graylog2/gelf-php (Allow sending log messages to a GrayLog2 server)
monolog/monolog suggests installing mongodb/mongodb (Allow sending log messages to a MongoDB server via PHP Driver)
monolog/monolog suggests installing php-amqplib/php-amqplib (Allow sending log messages to an AMQP server using php-amqplib)
monolog/monolog suggests installing php-console/php-console (Allow sending log messages to Google Chrome)
monolog/monolog suggests installing rollbar/rollbar (Allow sending log messages to Rollbar)
monolog/monolog suggests installing ruflin/elastica (Allow sending log messages to an Elastic Search server)
monolog/monolog suggests installing sentry/sentry (Allow sending log messages to a Sentry server)
Generating autoload files
> Incenteev\ParameterHandler\ScriptHandler::buildParameters
Creating the "app/config/parameters.yml" file
Some parameters are missing. Please provide them.
database_host ('%env(MYSQL_HOST)%'): 
database_port ('%env(MYSQL_PORT)%'): 
database_name ('%env(MYSQL_DATABASE)%'): 
database_user ('%env(MYSQL_USER)%'): 
database_password ('%env(MYSQL_PASSWORD)%'): 
mailer_transport (smtp): 
mailer_host ('%env(MAILER_HOST)%'): 
mailer_user ('%env(MAILER_USER)%'): 
mailer_password ('%env(MAILER_PASSWORD)%'): 
mailer_port ('%env(MAILER_PORT)%'): 
mailer_encryption (ssl): 
mailer_auth_mode (login): 
secret ('%env(SECRET_KEY)%'): 
> Sensio\Bundle\DistributionBundle\Composer\ScriptHandler::buildBootstrap


> Sensio\Bundle\DistributionBundle\Composer\ScriptHandler::clearCache

 // Clearing the cache for the dev environment with debug                       
 // true                                                                        

                                                                                
 [OK] Cache for the "dev" environment (debug=true) was successfully cleared.    
                                                                                

> Sensio\Bundle\DistributionBundle\Composer\ScriptHandler::installAssets

 Trying to install assets as relative symbolic links.

 -- -------- ---------------- 
     Bundle   Method / Error  
 -- -------- ---------------- 

                                                                                
 [OK] All assets were successfully installed.                                   
                                                                                

> Sensio\Bundle\DistributionBundle\Composer\ScriptHandler::installRequirementsFile
> Sensio\Bundle\DistributionBundle\Composer\ScriptHandler::prepareDeploymentTarget
www-data@49454f3566f0:~/dev$ 
```

You will only need to do the permissions changes once. After this / subsequent development sessions, just run `make dev`.

