My Steps (Magento Vanilla):
https://medium.com/@steve_64977/how-to-setup-a-docker-based-magento-2-3-local-development-environment-on-linux-in-no-time-57d28c7418fb

1. Pulled docker images based on Magento requirements here: https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html

2. Change the approriate image versions of the service components in the docker-compose.yml.

3. Created Dockerfile for PHP-FPM.

4. Docker compose up.

5. Fix PHP-FPM error. 
	Resolved By: No onigurumi https://github.com/docker-library/php/issues/880


6. Install Magento
	composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition=2.4.3-p1

  	Error: The default website is not defined. Set the website and try again.
  	Resolved: Deleted env.php

  Used:
    bin/magento setup:install \
    --base-url=http://local.magento.com \
    --db-host=magento-local-env_db_1 \
    --db-name=magento2 \
    --db-user=magento2 \
    --db-password=magento2 \
    --admin-firstname=admin \
    --admin-lastname=admin \
    --admin-email=admin@admin.com \
    --admin-user=admin \
    --admin-password=admin123 \
    --language=en_US \
    --currency=PHP \
    --timezone=Asia/Manila \
    --use-rewrites=1 \
    --elasticsearch-host=magento-local-env_elasticsearch_1

7. Nginx serving default page
  Resolved: Used image from https://hub.docker.com/r/magento/magento-cloud-docker-nginx 

8. Disabled 2FA

9. Fresh Magento is up!

