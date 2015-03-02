# Customized CodeIgniter
## Description
This is a Customized CodeIgniter Framework for my specific working environment. It is most likely to be deployed in OPENSHIFT environment but it does work at normal hosting envrionment, and it switches between 'OPENSHIFT' and 'NORMAL' environment automatically by determin whether there is an ['envrionmental variable'](https://developers.openshift.com/en/managing-environment-variables.html) OPENSHIFT_APP_NAME, if it does, then the:
* system and application path will be changed to OPENSHIFT_DATA_DIR;
* database is change to OPENSHIFT_MYSQL_DB_*;
* cache folder is changed to OPENSHIFT_TMP_DIR;
* encryption token is changeto OPENSHIFT_SECRET_TOKEN;
* etc.

## Current Components and Versions
* [CodeIgniter](https://github.com/bcit-ci/CodeIgniter) | [2.2.1 stable + security fixes](https://github.com/bcit-ci/CodeIgniter/tree/2.2-stable)
* [DataMapper](http://stensi.com/datamapper/index.html) | [1.6.0](http://stensi.com/datamapper/pages/download.html)
* [UIkit](http://getuikit.com) | [2.17.0](https://github.com/uikit/uikit/releases/download/v2.17.0/uikit-2.17.0.zip)
* [jQuery](http://jquery.com/) | [1.11.2](http://jquery.com/download/)

## OPENSHIFT Additional Environment Variables
For OPENSHIFT APP with provided MYSQL database, it does require a few [custom environment variables](https://developers.openshift.com/en/managing-environment-variables.html#custom-variables):
* OPENSHIFT_MYSQL_DB_CHARSET = 'utf8'
* OPENSHIFT_MYSQL_DB_COLLAT = 'utf8_unicode_ci'
* OPENSHIFT_MYSQL_DB_NAME = 'database_name'
* OPENSHIFT_MYSQL_DB_DRIVER = 'mysql'

these are just for the ease of change by SSH command without git push. You can change with your own flavor.

## Modified entries in application/config/config.php
In the application/config/config.php, there are some other OPENSHIFT environment variables used, please adjust it as you want. I will make a list of what I have changed later.

## OPENSHIFT ACTION HOOK
Together there is a 'post_deploy' [Action Hook](https://developers.openshift.com/en/managing-action-hooks.html), which is used for OPENSHIFT environment, it will:
* move the application forlder and system folder to OPENSHIFT_DATA_DIR/ci, leave the:
  * index.php,
  * .htaccess,
  * assets folder

at the OPENSHIFT_REPO_DIR. Modify it as you wish. And of course, the index.php is also adjusted (the path) automatically if it detects the OPENSHIFT environment.

## UIkit
I have been working with UIkit from [YOOtheme](http://yootheme.com) since the first day of its release and so far I love it. Currently I only and almost everytime use it, so here it is. I have not modified any thing with UIkit, it is a complete set of 'min' files of the current version I have, and I will update it regularly.

## jQuery
It is the main dependency of UIkit and possibly others. I will update it reqularly.

## Copyright, Licenses & Disclaimer
Generally:
* All orginal legal owner of the components included in this project has the ultimate copyright and please use according to their licenses and conditions.
* All scipts that I have written included in this project are licensed to any one, who would like to use it, freely and free of any charge.
* All programmes and scripts here in this project are provided 'as is', use at your own risk and I, personally, will not be held responsible for any issue caused by using the whole or part of this project.

Please follow the licenses and conditions within each file for proper usage.