How do I ...
============

... set up a computer for Development?
--------------------------------------

Most of the following points will happen in the Terminal app.

1. Check if Command Line Tools are installed on your computer:
  1. Type `gcc` in Terminal
  2. If not installed proceed with the instructions for installation
2. Install [Sass](http://sass-lang.com/) (necessary for legacy projects)
3. Install [Compass](http://compass-style.org/install/) (necessary for legacy projects)
4. Download and install [Node.js](https://nodejs.org/en/)
5. Install [gulp](http://gulpjs.com/)
6. Install [grunt](http://gruntjs.com/getting-started) (necessary for legacy projects)
7. Download and install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
8. Download and install [Vagrant](https://www.vagrantup.com/downloads.html)
9. Download and install [SequelPro](https://sequelpro.com/)

... start a new project ?
--------------------------

Use [Fosterkit](https://www.npmjs.com/package/fosterkit).


... update Vagrant ScotchBox MySQL Server?
------------------------------------------

1. `wget http://dev.mysql.com/get/mysql-apt-config_0.8.0-1_all.deb`
2. `sudo dpkg -i mysql-apt-config_0.8.0-1_all.deb`
  1. Select option 1
  2. Select mysql-5.7-*
  3. OK
3. `sudo apt-get update`
4. `sudo apt-get install mysql-server`
5. `sudo mysql_upgrade -u root -p`
  1. Password: `root`

... update database URL records using SequelPro
--------------------------------------------

1. Paste the script bellow into SequelPro Query tab

  ```sql
  UPDATE wp_options SET option_value = replace(option_value, 'http://olddomain.com', 'http://newdomain.com') WHERE option_name = 'home' OR option_name = 'siteurl';

  UPDATE wp_posts SET guid = replace(guid, 'http://olddomain.com','http://newdomain.com');

  UPDATE wp_posts SET post_content = replace(post_content, 'http://olddomain.com', 'http://newdomain.com');

  UPDATE wp_postmeta SET meta_value = replace(meta_value, 'http://olddomain.com', 'http://newdomain.com');
  ```

2. Change the DB prefix (`wp_`) to match the current DB prefix.
3. Change **olddomain.com** with the actual DB domain name and **newdomain.com** with the domain you want to change into.
4. Select the whole script with `CMD+A`.
5. Click **Run selection**.

... update WP user's password using SequelPro
---------------------------------------------

1. Paste the script bellow into SequelPro Query tab

  ```sql
  UPDATE wp_users SET user_pass= MD5('enter-your-new-password-here') WHERE ID = 1;
  ```

2. Change the DB prefix (`wp_`) to match the current DB prefix.
3. Type in a new password between the quotes of the MD5 function.
4. Change the ID with the ID of the user you're trying to update the password for.
5. Select the whole script with `CMD+A`.
6. Click **Run selection**

... increase files size limit upload on PHP server
--------------------------------------------------

1. SSH into the server then `sudo nano /etc/php/7.0/fpm/php.ini`
2. Paste the following snippet at the end of the file

  ```
  upload_max_filesize = 64M
  post_max_size = 64M
  max_execution_time = 300
  ```
