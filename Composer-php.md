## 1) The installation of Composer on a Linux server is simple and straightforward. All you have to do is download and install the Composer by executing the following command:

curl -sS https://getcomposer.org/installer | php

## 2) You need to make the ‘composer.phar’ file executable by running the following command :

chmod +x composer.phar

# 3) Run the following command to make Composer globally available for all system users:

mv composer.phar /usr/local/bin/composer

# 4) You can verify the installation by checking Composer version. Run the following command to confirm the Composer installation.

composer -V
