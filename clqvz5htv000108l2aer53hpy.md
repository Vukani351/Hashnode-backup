---
title: "Never Used Symphony Before?"
seoTitle: "Creating Symphony API"
seoDescription: "Never used symphony before? me too. This is my first time using it to create a CRUD API and I recorded the process from installing php + symphony & my-SQL."
datePublished: 2024-01-02T06:34:41.155Z
cuid: clqvz5htv000108l2aer53hpy
slug: symphony-crud-api
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1717898749629/3f71930b-e075-4950-ad1e-ca830bc3b0c5.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1717900130052/e3b2793a-ef34-4c4b-994d-a5081acc4ddc.png
tags: php, crud-api, crud-operations, sumphony

---

# Documenting The Process To Creating CRUD API using Symphony

### Installing Symphony:

> [USING THIS GUIDE](https://symfony.com/doc/4.1/setup.html#start-coding)

* First installed [composer-setup.exe](https://getcomposer.org/download/).
    
> To be able to use it you must place it where you have installed PHP locally or use [XAMP](https://www.apachefriends.org/) installation folder.

> If you choose to use a manually installed PHP it means you have to edit the `php.ini` develop file and make a copy of it, then remove the **"-development"** in the file name.

* The installer will make recommendations on which items to turn on in the ini file, to do that just remove the **";"** before those items to uncomment the line.
 
* So before you can install Symfony you must run the command to allow scoop to do its thing:

### *RUN THESE COMMANDS ON THE POWERSHELL:*

```powershell
 Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
 # The above one is optional, needed to run a remote script the first time
 irm get.scoop.sh | iex
```

* After that run `scoop -help` to check if scoop is installed.
 
```sql
   scoop install main/symfony-cli
```

* When its done installing it will tell you "symfony-cli' (5.7.5) was installed successfully!".

* Use `symfony new --webapp my_project` to create a application

* Use `symfony new my_project` to create console, API or microservice.

## follow :

* Steps to create [symfony project](https://symfony.com/download)
    
* To create a skeleton project we in windows we run

```plaintext
 composer create-project symfony/website-skeleton my-project
```

* In mac I think we don't need the "composer" before "create...".
    
* cd into the project `cd projectName`.
    
* run `symfony server:start -d` to start the project.
    
## Adding DB to Project:

* [DB INTEGRATION GUIDE](https://symfony.com/doc/current/doctrine.html)
    
* I tried using the integrated terminal in VS Code but it did not work so this time around I am using cmd from File Explore.
    
* Ran the command \`\`\`composer require doctrine\`\`
    
* Realized I was having error with which php version the project wanted so I moved the project outside of the htdocs in XAMP folder to another folder and the command worked.
    
* To create a docker file for mysql on docker I used `./bin/console make:docker:database`.
    
* After trying different commands from the docs \`\`\`docker-compose exec database mysql -u root --password main\`\` actually works where, user is **root** and databases is **main**.
    
* After the terminal shows that I am in mysql I ran `show databases;` to test.

* When creating entities Doctren wants us to work with objects and properties not db models 'still need some clarity on this' & it uses the ORM to map the data to DB.
    
* To create db models i used `php ./bin/console make:entity`.
    
* Console was supposed to generate the entity with the repository in the project **src** folder but it only made the entity so I will try again n it should work this time.
    
* At this point we have entities but no database to write to, create an entity i had to first install the doctrine migrations bundle [Following](https://www.doctrine-project.org/projects/doctrine-migrations/en/3.4/reference/introduction.html) `composer require "doctrine/migrations"`
    
* and also run the command to add symfony config in yaml -&gt; `composer require symfony/yaml`
    
* Then I had to go to the [Configuration Page](https://www.doctrine-project.org/projects/doctrine-migrations/en/3.4/reference/configuration.html) and add the config...yaml file.
    
* After adding the migration config I changed the migration path to the projects one.
    
* Also on the same page you follow along on creating and populating the **migrations-db.php**
    
* The command `php ./vendor/bin/doctrine-migrations migrate` was failing and throwing a 'driver not found error', so I went to enable mysql on the Program Files -&gt; php.ini & the error changed to *"An exception occurred in the driver: SQLSTATE\[HY000\] \[2002\] No connection could be made because the target machine actively refused it".*
    
* After many attempts the main thing that helped was installing mysql on the machine and not using the one that is on docker because that connection was failing.
    
* So what's clear is docs commands starting with *doctrine* fail with some error based on how the project was generated but those starting with php ./vendor... eg `php ./vendor/bin/doctrine-migrations status` will work. size - 9w by 16 h

