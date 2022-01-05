# Pre-requisites
1. Ubuntu 20.x
2. Docker

# How to Run
1. Follow this great guide by Steve Bien-Aime, step by step: https://medium.com/@steve_64977/how-to-setup-a-docker-based-magento-2-3-local-development-environment-on-linux-in-no-time-57d28c7418fb
2. Clone this repo. ``` git clone https://github.com/tibzoy/dockerized-magento.git ```
3. CD to dockerized-magento and run ``` docker-compose -f docker-compose.yaml up --build -d ```
4. If you've reached the end of the tutorial, you should be able to browse a fresh Magento 2.4 install at http://local.magento.com


# My Steps (Magento Vanilla):
https://medium.com/@steve_64977/how-to-setup-a-docker-based-magento-2-3-local-development-environment-on-linux-in-no-time-57d28c7418fb

1. Pulled docker images based on Magento requirements here: https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html
``` docker pull [image] ```

2. Change the approriate image versions of the service components in the docker-compose.yml.

3. Created Dockerfile for PHP-FPM.

4. Docker compose up.
``` docker-compose -f docker-compose.yaml up --build -d ```

5. Fixed PHP-FPM error (No onigurumi package). (in case)
	Resolved By:  https://github.com/docker-library/php/issues/880

6. Install Magento
	``` composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition=2.4.3-p1 ```

  	If you met an error when running ```bin/magento setup:install``` : The default website is not defined. Set the website and try again.,
  	resolved by deleted env.php.

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
  Resolved by: Use image from https://hub.docker.com/r/magento/magento-cloud-docker-nginx 

8. Disabled 2FA

9. Fresh Magento is up!

