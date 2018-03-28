# Instruction to create local wordpress development enviroment usign Docker

# Prerequisite
To have the best output please try your best to prepare as close as possible enviroment as I used this make this happen.
Last time I test it is 2018/3/27

* macOS Sierra (Version 10.12.6)
* Docker version 17.12.0-ce
* docker-compose version 1.18.0
* WordPress version 4.9.4
* Bacis knowledge about Docker command


# Step 1 Backup your production site.
I used WPEngine to host my wordpress site, and they have easy way to back up your production site.
![alt text](https://github.com/YukiKuroshima/wordpress-docker/blob/master/doc/Screen%20Shot%202018-03-27%20at%209.40.28%20PM.png)
Click "Back up now" and you will get confirmation email.

# Step 2 Get your content
Go to the back up page in wp engine.

Select your back up point. Your docker container is going to use this content.
![alt text](https://github.com/YukiKuroshima/wordpress-docker/blob/master/doc/Screen%20Shot%202018-03-27%20at%209.40.28%20PM.png)

Click "Download ZIP" and select "Full backup"
![alt text](https://github.com/YukiKuroshima/wordpress-docker/blob/master/doc/Screen%20Shot%202018-03-27%20at%2010.13.12%20PM.png)
You will get the download link to the email you typed in couple of minutes.
Download that and keep it where you can find easily. You will need it in the next step.

# Step 3 Get database dump
Wordpress keeps your post data, user data, etc in the MySQL.
You will need the SQL dump file to initialize your wordpress container.
To do it, we are going to use the WordPress plug in called "All-in-One WP Migration"
Get it in your live site (WordPress site that you want to containerlize)
![alt text](https://github.com/YukiKuroshima/wordpress-docker/blob/master/doc/Screen%20Shot%202018-03-27%20at%2010.19.10%20PM.png)

Please follow the next step carefully.
Activate All-in-One WP Migration and go to the export page from the side bar.
Click "Advanced options" and select followings:
* Do not expoert media library (files)
* Do not expoert themes (files)
* Do not expoert must-use plugins (files)
* Do not expoert plugins (files)

Click "Export To" and select "File".
Download the file and keep it where you can find it. You will need it later in this tutorial.

# Step 4 Prepare your wordpress container
Clone this repo in the directory you want to keep your wordpress files.
For example, you can do following.
```
mkdir wordpress-docker
cd wordpress-docker
git clone https://github.com/YukiKuroshima/wordpress-docker.git
```
You will see following files in the project.

![alt text](https://github.com/YukiKuroshima/wordpress-docker/blob/master/doc/Screen%20Shot%202018-03-27%20at%2010.48.41%20PM.png)

You only need `docker-compose.yaml` and `wp-content`. You can delete rest of files if you want.


# Step 5 Migrate the database
