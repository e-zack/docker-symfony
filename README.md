# PHP symfony environment
This is a complete stack for running Symfony 4 into Docker containers using docker-compose tool.

# Installation
First, clone this repository:
```html
$ git clone https://github.com/e-zack/docker-symfony.git
```
Let’s start Docker !
```html
$ docker-compose build
```

Then, run:
```html
$ docker-compose up -d
```

How Docker work ?

I will not explain how Docker because this is not the subject, but for keep going this post you have to understand two things :
* Each container is one linux distribution with one component
* Each container have one root access by default

So when you execute this :
```html
$ docker exec -it -u sf4_mysql bash
```

You are right now in the mysql container as root user. You can explorer this container as you want ;)

# Symfony here we are

Now we know how use Docker, so let’s go to the PHP one and not as root, but as user : dev
```html
$ docker exec -it -u dev sf4_php bash
```
Now you are inside the php container with dev user and we have to get Symfony. Just to test, launch a php -v in this container. ;)

So let’s go to your home :
```html
cd /home/wwwroot/sf4
```

Installation of Symfony4 with composer
```html
$ composer create-project symfony/skeleton temp-folder ^4.4
```

or : for last version of Symfony
```html
$ composer create-project symfony/skeleton temp-folder 
```

When it’s done, we will get the project to the root path.
```html
$ cp -Rf /home/wwwroot/sf4/temp-folder/. .
$ rm -Rf /home/wwwroot/sf4/temp-folder
```

Launch in your browser :
```html
http://localhost
```

Congratulation !! You can now easily start your new Symfony project. If you look inside the docker-compose.yml file you can see all acces as you need, for example the mysql access :
```html
MYSQL_ROOT_PASSWORD: root
MYSQL_DATABASE: sf4
MYSQL_USER: sf4
MYSQL_PASSWORD: sf4
```


