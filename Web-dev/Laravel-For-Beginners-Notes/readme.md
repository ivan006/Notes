# Laravel web app development

- [Section 1. Install development tools (Line 30)](#1.)
	- [Chapter 1. Install development tools (Line 30)](#1.)
- Section 2. Use the dev tools
	- [2. Introduction (Line 378)](#2.)
	- [3. Database component (Line 414)](#3.)
	- [4. Routes (Line 531)](#4.)
	- [5. Controllers (Line 588)](#5.)
	- [6. Models (Line 634)](#6.)
	- [7. Views component (Line )](#7.)
- [13. Use common dev stratergies (Line )](#13.)
  - [8.1. /5.1. Intro](#8.1)
  - [8.2. /5.2. Forms](#8.2)
  - [8.3. /5.3. Coming soon](##)
  - [8.4. /5.4. Coming soon](##)



## <a name="1."></a>Chapter 1. Install development tools


### Table Of Content

- [Virtual Local Server (VLS)](#Virtual_Local_Server)
- [Package Installation Manager ](#Package_Installation_Manager)
- [IDE](#IDE)
- [Database Manager](#Database_Manager)
- [Laravel powered app](#1.5.)


### <a name="Virtual_Local_Server"></a>Virtual Local Server (VLS)

#### This VLS system comprises of 5 parts.
- VLS Terminal
- VLS Engine
- VLS Content Location
- VLS Configuration Manager
- VLS Configuration Package
- VLS Environment
#### VLS Terminal
- Intro
	- Purpose: An interface to the virtual server
	- Name: Git Bash
- Installation
	- [Git Bash](https://git-scm.com/download/win).
#### VLS Engine
##### Intro
- Purpose: Used to run the virtual server
- Name: VirtualBox
##### Installation
- [Virtual Box](https://www.virtualbox.org/wiki/Downloads) (then click "windows hosts").
- Then edit your environment variables:
  - Orientate yourself to `Control Panel\System and Security\System`
  - Click `Advanced System Settings` and `Environment Variables`
  - Click `User variables for Person > Path`
  - Edit `Variable value`
    - Add this to the beginning `C:\Program Files\Oracle\VirtualBox;`
#### VLS Content Location
- Make this folder: `c:/laravel-apps`
#### VLS Configuration Manager
##### Intro
- Purpose: Used to help configure our virtual server
- Name: Vagrant
##### Installation
- [Vagrant](https://www.vagrantup.com/downloads.html).
#### VLS Configuration Package (Known as a "Box")
##### Intro
- Purpose: Used to configure our virtual server so that it can facilitate the specified framework.
- Name: Laravel Homestead
##### Installation
- For Very Fast Connections:
  - The file is about a gig.
  - Open a new instance of Git Bash and run this `vargant box add laravel/homestead`.
  - When prompted enter `2` for virtualbox installation type.
- For Normal Connections:
  - Installer Downloading
    - The file is about a gig.
    - Go to https://app.vagrantup.com/boxes/search
    - Search for `Laravel` and choose Homestead by Laravel
    - Either click the latest version or a version you want (only version 6 and above is able to have it's PHP version switched, which will be necessary).
    - Then prepend the URL link with this `/providers/virtualbox.box`
  - Installation
    - Rename the downloaded file to `virtualbox.box`.
    - Use Git Bash to install it
      - By running this command `vagrant box add laravel/homestead file:///C:/Users/Ivan/Downloads/virtualbox.box`.
    - Download  [metadata_url](https://abbasharoon.me/metadata_url) (right click this link and say "save link as"), remove its file extension and move it to your newly formed folder           
    `%USERPROFILE%\.vagrant.d\boxes\laravel-VAGRANTSLASH-homestead`.
    - In this same location rename the directory named “0” to the same number as the version of the box that that you installed
      - E.g. `6.1.0`.
##### Uninstallation
- `vagrant box remove laravel/homestead --box-version=6.2.0`
- Configure the box number version to your case
#### VLS Environment
##### Installation
- Part 1 (ssh keys)
	- Open a new instance of Git Bash, locate yourself with `cd .ssh/` and the run `ssh-keygen -t rsa -b 4096 -C "your@email.com"` replace the email here with your email.
	- When prompted for more detail just click enter each time (without entering any details) until it says that the keys have been "saved".
- Part 2 (Homestead folder)
	- Open Git Bash, locate yourself with this command `cd c:`
	- Run this command `git clone https://github.com/laravel/homestead.git Homestead`.
	- From windows explorer run this file `C:\Homestead\init.bat`.
	- Homestead.yaml
	  - In this file `C:\Homestead\Homestead.yaml` configure this attributes
	     - folders:
		- \- map: `C:\laravel-apps`
- Part 3 (homestead-7 folder)
  - Orientate yourself to `cd c:/Homestead` and then run the command `vagrant up`
    - Note if you are not using the latest version of Homestead you might need to clarify that
	- In the `homestead.rb` file
		- Location: - `C:\Homestead\scripts`
		- Edit: Change the version number in this line `config.vm.box_version = settings['version'] ||= '>= 6.3.0'`
	- And in the `homestead.yaml` file in the folder `C:\Homestead`
  - If this doesn't work the first time restart Git Bash and try again.
  - When the first launch has complete run the command `vagrant halt`
##### Uninstallation (if ever you need to)
- Part 1 (homestead-7 folder)
	- Get environment ID by running `vagrant global-status` and checking the ID code of the specific environment
	- Run `vagrant destroy 1a1a1a1a` (replace `1a1a1a1a` with the environment ID)
- Part 2 (Homestead folder)
	- Delete the `Homestead` folder inside `C:`
- Part 3 (ssh keys)
	- Go to `%USERPROFILE%\.ssh`
	- Manually delete it's contents
##### Operation
- Please note: In later sections of this course you will be editing source code for that you will need to make sure Laravel Homestead is open and to save computer resources close it when your not working.
- Open - using Git Bash locate yourself with `cd c:/Homestead` and then run the command `vagrant up` (executing this may take a while).
- Close - using Git Bash locate yourself with `cd c:/Homestead` and then run the command `vagrant halt`
- Check status
  - This just tells you if the virtual machine is running or not.
  - Using Git Bash locate yourself with `cd c:/Homestead` and then run `vagrant global-status`.
- Provision
  - Orientate yourself to `cd c:/Homestead` then `vagrant up` then `vagrant provision` then if you want `vagrant halt`
- Troubleshoot
  - If at some point you get the message `No input file selected` either
    - Restart homestead
    - Provision homestead
### <a name="Package_Installation_Manager"></a>Package Installation Manager </summary>
- We will be using Composer

#### Installation
- Installation: [Composer](https://getcomposer.org/download/)
#### Operation
- Composer functions are used through a command line interface.
#### Extensions
##### Laravel Installer
- Add the globally available "create new Laravel project" command to composer
  - open a new instance of Git Bash and run `composer global require "laravel/installer"`.

### <a name="IDE"></a>IDE
- An IDE is just a souped-up code editor. The IDE we will use is called Atom. Alternatively we suggest Microsoft Visual Studio
- Core
	- Google `Atom`, download installer and install.
#### <a name="Plugins/Extra_Features"></a> Plugins/Extra Features
##### Custom Code Snippets
- Intro
  - Code Snippets enable you to create a custom library of commonly used code samples.
  - This means that instead of writing a full block of code (for instance `Hello Jack. How are you today?`) you can just use a shortcut (e.g. `greet` then tab key)
- Usage
  - Many IDEs support this either as a built-in extra feature or as an optional plugin (just search online for your IDE's variant)
  - If your using Atom
  - Atom Snippets comes as a built-in extra feature
  - In atom orient yourself to the snippets settings file with `File > Snippets`
  - At the bottom of the file add this code
  ```
    '.php':
    'Greeting for php':
    'prefix': 'greet'
    'body': 'Hello $1. How are you today?'
  ```
    - Line 1: Type of code
    - Line 2: Name
    - Line 3: Shortcut
    - Line 4: Sample
    - $1, $2.. etc: Is for the cursor position (press tab to go to the next position)
    - For multi lines samples wrap the code in two sets of these `'''`
  - To make multiple snippet for the same code type you must structure it like this
  ```
    '.php':
    'Greeting for php':
    'prefix': 'greet'
    'body': 'Hello $1. How are you today?'
    'Greeting for php2':
    'prefix': 'greet2'
    'body': 'Hello $1. How are you today2?'
  ```
##### Setup to work with `.blade.php`
- To make it work with `blade` file you must install the blade syntax highlighter plugin called `language-blade` (then restart Atom)
##### Blade Snippet Library
- This may also be useful (if your using Atom search for `blade-snippets`)
##### Laravel Snippets
- This may also be useful (if your using Atom search for `Laravel`  by Cronos87)

### <a name="Database_Manager"></a> Database Manager
- General: We will be using MySQL Workbench this is a MySQL tool which allows you to manage databases.
- Note: A homestead connection wont work if you have not launched your local server.
- Install: Download installer from here [https://www.mysql.com/products/workbench/](https://www.mysql.com/products/workbench/).
#### Configuration
##### Setup Connection
- General: Note that if this doesn't work the first time close the connection and try again.
- Launch MySQL Workbench and by default you will be on the welcome page which shows the message `Welcome to MySQL Workbench`
- Click the plus symbol in the page.
- In the popup configure these attributes
  - Connection Name: `Local_Server`
  - Connection Method: Standard TCP/IP over SSH
  - SSH Hostname: your SSH Hostname
    - To find out what your SSH Hostname is do this:
      - Launch vagrant
      - Check the load message for a field called `SSH address` the value here is your SSH Hostname. Copy it.
  - SSH Username: `vagrant`
  - SSH Password: click store in vault then enter `vagrant`
  - MySQL Hostname: `localhost`
  - Username: `homestead`
  - Password: click store in vault then enter `secret`
- Then your connection will be saved to the welcome page.
##### Reposition tools - Schemas tool bar
- Run the connection
- In the sidebar locate the schemas tool bar
- Click its expand/collapse toggler
- Now is will be nice and visible
##### Operations
- To open MYSQL WorkBench launch it from its launch icon.










### <a name="1.5."></a>Laravel powered app
#### Table Of Content


- [General](#General)
- [Source Code](#Source-Code)
- [Database](#Database)

#### <a name="General"></a>General

##### Helpfull links
- https://devmarketer.io/learn/setup-laravel-project-cloned-github-com/

##### Laravel Overview
- Laravel is something you install on an app by app basis.
- It determines the architecture of your apps source code and provides it with lots of useful prebuilt functions.

##### PHP artisan
- Other that all the fundamental mechanisms that we will cover in later sections you will also have access to a set of command line functions called PHP artisan.
- These commands are helpful and can assist you while you build your application.



#### <a name="Source-Code">Source Code</a>


##### Installation
- In Git Bash locate yourself using `cd c:/laravel-apps`
- Decide on your project name e.g. `fundamental-mechanisms-app` (this is the example name because in the next section we will be practicing using what we call fundamental mechanisms)
- Decide if you want the latest version or and older versions
  - For latest do this
     - Run `composer create-project --prefer-dist laravel/laravel`. And if you have the Laravel extension for composer you can even use `laravel new fundamental-mechanisms-app`
  - Or for old version do This
     - Run `composer create-project --prefer-dist laravel/laravel fundamental-mechanisms-app 5.2.29` for specific version (in this case version 5.2.29).
     - If you get an error try first restarting Git Bash.
##### Configurations
- Map it in Homestead
	- To do this you will need to update this file `Homestead.yaml`, which is located in either `C:\Homestead\resources\` or `C:\Homestead\`
	 - Configure these attributes
	    - sites:
	 - \- map: `fundamental-mechanisms-app.test`
	 - to: `/home/vagrant/code/fundamental-mechanisms-app/public`
	 - For multiple project running in parallel do This
	    - Duplicate the above mentioned set of attributes and configure like this
	    ```
		sites:
		    - map: fundamental-mechanisms-app.test
		      to: /home/vagrant/code/fundamental-mechanisms-app/public
		    - map: fundamental-mechanisms-app2.test
		      to: /home/vagrant/code/fundamental-mechanisms-app2/public
	    ```
- Map it in your host file
	 - Using windows explorer locate yourself to here `C:\Windows\System32\drivers\etc\`
	 - Temporarily move the `host` file to your desktop.
	 - Open the host file in a code editor and configure it so it's contents ends with (to run multiple projects duplicate one of these code lines and configure).
	 ```
	 192.168.10.10 laravel.test
	 192.168.10.10 homestead.test
	 192.168.10.10 fundamental-mechanisms-app.test
	 ```
	 - Move it back into it's original location `C:\Windows\System32\drivers\etc\`.
- Provision homestead
  - Run homestead - run `cd c:/Homestead` and then `vagrant up`
  - Run the command `vagrant provision`.

##### PHP version
- Check
	- Add this to your routes (see how in later sections) and
	```php
	  Route::get('/phpversion', function () {
	    echo phpversion();
	  });
	```
	- Then open the corresponding page in your browser
- Change
	- Open `Homestead.yaml`
	- Add and set a php field in your site configurations. The versions available to use are limited to "5.6", "7.0", "7.1", "7.2" and "7.3" ("7.3" is default)
	 ```
	   sites:
	 - map: fundamental-mechanisms-app.test
	   to: /home/vagrant/code/fundamental-mechanisms-app/public
	   php: "5.6"
	 ```
	 - Provision homestead - Orientate yourself to `cd c:/Homestead` then `vagrant up` then `vagrant provision` then if you want `vagrant halt`
##### Testing
- Run your local server. Open your browser and enter the URL   `fundamental-mechanisms-app.test/` and see if a page opens with the text "Laravel".
- After completion close Homestead - run `vagrant halt`
##### Patches
- Foreach loop error
	- Cause
	  - Software incompatibility: If you are running a version  of PHP that is higher than 7.1 with a version of Laravel that is lower than 5.6 you will get this error
	  - Test your PHP and Laravel versions, here's how
	    - Oriented yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
	    - Run `php artisan --version` and `php -v`
	- Fix
	  - Option 1
	    - Go to `vendor\laravel\framework\src\Illuminate\Database\Eloquent\Builder.php` (eloquent builder file)
	- Replace this: `$originalWhereCount = count($query->wheres);`
	- With this: `$originalWhereCount = is_null($query->wheres) ? 0 : count($query->wheres);`
	  - More info
	    - This error shows when you try to run certain types of foreach loops and looks like this `count(): Parameter must be an array or an object that implements Countable`
	    - See more at  https://stackoverflow.com/questions/48343557/count-parameter-must-be-an-array-or-an-object-that-implements-countable
	  - Option 2
	    - If your using Laravel version `5.2.29` revert your php version to `5.6`

#### <a name="Database">Database</a>
##### Installation
- Create new DB
	- Launch MySQL WorkBench then and open your server environments connection
	- Click on the "new schema" symbol and
	- Decide on a database name (we recommend using the same name as your app) `fundamental-mechanisms-app`.

##### Configurations
- Configure .env file
	- If using Ubuntu
	  - DB_HOST= `127.0.0.1`
	  - DB_DATABASE= `fundamental-mechanisms-app`
	  - DB_USERNAME= [your username]
	  - DB_PASSWORD= [your password]
	- If using Windows
	  - DB_HOST= `192.168.10.10`
	  - DB_DATABASE= `fundamental-mechanisms-app`
	  - DB_USERNAME= `homestead`
	  - DB_PASSWORD= `secret`
- A note on security
	- The database.php file (location in the `config` folder) is used to connect to the DB.
	- But since the database login info may be sensitive it is not kept in that file.
	- Rather there are two extra files: A `.env` file and a `.env.example` file.
	- The `.env` file is used to store the database logins which the database.php file can reference to make the connection.
	- This is so that when sharing your app with other people, say if they want to have their own implementation of your app, then you can ensure your databases security.
	- This is done by leaving the `.env` file out and getting the recipient to set up their own `.env` file as per there own database settings.
	- They will still have access to the `.env.example` file which they can use to see how to structure their `.env` file.

##### Testing
- Run `cd C:/laravel-apps/fundamental-mechanisms-app` then `php artisan tinker`
- Run
`DB::connection()->getPdo();`
- If it says Unknown database then your have failed to connect
- If it shows an array called `PDO` then you managed to connect.
- To re-test first exit and re-enter tinker by running `exit` and then `php artisan tinker`
- When your done run `exit`


## <a name="2."></a>Chapter 2. Introduction

### MVC
- MVC is a code organizational structure
	- It separates the execution script from the helpers scripts
	- The main execution script is in the letter "C", meaning controller, and the helper scripts are in the letter "M" and "V, model and view.
	- ![](https://raw.githubusercontent.com/ivan006/Study_Notes/master/Web-dev/Laravel-For-Beginners-Notes/MVC-pattern2.png)

### Overview of components
- Entity data components
	- Database -Storage
		- This stores the data
- Entity action components
	- A URL - Request
		- This requests the action, front end action component
	- A page - Response
		- This communicates the response after the rest of the action is executed, front end action component
	- A route - Request translator
		- This translates the action request, back end action component
	- A controller - Action
		- This executes the action, back end action component
	- A model - Set of query templates
		- These guide the parts of the action that interact with the database, back end action component
	- A view - Response template
		- These guide the parts of the action that generate the response, back end action component

### Databases vs File formats

- Similar to a file format - entities types store your data in a certain structure.
- Entity tools are what make up your app. Similar to desktop programs - entity tools are for opening your entities. Each one contains multiple action protocols. 

- In business storing information in entity types (and then using the entity type corresponding tool) does create rigidity but with rigidity comes enhanced performance.


### Controllers

#### Definition
 - A controller contains a set of controller methods
 - A controller method is the execution script for a entity type's action.

#### Location
They are stored in `C:\laravel-apps\fundamental-mechanisms-app\app\Http\Controllers` in a controller file together with the other controllers that are also associated with the same entity type.

#### Controller types
- Note: these are merely examples of controllers types there are in fact more
- Create entity
- Read entity
- Update entity
- Delete entity



### Models

####  Definition:
- A model contains your queries templates.
#### Location
- `C:/laravel-apps/fundamental-mechanisms-app/app`.



## <a name="3."></a>Chapter 3. Database component

### Table Of Content
- [Database](#Database)


### General
- Definition
  - A database is where we store our "raw data" which we can display into more easy to understand report like pages. The data can be considered as raw as it has no style yet added to it.


### Managing Tables - Using Migrations
#### General
- Definition: Migrations help you to create your db tables easier.
- You get two different types of migrations
  - Table migrations that are for creating entire tables with multiple columns
  - Column migrations for adding ad hoc columns to tables that are already created
- Migration files are located here: `C:\laravel-apps\fundamental-mechanisms-app\database\migrations`
- Migration files contain migration column action functions which basically specify the details of the columns your want to create
- Migration commands
  - Activate the migrations
    - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
    - Run `php artisan migrate`
  - Deactivate the migrations
    - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
    - Run `php artisan migrate:reset`
  - Deactivate recently activated migrations
    - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
    - Run `php artisan migrate:rollback`
  - Refresh all the migrations
    - Combing the effect of deactivating and then activating the migrations causes the tables to loose all their records.
    - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
    - Run `php artisan migrate:refresh`
  - Check the migrations activation status
    - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
    - Run `php artisan migrate:status`
- See more info here: [https://laravel.com/docs/5.6/migrations#columns](https://laravel.com/docs/5.6/migrations#columns)

#### Creating a table using a migration
- Try this out
- Determine the names and types
	- Determine the table's name
		- Make it use underscores for spaces and ends with an "s" (this will help to automatically associate it to a model) also if the model ends in `y` then it's table must end in `ies`
		- E.g. `type_a_entities`
	- Determine the field names and field data types (string or text etc.) of the tables data fields
		- E.g.
			- `data_field_a`
				- data type: `string`
			- `data_field_b`
				- data type: `string`
			- `data_field_c`
				- data type: `string`
- Generate file command
	- In Git Bash locate yourself to `C:/laravel-apps/fundamental-mechanisms-app`
	- Run `php artisan make:migration type_a_entities_m_table --create="type_a_entities"`
- Configure it
  - Open the migration file in a code editor. Locate the schema function in your migration's up method.
  - Add this to the `Schema::create` function
  ```php
      $table->string('data_field_a');
      $table->string('data_field_b');
      $table->string('data_field_c');
  ```
	- Note: when editing this be sure not to remove the default "id" (`$table->increments('id');`) and timestamps (`$table->timestamps();`) functions as they are best to keep.
- Generate the table
  - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
  - Run `php artisan migrate`

#### Create a column with a migration
- General: These allow you to add columns to tables without interrupting the tables content/records that are already created
- Example
	- We will practice this later
  - Setup
    - Create migration
      - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
      - Decide on a migration name.
      - Run `php artisan make:migration type_a_entities_m_column_data_field_d --table="type_a_entities"`
    - Add a column function to the migration
      - Open the migration file in a code editor.
      - Locate the schema function in your migration's up method
      - Here you will add a new line of code
      - For example
      ```php
        Schema::table('type_a_entities', function (Blueprint $table) {
            $table->integer('data_field_d')->unsigned();
        });
      ```
    - Add a column deletion function to the migration
      - Open the migration file in a code editor.
      - Locate the schema function in your migration's down method
      - Here you will add a new line of code
      - For example here I am adding two custom columns
      ```php
        Schema::table('type_a_entities', function (Blueprint $table) {
            $table->dropColumn('data_field_d');
        });
      ```
  - Use - Activate the migration

#### Deleting Migrations
- Unfortunately deleting a migration is quite hard
  - You cannot delete a migration without first deactivating it
  - Which you can do either by using
    - deactivate all migrations or by using
    - deactivate recent migrations
    - which will delete either all or some of your db content.  
  - After that you can delete the migration and then reactivate the migrations again.
  - If after that you try to create new migrations but get this error
  ```shell
  [ErrorException]
  include(blabla): failed to open stream: No such file or directory
  ```
  then solve it by running this in git bash `composer dump-autoload`


## <a name="4."></a> Chapter 4. Routes

### Table Of Content
- [Routes](#routes)
  - [Route Parameters](#Route-cont.-Route-Parameters)

### General
- Routes "request translators". This is because they link a URL with a controller.
- They are located in `C:\laravel-apps\fundamental-mechanisms-app\routes\web.php`

#### <a name="Check-All-Route-Details"></a> Check All Route Details
- Once you've created some routes you can check their details
- In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
- Run `php artisan route:list`

### Route anatomy
- Example
	- `Route::get('/a/create', 'TypeAEntity_Controller@MethodCreate');`.
	- In this case the URL is the word `/a/create` and the controller is called `MethodCreate` and is found inside a controller file called `TypeAEntity_Controller`
	- Try this out - bear in mind it wont work properly until you make a controller.

### Resourced route
- This creates not 1 but a set of routes.
- E.g. `Route::resource('/a/create', 'TypeAEntity_Controller');`
- This you use in accordance with a CRUD type controller (mentioned later) and note in the example only a controller file is mentioned.
- Check what routes you have made by checking all your route's details (see how here [Check All Route Details](#Check-All-Route-Details)).

### Non-separated action execution script
- Not separating your action execution script into a controller is possible but is discouraged as it is too disorganized.
```php
  Route::get('/a/read', function(){
    return "Hello world";
  });
```

### Routes Names
- Names can be used to abbreviate routes making it easier for developers to reference them.
- Basic Method
  - Add a bit of code to your route
  - E.g. ` Route::get('ExampleRoute/ExamplePart/ExamplePart', array('as'=>'Example.Route', function(){ return "Hello world!"; }));`
  - This gives this name `Example.Route` to this route `ExampleRoute/ExamplePart/ExamplePart`.
- CRUD Method
  - CRUD controller route by default have names defined. Check what they are by checking all your route's details (see how here [Check All Route Details](#Check-All-Route-Details)).


### <a name="Route-cont.-Route-Parameters"></a>Route Parameters
- General: Route parameters are variables are passed through the URL.
- Usefulness: The URL could have a number in it which reflects a the id number of a entity that you would like to see.
- Example:
	- In this case it's called `ExampleParameter`
	```php  
	  Route::get('/a/read/{ExampleParameter}', 'TypeAEntity_Controller@MethodRead');
	```
	- Try this out
		- bear in mind it wont work properly until you make a controller.


## <a name="5."></a> Chapter 5. Controllers

### Table Of Content

- [Basic Setup](#Basic-Setup)
- [Integration with Route Parameters](#Integration-with-Route-Parameters)

###  <a name="Basic-Setup"></a> Basic Setup

#### Set up a controller that is blank
- These are completely blank and must be made from scratch
- To create one locate yourself to `C:\laravel-apps\fundamental-mechanisms-app\app\Http\Controllers` and create a new php file, the name format should be camel case but e.g. `TypeAEntity_Controller.php`
- To avoid class name collisions we recommend ending your controller with `_Controller`

#### Set up a controller that is generated
- These come with the controller file's foundation code already in place
- To create one
	- Open Git Bash and locate yourself using `cd` command to `C:/laravel-apps/fundamental-mechanisms-app`
	- Run `php artisan make:controller TypeAEntity_Controller`
- Try this out
	- bear in mind it wont work properly until you make a controller.

#### Set up a controller that is resourced
- These come with the controller file's foundation code already in place and some commonly used controllers set up
- To create one
	- Open Git Bash and locate yourself using `cd` command to `C:/laravel-apps/fundamental-mechanisms-app`
	- Run `php artisan make:controller --resource TypeAEntity_Controller`, note the camel casing on the controller name.



### <a name="Integration-with-Route-Parameters"></a> Integration with Route Parameters
- Example:
  - Route
    - Name/parameters: Reuse `/a/read/{a}`
  - Controller method
    ```php
      public function MethodRead($a)
      {
        return "Hello ".$a."!";
      }
    ```
	- Try this out
		- Test using: `fundamental-mechanisms-app.test/a/read/Bob`.



## <a name="6."></a> Chapter 6. Models

### Table Of Content

- [Setup a model (Line 30)](#6.1.)
- [SQL models (Line 695)](#6.2.)
- [ORM models (Line 788)](#6.3.)
- [ORM models with relationships (Line 1069)](#6.4.)
- [Model testing environment (Roughly Line 1882)](#6.5.)
- [Models with accessors and mutators (Roughly Line 1930)](#6.6.)

###  <a name="6.1."></a> Setup a model

#### Setup a model
- Name
	- Rules
		- If you format the name of model and the table in a certain way the app will automatically associate them and you will not need to configure the table associator otherwise would will have to configure the table associator
		- Use a camel cased and singular version of the table name
- Table associator
	- To specify a table put this into your model's class `protected $table = 'table_name';`
- Generate file command
	- Using Git Bash locate yourself using  `cd C:/laravel-apps/fundamental-mechanisms-app`.
	- Then run `php artisan make:model TypeAEntity`
- Primary key associator
	- If your tables primary key is not "id" you will need to specify it.
	- To specify the primary key put this into your model class `protected $primaryKey = 'id';`
- De-restrict fields
	- Give the model some freedoms like allowing it to do multiple value inserts
	- By default a new entity can't be populated with content on inception this changes that
	- Choose the data fields that you want to be able to be populated on the entity's inception
	- Put this model configurator into your model's class
	```php
		protected $fillable = [
			'data_field_a',
			'data_field_b',
			'data_field_c',
		];
	```
- Importing model into the controller
  - Put this in the header of the associated controller file `use App\TypeAEntity;`



#### Setup a table-model pair
- General: Tables and models are rarely made independently so here's how to make them simultaneously.

##### Setup a table-model pair - The short way
- Try this out
- Generate the migration and model file with a single command
	- In Git Bash locate yourself to `C:/laravel-apps/fundamental-mechanisms-app`
	- Run `php artisan make:model TypeAEntity -m`
- Follow the `Creating a table using a migration` and `Setup a model` to finish setting them up except leave out the `generate file command` steps of course


##### Setup a table-model pair - The long way
- Follow the steps in `Creating a table using a migration`
- Follow steps in `Setup a model`

### <a name="6.2."></a>  SQL Models
- There are four types of database queries and the are abbreviated with "CRUD"
  - Create
  - Read
  - Update
  - Delete
- SQL means Structure Query Language
- SQL is a language for managing the data in a database.

#### Create (Insert)
- Try this out
- Route:
	- Name/parameters: Reuse `/a/create/{a}` parameters to use - swap to `$a`
- Controller method
	- Import the model - put `use App\TypeAEntity;` in the header of your controller
	- Here's the entire body of code
  ```php
		public function MethodCreate($a)
	  {
	    TypeAEntity::model_create($a, $a, $a);
	  }
  ```
	- Class/name/parameters: `TypeAEntity_Controller`->`MethodCreate` parameters to use - `$a`
	- And the script is:
	```php
		TypeAEntity::model_create($a, $a, $a);
	```
- Model method
	- Import the SQL functionality - put `use Illuminate\Support\Facades\DB;` in the header of your controller
	- Heres the entire body of code
	```php
		static function model_create($a, $b, $c)
    {
      DB::insert('insert into type_a_entities(data_field_a, data_field_b, data_field_c) values(?, ?, ?)', [$a, $b, $c]);
    }
	```
	- Class/name/parameters: `TypeAEntity`->`model_create` parameters to use - `$a, $b, $c`
	- The query is: `DB::insert('insert into type_a_entities(data_field_a, data_field_b, data_field_c) values(?, ?, ?)', [$a, $b, $c]);`
	- And model method type is: `static`
- URL example: `fundamental-mechanisms-app.test/a/create/hello`



#### Read
- Try this out
- Route:
	- Name/parameters: Reuse `/a/read/{a}`
- Controller method:
	- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodRead` parameters to use - `$a`
	- Script: `return "<pre>".var_dump(TypeAEntity::model_read($a))."</pre>";`
- Model method:
	- Class/name/parameters: `TypeAEntity`->`model_read` parameters to use - `$a`
	- Query: `return DB::select('select * from type_a_entities where data_field_a  = ?', [$a]);`
	- Model method type is: `static`
- URL example: `fundamental-mechanisms-app.test/a/read/hello`

#### Update
- Try this out:
- Route:
	- Name/parameters: `/a/update/{a}/{b}`
	- Associated controller method: `MethodUpdate`
- Controller method:
	- Class/name/parameters: `TypeAEntity_Controller`->`MethodUpdate` parameters to use - `$a, $b`
	- Script: `TypeAEntity::model_update($a, $b);`
- Model method:
	- Class/name/parameters: `TypeAEntity`->`model_update` parameters to use - `$a, $b`
	- Query `DB::update('update type_a_entities set data_field_a  = ? where id = ?', [$a, $b]);`
	- Model method type is: `static`
- URL example: `fundamental-mechanisms-app.test/a/update/bye/1`



#### Delete
- Try this out
- Route:
	- Name/parameters: `/a/delete/{a}`
	- Associated controller method: `MethodDelete`
- Controller method:
	- Class/name/parameters: `TypeAEntity_Controller`->`MethodDelete` parameters to use - `$a`
	- Script: `TypeAEntity::model_delete($a);`
- Model method:
	- Class/name/parameters: `TypeAEntity`->`model_delete` parameters to use - `$a`
	- Query `DB::delete('delete from type_a_entities where id = ?', [$a]);`
	- Model method type is: `static`
- URL example: `fundamental-mechanisms-app.test/a/delete/1`



### <a name="6.3."></a> ORM Models

#### Create types
##### Create record with one field value
- Try this out
- Route:
	- Name/parameters: reuse `/a/create/{a}`
- Controller method:
	- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodCreate`
	- Script:
	```php
		$var = new TypeAEntity;
		$var->data_field_a = $a;
		$var->data_field_b = $a;
		$var->data_field_c = $a;
		$var->save();
	```
- Model method:
	- Class/name/parameters: this one is all ready automatically made
- URL example: `fundamental-mechanisms-app.test/a/create/hello`

##### Create record with multiple field values
- Try this out
- Route:
	- Name/parameters: reuse `/a/create/{a}`
- Controller method:
	- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodCreate`
	- Script:
	```php
		TypeAEntity::create([
      'data_field_a'=>$a,
      'data_field_b'=>$a,
      'data_field_c'=>$a,
    ]);
	```
- Model method:
	- Class/name/parameters: this one is all ready automatically made
	- `De-restrict fields` as shown in previous section
- URL example: `fundamental-mechanisms-app.test/a/create/hello`



#### Read types
##### Find all records (and return a field's values)
- Try this out
- Route:
	- Name/parameters: reuse `/a/read` but now with no parameters
- Controller method:
	- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodRead` parameters to use - swap to none
	- Script:
	```php
		foreach (TypeAEntity::all() as $var) {
				echo $var->data_field_a."<br>";
		}
	```
- Model method:
	- Class/name/parameters: this one is all ready automatically made
- URL example: `fundamental-mechanisms-app.test/a/read`

##### Find all records and sort by date created
- Method 1
	- Try this out
	- Route:
		- Name/parameters: reuse `/a/read`
	- Controller method:
		- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodRead`
		- Script:
		```php
			foreach (TypeAEntity::latest()->get() as $var) {
					echo $var->data_field_a."<br>";
			}
		```
	- Model method:
		- Class/name/parameters: this one is all ready automatically made
	- URL example: `fundamental-mechanisms-app.test/a/read`
- Method 2
	- Try this out
	- Controller method:
		- Script:
		```php
      foreach (TypeAEntity::orderBy('id', 'desc')->get() as $var) {
          echo $var->data_field_a."<br>";
      }
		```
- Method 3
	- Try this out
	- Controller method:
		- Script:
		```php
      foreach (TypeAEntity::orderBy('id', 'desc')->get() as $var) {
          echo $var->data_field_a."<br>";
      }
		```
##### Find based on primary key (and return a field's values)
- Try this out
- Controller method:
	- Script:
	```php
		return TypeAEntity::find(5)->data_field_a;
	```

##### Find based on primary key (and return a field's values) or display an error
- Try this out
- Controller method:
	- Script:
	```php
		return TypeAEntity::findOrFail(1);
	```
##### Find based on other conditions (this example only works with soft-deleted items which comes later)
- Try this out
- Controller method:
	- Script:
	```php
		return TypeAEntity::withTrashed()->orderBy('id','desc')->get();
	```
##### Find based on other conditions (and return a field's values) or display an error
- Try this out
- Controller method:
	- Script:
	```php
		return TypeAEntity::where('id','<',50)->firstOrFail();
	```

#### Update types
##### Update based on primary key
- Try this out
- Route:
	- Name/parameters: reuse `/a/update/{a}` parameters to use - swap to `$a`
- Controller method:
	- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodUpdate` parameters to use - swap to `$a`
	- Script:
	```php
    $var = TypeAEntity::find(2);
    $var->data_field_a = $a;
    $var->save();
	```
- Model method:
	- Class/name/parameters: this one is all ready automatically made
- URL example: `fundamental-mechanisms-app.test/a/update/bye`

##### Update based on other conditions
- Try this out
- Controller method:
	- Script:
	```php
    TypeAEntity::where('id', 2)->where('data_field_a', $a)->update(['data_field_b'=>$a]);
	```
- URL example: `fundamental-mechanisms-app.test/a/update/hello`

#### Delete types
##### Delete method 1
- Note: this works only works when soft delete (a feature we will use later) is not activated
- Try this out
- Route:
	- Name/parameters: reuse `/a/delete/{a}`
- Controller method:
	- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodDelete`
	- Script:
	```php
    TypeAEntity::find($a)->delete();
	```
- Model method:
	- Class/name/parameters: this one is all ready automatically made
- URL example: `fundamental-mechanisms-app.test/a/delete/2`

##### Delete method 2
- Note: this works only works when soft delete is not activated
- Try this out
- Route:
	- Name/parameters: reuse `/a/delete/{a}`
- Controller method:
	- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodDelete`
	- Script:
	```php
    TypeAEntity::destroy($a);
	```
- URL example: `fundamental-mechanisms-app.test/a/delete/4`

##### Delete multiple
- Route:
	- Name/parameters: reuse `/a/delete/{a}/{b}` parameters to use - swap to `$a, $b`
- Controller method:
	- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodDelete` parameters to use - swap to `$a, $b`
	- Script:
	```php
    TypeAEntity::destroy([$a, $b]);
	```
- URL example: `fundamental-mechanisms-app.test/a/delete/5/6`

##### Delete multiple based on condition
- Route:
	- Name/parameters: reuse `/a/delete/{a}` but with only one parameter
- Controller method:
	- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodDelete` but with only one parameter
	- Script:
	```php
    TypeAEntity::where('data_field_a',$a)->delete();
	```
- URL example: `fundamental-mechanisms-app.test/a/delete/bye`



#### Soft delete types
##### General
- Records that are deleted softly are not properly deleted but they wont display when functions like `findAll` are run.
- Set up/activate
  - Model
    - Line 1
      - Put this at beginning of the `TypeAEntity` model file before the model class `use Illuminate\Database\Eloquent\SoftDeletes;`
    - Line 2
      - Put this at beginning of the `TypeAEntity` model class `use SoftDeletes;`
    - Line 3
      - Put this in the `TypeAEntity` model class - `protected $dates = ['deleted_at'];`
  - Database
    - Add a new `Create a column with a migration` called `type_a_entities_m_column_deleted_at` for the `type_a_entities` table.
    - Configure it    
      - In the  `up` method write `$table->softDeletes();`
      - In the `down` method write `$table->dropColumn('deleted_at');`

##### Soft Delete

- Route:
	- Name/parameters: reuse `/a/delete/{a}`
- Controller method:
	- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodDelete`
	- Script:
	```php
    TypeAEntity::find($a)->delete();
	```
- URL example: `fundamental-mechanisms-app.test/a/delete/7`


##### Read Items That Have Been Soft Deleted
- Find all records
	- Route:
		- Name/parameters: reuse `/a/read`
	- Controller method:
		- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodRead`
		- Script:
		```php
			foreach (TypeAEntity::withTrashed()->get() as $var) {
					echo $var."<br>";
			}
		```
	- URL example: `fundamental-mechanisms-app.test/a/read`
- Find all trashed
	- Route:
		- Name/parameters: reuse `/a/read`
	- Controller method:
		- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodRead`
		- Script:
		```php
			return TypeAEntity::onlyTrashed()->get();
		```
	- URL example: `fundamental-mechanisms-app.test/a/read`


##### Restore All Soft Deleted items
- Route:
	- Name/parameters: reuse `/a/update` but without parameters
- Controller method:
	- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodUpdate` parameters to use - swap to none
	- Script:
	```php
		TypeAEntity::onlyTrashed()->restore();
	```
- URL example: `fundamental-mechanisms-app.test/a/update`

##### Empty trash (While Soft Delete is Activated)
- This will properly delete all the items that are currently only soft deleted
- Route:
	- Name/parameters: Reuse `/a/delete` parameters to use - swap to none
- Controller method:
	- Class/name/parameters: Reuse `TypeAEntity_Controller`->`MethodDelete` parameters to use - swap to none
	- Script:
	```php
		TypeAEntity::onlyTrashed()->forceDelete();
	```
- URL example: `fundamental-mechanisms-app.test/a/delete`


### <a name="6.4."></a> ORM models with relationships

- [One to one relationship](#6.4.1.)
- [One to many relationships](#6.4.2.)
- [Many to many relationships](#6.4.3.)
- [Intermediate relationship (one to many)](#6.4.4.)
- [Polymorphic relationship (one to many)](#6.4.5.)
- [Polymorphic relationship (many to many)](#6.4.6.)



#### General
- This section covers ORM models methods. These are a type of model method that makes tables interrelated. The purpose of these relationships is to create super entities or networks of entities. For instance an entity can be primarily based on a record in one table but then also have supplementary info stored in a record of of a related table. There are many different types of relationships.
- ![](https://raw.githubusercontent.com/ivan006/Study_Notes/master/Web-dev/Laravel-For-Beginners-Notes/erd_2.png)
- Entities as real examples
	- type_a_entities -		posts	 
	- type_b_entities -		users	 
	- type_b_entity_type_c_entity -	role_user	 
	- type_c_entities -	roles	 
	- type_d_entities -		countries	 
	- type_e_entities - 	photos
	- type_f_entities -		tags and videos (but videos is faulty as has no associative table) 	 
	- type_f_entity_relation -		tag_relationships	 




#### <a name="6.4.1."></a> One to one relationship
##### Set up
- Set up for `TypeBEntity`
	- This will be `TypeAEntity`'s parent
	- Table
		- Setup a table-model pair - The short way (as previously demonstrated)
			- Model name `TypeBEntity`
			- Table name: this will be automatically configured
			- Table columns
			```php
			  $table->string('data_field_a');
			  $table->text('data_field_b');
			```
	- Model
		- `De-restrict fields` as shown in a previous section
	  - Configure relationship
			- Depending on how your foreign key has been named add either of the following model methods
		  - Method 1 - The manual foreign key specifier method
			  ```php
			    public function TypeAEntity(){
			      return $this->hasOne('App\TypeAEntity', 'type_b_entity_id');
			    }
			  ```
		    - Manually specify the foreign key in the `hasOne()` accessor's second parameter.
		    - Also note your if your parent model's primary key column is not `id` you can specify it in the third parameter.
		  - Method 2 - The automatic foreign key specifier method
				- This only works if the foreign keys column name is based on it's parent tables name and ends with `_id` and is singular (e.g. `type_b_entity_id`)
			  ```php
			    public function TypeAEntity(){
			      return $this->hasOne('App\TypeAEntity');
			    }
			  ```
		    - Add this in the model's class
		    - Note: the name of the controller (in this case `TypeAEntity`) doesn't matter as long as we refer to it in our route correctly, but it is easiest to base its name on the table it references.
	- Controller
		- `Set up a controller that is resourced` as previously demonstrated.
			- Name: `TypeBEntity_Controller`
			- Aliases: add this to the header
			```php
				use App\TypeBEntity;
				use App\TypeAEntity;
			```
	- Data
		- Create a record
			- Do as demonstrated in `Create record with multiple field values`
			- Route:
				- Name/parameters: `/b/create/{a}`
				- Associated controller method: `TypeBEntity_Controller@create`
			- Controller method:
				- Class/name/parameters: `TypeBEntity_Controller`->`create` parameters to use - `$a`
				- Script: just add this
				```php
					TypeBEntity::create([
			      'data_field_a'=>$a,
			      'data_field_b'=>$a,
			    ]);
				```
			- URL example: `fundamental-mechanisms-app.test/b/create/1`
		- Delete a record (only use if needed)
			- Do as demonstrated in `Delete method 2`
			- Route
				- Name/parameters: Reuse `/b/delete/{a}` parameters to use - `$a`
			- Controller method
				- Class/name/parameters: `TypeBEntity_Controller`->`destroy` parameters to use - `$a`
				- Script:
				```php
					TypeBEntity::destroy($a);
				```
				- URL example: `fundamental-mechanisms-app.test/b/delete/1`
- Set up for `TypeAEntity`
	- Database
		- Add a foreign key column
			- Edit the migration by adding this to your set of column functions
			```php
				$table->integer('type_b_entity_id')->unsigned();
			```
			- Then `refresh all the migrations` (as shown how in previous section)
	- Model
		- Add this in the model's class
		```php
		  public function TypeBEntity(){
		    return $this->belongsTo('App\TypeBEntity');
		  }
		```

##### Query child of parent entity
- Create
	- Route:
		- Name/parameters: `/b/read/a/create/{a}/{b}` parameters to use - `$a, $b`
	- Controller method:
		- Class/name/parameters: `TypeBEntity_Controller`->`showACreate` parameters to use - `$a, $b`
		- Script:
		```php
			TypeBEntity::findOrFail($a)->TypeAEntity()->save(
				new TypeAEntity([
					'data_field_a'=>$b,
					'data_field_b'=>$b,
					'data_field_c'=>$b,
					'type_b_entity_id'=>$b,
				])
			);
		```
	- URL example: `fundamental-mechanisms-app.test/b/read/a/create/1/1`
- Read
	- Route:
		- Name/parameters: `/b/read/a/read/{a}` parameters to use - `$a`
	- Controller method:
		- Class/name/parameters: `TypeBEntity_Controller`->`showAShow` parameters to use - `$a`
		- Script:
		```php
			return TypeBEntity::find($a)->TypeAEntity->all();
		```
	- URL example: `fundamental-mechanisms-app.test/b/read/a/read/1`
- Update
	- Route:
		- Name/parameters: `/b/read/a/update/{a}/{b}` parameters to use - `$a, $b`
	- Controller method:
		- Class/name/parameters: `TypeBEntity_Controller`->`showAUpdate` parameters to use - `$a, $b`
		- Script:
		```php
			$var = TypeAEntity::whereTypeBEntityId($a)->first();
			$var->data_field_a = $b;
			$var->save();
		```
	- URL example: `fundamental-mechanisms-app.test/b/read/a/update/1/2`
- Delete
	- Route:
		- Name/parameters: `/b/read/a/delete/{a}` parameters to use - `$a`
	- Controller method:
		- Class/name/parameters: `TypeBEntity_Controller`->`showADestroy` parameters to use - `$a`
		- Script:
		```php
			TypeBEntity::findOrFail($a)->TypeAEntity->forceDelete();
		```
	- URL example: `fundamental-mechanisms-app.test/b/read/a/delete/1`
  - Note: If soft delete is not enabled then you can replace `forceDelete()` with `delete()`

##### Query parent of child entity

- Read
	- Route:
		- Name/parameters: `/a/read/b/read/{a}` parameters to use - `$a`
	- Controller method:
		- Class/name/parameters: `TypeAEntity_Controller`->`showBMethodShow` parameters to use - `$a`
		- Script:
		```php
			return TypeAEntity::find($a)->TypeBEntity;
		```
	- URL example: `fundamental-mechanisms-app.test/a/read/b/read/1`

#### <a name="6.4.2."></a> One to many relationships
##### Set up
- Set up for `TypeBEntity`
	- Model
	```php
	  public function TypeAEntities(){
	    return $this->hasMany('App\TypeAEntity');
	  }
	```
  - After adding this you can remove the previous relationships method but it's not vital
  - The model method's name here is plural as it is a many relationship
- Set up for `TypeAEntity`
 	- Data
		- Create a second record
			- URL example: `fundamental-mechanisms-app.test/b/read/a/create/1/2`


##### Query children of parent entity
- Create
	- Route:
		- Name/parameters: Reuse `/b/read/a/create/{a}/{b}` parameters to use `$a, $b`
	- Controller method:
		- Class/name/parameters: Reuse `TypeBEntity_Controller`->`showACreate` parameters to use `$a, $b`
		- Script:
		```php
			TypeBEntity::findOrFail($a)->TypeAEntities()->save(
				new TypeAEntity([
					'data_field_a'=>$b,
					'data_field_b'=>$b,
					'data_field_c'=>$b,
					'type_b_entity_id'=>$b,
				])
			);
		```
	- URL example: `fundamental-mechanisms-app.test/b/read/a/create/1/1`
	- Note: Notice that the only change we are making to this controller is changing the queries model method
- Read
	- Route:
		- Name/parameters: Reuse`/b/read/a/read/{a}` parameters to use - `$a`
	- Controller method:
		- Class/name/parameters: Reuse `TypeBEntity_Controller`->`showAShow` parameters to use - `$a`
		- Script:
		```php
			foreach (TypeBEntity::findOrFail($a)->TypeAEntities as $var){
				echo $var->data_field_a. "<br>";
			}
		```
	- URL example: `fundamental-mechanisms-app.test/b/read/b/read/1`
- Update
	- Route:
		- Name/parameters: Reuse`/b/read/a/update/{a}/{b}` parameters to use - `$a, $b`
	- Controller method:
		- Class/name/parameters: Reuse `TypeBEntity_Controller`->`showAUpdate` parameters to use - `$a, $b`
		- Script:
		```php
			$var = TypeBEntity::findOrFail($a)->TypeAEntities()->whereId(1)->update([
				'data_field_a'=>$b
			]);
		```
	- URL example: `fundamental-mechanisms-app.test/b/read/a/update/1/2`
- Delete
	- Route:
		- Name/parameters: Reuse `/b/read/a/delete/{a}` parameters to use - `$a`
	- Controller method:
		- Class/name/parameters: Reuse `TypeBEntity_Controller`->`showADestroy` parameters to use - `$a`
		- Script:
		```php
			$var = TypeBEntity::findOrFail($a)->TypeAEntities()->whereId(1)->delete();
		```
	- URL example: `fundamental-mechanisms-app.test/b/read/a/delete/1`

#### <a name="6.4.3."></a> Many to many relationships

##### General

- This can be used by things like "tags" - where a post can have multiple tags and each tag can be used by multiple posts
- For this you need a relationships table.

##### Setup

- Data
	- `Refresh all the migrations` to have a clean start
- Set up `TypeCEntity`
  - Table
	 	- Setup method: `Setup a table-model pair - The short way`
    - Name: `TypeCEntity`
    - Columns
    ```php
      $table->string('name');
    ```        
	- Model
    - De-restrict fields
			```php
				'name',
			```
		- Relationships method
			- Class/name/parameters:
				- Name:
					- Rules: The name must be plural as it is a many relationship
					- E.g. `TypeCEntity`->`TypeBEntities`
			- Type: `public`
			- Query: 			
				- For if the relationships table and it's foreign keys columns are named according to the rules
				```php
				    return $this->belongsToMany('App\TypeBEntity');
				```
	- Data
		- Controller
			- `Set up a controller that is resourced` as previously demonstrated.
				- Name: `TypeCEntity_Controller`
				- Aliases: add this to the header
				```php
					use App\TypeCEntity;
				```
		- Create records (make 3)
			- Do as demonstrated in `Create record with multiple field values`
			- Route
				- Name/parameters: `/c/create/{a}` parameters to use - `$a`
			- Controller method
				- Class/name/parameters: `TypeCEntity_Controller`->`create` parameters to use - `$a`
				- Script:
				```php
					TypeCEntity::create([
						'name'=>$a,
					]);
				```
			- URL example: `fundamental-mechanisms-app.test/c/create/1`
		- Delete records (only use if needed)
			- Do as demonstrated in `Delete method 2`
			- Route
				- Name/parameters: `/c/delete/{a}` parameters to use - `$a`
			- Controller method
				- Class/name/parameters: `TypeCEntity_Controller`->`destroy` parameters to use - `$a`
				- Script:
				```php
					TypeCEntity::destroy($a);
				```
				- URL example: `fundamental-mechanisms-app.test/c/delete/1`
- Set up `TypeBEntity`
	- Model method:
		- Class/name/parameters:
			- Name:
				- Rules: The name must be plural as it is a many relationship
				- E.g. `TypeBEntity`->`TypeCEntities`
		- Type: `public`
		- Query: 				
	    - Auto method
	      - For if the relationships table and it's foreign keys columns are named according to the rules
	      ```php
	          return $this->belongsToMany('App\TypeCEntity')->withPivot('created_at');
	      ```
	    - Manual method
	      - For if the relationships table and it's foreign keys columns aren't named according to the rules
	      ```php
	          return $this->belongsToMany(
							'App\TypeCEntity',
							'type_b_entity_type_c_entity',
							'type_b_entity_id',
							'type_c_entity_id'
						);
	      ```
	- Data
		- Create records
			- URL example: `fundamental-mechanisms-app.test/b/create/1`
		- Delete records (only use if needed)
			- URL example: `fundamental-mechanisms-app.test/b/delete/1`
- Set up `TypeBEntityTypeCEntity`
	- Note: This is a associative entity as it simple relates other entities
	- Table-model pair
	 	- Setup method
		 	- `Setup a table-model pair - The long way`
			- We use this method cause we want to keep our table name singular
  - Table
    - Name
        - Rules
					- Must be a combo of both of the entities you are trying to connect
        	- The order of the name combo must be in alphabetic order  
        	- Use the singular version of the table names
        - E.g. `type_b_entity_type_c_entity`
    - Columns
      - These are foreign keys
      - The naming rules
        - They must be named according to the foreign tables the refer to and then have `_id` at the end.
      - E.g.
      ```php
        $table->integer('type_b_entity_id');
        $table->integer('type_c_entity_id');
      ```
  - Model
    - Name
      - Rules: You can use a camel cased version of the table name.
      - E.g. `TypeBEntityTypeCEntity`
    - Table associator: `type_b_entity_type_c_entity`
		- De-restrict fields
		```php
			'type_b_entity_id',
		  'type_c_entity_id',
		```

##### Query relationships of child entity

- Create
	- Method 1
		- Route:
			- Name/parameters: `/b/read/CLink/create/{a}/{b}` parameters to use - `$a, $b`
		- Controller method:
			- Class/name/parameters: `TypeBEntity_Controller`->`showCLinkCreate` parameters to use - `$a, $b`
			- Script:
			```php
				TypeBEntity::findOrFail($a)->TypeCEntities()->attach($b);
			```
		- URL example: `fundamental-mechanisms-app.test/b/read/CLink/create/1/1`
	- Method 2 (detach all others)
		- Note: The IDs of the parent entities that go in an inside the `sync` function
		- Route:
			- Name/parameters: Reuse `/b/read/CLink/create/{a}/{b}/{c}` parameters to use - swap to `$a, $b, $c`
		- Controller method:
			- Class/name/parameters: Reuse `TypeBEntity_Controller`->`showCLinkCreate` parameters to use - swap to `$a, $b, $c`
			- Script:
			```php
				TypeBEntity::findOrFail($a)->TypeCEntities()->sync([$b,$c]);
			```
		- URL example: `fundamental-mechanisms-app.test/b/read/CLink/create/1/2/3`
- Read
	- Route:
		- Name/parameters: `/b/read/CLink/read/{a}` parameters to use - `$a`
	- Controller method:
		- Class/name/parameters: Reuse `TypeBEntity_Controller`->`showCLinkShow` parameters to use - `$a`
		- Script:
		```php
      foreach (TypeBEntity::find($a)->TypeCEntities as $var){
        echo $var->pivot->created_at."<br>";
      }
		```
	- URL example: `fundamental-mechanisms-app.test/b/read/CLink/read/1`
- Delete
	- Note: Don't do these until the end of the subsection as we will still be using these links
	- Detach 1 only
		- Route:
			- Name/parameters: `/b/read/CLink/delete/{a}/{b}` parameters to use - `$a, $b`
		- Controller method:
			- Class/name/parameters: Reuse `TypeBEntity_Controller`->`showCLinkDestroy` parameters to use - `$a, $b`
			- Script:
			```php
				TypeBEntity::findOrFail($a)->TypeCEntities()->detach($b);
			```
		- URL example: `fundamental-mechanisms-app.test/b/read/CLink/delete/1/2`
	- Detach all
		- Route:
			- Name/parameters: Reuse `/b/read/CLink/delete/{a}` parameters to use - swap to `$a`
		- Controller method:
			- Class/name/parameters: Reuse `TypeBEntity_Controller`->`showCLinkDestroy` parameters to use - swap to `$a`
			- Script:
			```php
		    TypeBEntity::findOrFail($a)->TypeCEntities()->detach();
			```
		- URL example: `fundamental-mechanisms-app.test/b/read/CLink/delete/1`

##### Query parents of child entity

- Read
	- Type 1
		- Route:
			- Name/parameters: `/b/read/c/read/{a}` parameters to use `$a`
		- Controller method:
			- Class/name/parameters: `TypeBEntity_Controller`->`showCShow` parameters to use - `$a`
			- Script:
			```php
				foreach (TypeBEntity::find($a)->TypeCEntities as $var){
					echo $var->name."<br>";
				}
			```
		- URL example: `fundamental-mechanisms-app.test/b/read/c/read/1`
	- Type 2
		- Route:
			- Name/parameters: Reuse `/b/read/c/read/{a}` parameters to use `$a`
		- Controller method:
			- Class/name/parameters: Reuse `TypeBEntity_Controller`->`showCShow` parameters to use - `$a`
			- Script:
			```php
				dd(TypeBEntity::find($a)->TypeCEntities);
			```
		- URL example: `fundamental-mechanisms-app.test/b/read/c/read/1`
- Update
	- Route:
		- Name/parameters: `/b/read/c/update/{a}/{b}/{c}` parameters to use `$a, $b, $c`
	- Controller method:
		- Class/name/parameters: `TypeBEntity_Controller`->`showCUpdate` parameters to use - `$a, $b, $c`
		- Script:
		```php
			if(TypeBEntity::find($a)->has("TypeCEntities")){
				foreach(TypeBEntity::find($a)->TypeCEntities as $var){
					if($var->name == $b) {
						$var->name = $c;
						$var->save();
					}
				}
			}
		```
	- URL example: `fundamental-mechanisms-app.test/b/read/c/update/1/1/5`
- Delete
	- Route:
		- Name/parameters: `/b/read/c/delete/{a}/{b}` parameters to use `$a, $b`
	- Controller method:
		- Class/name/parameters: `TypeCEntity_Controller`->`showCDestroy` parameters to use - `$a, $b`
		- Script:
		```php
			TypeBEntity::find($a)->TypeCEntities()->find($b)->delete();
		```
	- URL example: `fundamental-mechanisms-app.test/b/read/c/delete/1/2`

##### Query children of parent entity
- Read
	- Route:
		- Name/parameters: `/c/read/b/read/{a}` parameters to use `$a`
	- Controller method:
		- Class/name/parameters: `TypeCEntity_Controller`->`showBShow` parameters to use - `$a`
		- Script:
		```php
			foreach (TypeCEntity::find($a)->TypeBEntities as $var){
				echo $var->data_field_a."<br>";
			}
		```
	- URL example: `fundamental-mechanisms-app.test/c/read/b/read/3`


#### <a name="6.4.4."></a> Intermediate relationship (one to many)
##### Preparation

- Data
	- `Refresh all the migrations` to have a clean start
- Set up `TypeDEntity`
 	- Table-model pair
		- Setup method: `Setup a table-model pair - The short way`
  - Table
    - Name: `TypeDEntity`
    - Columns
    ```php
      $table->string('name');
    ```        
	- Model
    - De-restrict fields
			```php
				'name',
			```
		- Relationships method
			- Class/name/parameters:
				- Name: `TypeDEntity`->`TypeAEntities`
			- Type: `public`
			- Query: 			
				- For if the relationships table and it's foreign keys columns are named according to the rules
				```php
						return $this->hasManyThrough('App\TypeAEntity', 'App\TypeBEntity');
				```
				- Accessor's 1st parameter: Distant entity name
				- Accessor's 2nd parameter: Intermediate entity name
				- Accessor's 3rd parameter: If you need a custom name for the foreign id column of the intermediary entity
				- Accessor's 4th parameter: If you need a custom name for the foreign id column of the distant entity
	- Data
		- Controller
			- `Set up a controller that is resourced` as previously demonstrated.
				- Name: `TypeDEntity_Controller`
				- Aliases: add this to the header
				```php
					use App\TypeDEntity;
				```
		- Create records (make 3)
			- Do as demonstrated in `Create record with multiple field values`
			- Route
				- Name/parameters: `/d/create/{a}` parameters to use - `$a`
			- Controller method
				- Class/name/parameters: `TypeCEntity_Controller`->`create` parameters to use - `$a`
				- Script:
				```php
					TypeDEntity::create([
						'name'=>$a,
					]);
				```
			- URL example: `fundamental-mechanisms-app.test/d/create/1`
		- Delete records (only use if needed)
			- Do as demonstrated in `Delete method 2`
			- Route
				- Name/parameters: `/d/delete/{a}` parameters to use - `$a`
			- Controller method
				- Class/name/parameters: `TypeDEntity_Controller`->`destroy` parameters to use - `$a`
				- Script:
				```php
					TypeDEntity::destroy($a);
				```
				- URL example: `fundamental-mechanisms-app.test/d/delete/1`
- Set up `TypeBEntity`
	- Table
		- New column
	    - Creation method: `Create a column with a migration`
      - Migration name: `type_b_entity_m_column_type_d_entity_id`
      - Table name: `type_b_entities`.
      - Table columns
      ```php
        $table->integer('type_d_entity_id');
      ```  
  - Model
    - De-restrict fields
  	```php
			'type_d_entity_id',
		```
  - Data
		- Create a record
			- Route:
				- Name/parameters: Reuse `/b/create/{a}/{b}` parameters to use - swap to `$a, $b`
			- Controller method:
				- Class/name/parameters: Reuse `TypeBEntity_Controller`->`create` parameters to use - swap to `$a, $b`
				- Script: just add this
				```php
					TypeBEntity::create([
						'data_field_a'=>$a,
						'data_field_b'=>$a,
						'type_d_entity_id'=>$b,
					]);
				```
			- URL example: `fundamental-mechanisms-app.test/b/create/1/1`
		- Delete a record (only use if needed)
				- URL example: `fundamental-mechanisms-app.test/b/delete/1`
- Set up `TypeAEntity`
	- Data
	  - Create a record
			- URL example: `fundamental-mechanisms-app.test/b/read/a/create/1/1`
	  - Delete a record (only use if needed)
			- URL example: `fundamental-mechanisms-app.test/b/read/a/delete/1`

---
up till here
---







##### Query grandchild of parent entity
- View
	- Route
	```php
	  Route::get('/ExampleRoute50', function(){
	    $example_variable = TypeDEntity::find(1);
	    foreach ($example_variable->TypeAEntities as $example_variable_part){
	      echo "<br><br>".$example_variable_part;
	    }
	  });
	```

####  <a name="6.4.5."></a>Polymorphic relationship (one to many)
##### General
- Definition
	- A good way of understanding a polymorphic relationship is to think of it as a kind of "either-or to many relationship"
	- A polymorphic relationship means a relationship where a child table can be shared between different types of parents (or different parent tables)
##### Prerequisites
- Great-grand-child table-model pair
    - Setup it up - just follow as previously demonstrated in `Setup a table-model pair - The short way` and use the following specs
        - Migration
            - Table's name `TypeEEntity`
            - Table columns
            ```php
              $table->integer('parent_id');
              $table->string('parent_type');
              $table->string('data_field_a');
            ```
        - Model
            - De-restrict fields
				  	```php
							'parent_id',
							'parent_type',
							'data_field_a',
						```
            - Relationship
            ```php
              public function parent() {
                return $this->morphTo();
              }
            ```
- `TypeAEntity`
    - Migration
        - Since we will now be using polymorphic relationships this will be configured.
        - Comment this out `$table->integer('type_b_entity_id')->unsigned();`
        - Refresh all the tables
    - Model
        - Relationship
            - Add this
            ```php
              public function TypeEEntities() {
                return $this->morphMany('App\TypeEEntity', 'parent');
              }
            ```
- `TypeBEntity`
    - Model
        - Relationship
            - Add this
            ```php
              public function TypeEEntities() {
                return $this->morphMany('App\TypeEEntity', 'parent');
              }
            ```
- Repopulate some content
    - Since we refreshed all the tables we will need to repopulate some content.
    - Use the following routes to add content
        - For `type_a_entity` use `/ExampleRoute16` do not use `/ExampleRoute48`
        - For `type_b_entity` use `/ExampleRoute40` don't use `/ExampleRoute46`
        - For example grandparent model use `/ExampleRoute38`
        - For example grandparent-parent relationship model use `/ExampleRoute36`
##### Queries
- Create
  - Create 2 great grandchild records
      - As done here `Create record with multiple field values`
      - Use these details
      ```php
        Route::get('/ExampleRoute51', function(){
          TypeEEntity::create(['parent_id'=>1, 'parent_type'=>'App\TypeAEntity']);
          TypeEEntity::create(['parent_id'=>1, 'parent_type'=>'App\TypeBEntity']);
        });
      ```
  - Create a great grandchild record through a parent
  ```php
    Route::get('/ExampleRoute51.2', function(){
      TypeAEntity::findOrFail(7)->ExampleGreatGrandChildren()->create(['data_field_a'=>'example_value']);
    });
  ```
- Read
  - View the descendent polymorphically
      - `TypeAEntity`
          - Route
          ```php
            Route::get('/ExampleRoute53', function(){
                $example_variable = TypeAEntity::find(1);
                foreach ($example_variable->TypeEEntities as $example_variable_part) {
                  echo "<br><br>".$example_variable_part;
                }
            });
          ```
      - `TypeBEntity`
          - Route
          ```php
            Route::get('/ExampleRoute54', function(){
                $example_variable = TypeBEntity::find(1);
                foreach ($example_variable->TypeEEntities as $example_variable_part) {
                  echo "<br><br>".$example_variable_part;
                }
            });
          ```
  - View the ancestor polymorphically (inverse of view the descendent polymorphically)
    - Route
    ```php
      Route::get('/ExampleRoute55', function(){
          $example_variable = TypeEEntity::find(1);
          return $example_variable->parent;
      });
    ```
- Update
  - Update great grandchild through it's parent
  ```php
    Route::get('/ExampleRoute55.1', function(){
      $example_variable = TypeAEntity::findOrFail(7)->ExampleGreatGrandChildren()->whereId(9)->first();
      $example_variable->data_field_a = "example_value2";
      $example_variable->save();
    });
  ```
  - Update a great grandchild's relationship through a parent
    - Give it a new parent
    ```php
      Route::get('/ExampleRoute55.2', function(){
        TypeAEntity::findOrFail(7)->ExampleGreatGrandChildren()->save(TypeEEntity::findOrFail(2));
      });
    ```
    - Remove it's parent
    ```php
      Route::get('/ExampleRoute55.3', function(){
        TypeAEntity::findOrFail(7)->ExampleGreatGrandChildren()->whereId(9)->update(['parent_id'=>'', 'parent_type'=>'']);
      });
    ```
- Delete
  - Delete great grandchild records
  ```php
    Route::get('/ExampleRoute52', function(){
      TypeEEntity::find(1)->forceDelete();
    });
  ```
  - Delete great grandchild record through parent
  ```php
    Route::get('/ExampleRoute52.1', function(){
      TypeAEntity::findOrFail(7)->ExampleGreatGrandChildren()->whereId(7)->delete();
    });
  ```
####  <a name="6.4.6."></a>Polymorphic relationship (many to many)
##### Prerequisites
- Parent 2 table-model pair
    - Setup it up - just follow as previously demonstrated in `Setup a table-model pair - The short way` and use the following specs
        - Migration
            - Table's name `TypeFEntity`
            - Table columns
            ```php
              $table->string('name');
            ```
        - Model
            - De-restrict fields
				  	```php
							'name',
						```
            - Relationship
            ```php
              public function TypeAEntities() {
                return $this->morphedByMany('App\TypeAEntity', 'type_f_entity_relation');
              }
              public function TypeEEntities() {
                return $this->morphedByMany('App\TypeEEntity', 'type_f_entity_relations');
              }
            ```
- Bridging/relationship table-model pair
    - Setup it up - just follow as previously demonstrated in `Setup a table-model pair - The short way` and use the following specs
        - Migration
            - Table's name `TypeFEntityRelationship`
            - Table columns
            ```php
              $table->string('type_f_entities_id');
              $table->integer('type_f_entity_relation_id');
              $table->string('type_f_entity_relation_type');
            ```
        - Model
            - De-restrict fields
				  	```php
						'type_f_entities_id',
						'type_f_entity_relation_id',
						'type_f_entity_relation_type',
						```
- `TypeAEntity`
  - Model
      - Relationship
          - Add this
          ```php
            public function TypeFEntities() {
              return $this->morphToMany('App\TypeFEntity', 'type_f_entity_relation');
            }
          ```
- Example Great Grand Child model
  - Model
      - Relationship
          - Add this
          ```php
            public function TypeFEntities() {
              return $this->morphToMany('App\TypeFEntity', 'type_f_entity_relation');
            }
          ```
##### Queries
- Create
  - Create 2 parent 2 records
      - As done here `Create record with multiple field values`
      - Use these details
      ```php
        Route::get('/ExampleRoute56', function(){
          TypeFEntity::create(['name'=>'grand-child2.1']);
          TypeFEntity::create(['name'=>'grand-child2.2']);
        });
      ```
  - Create 2 relationship records
    - As done here `Create record with multiple field values`
    - Bear in mind you can use either the `save()` function of the `attach()` function
    ```php
      Route::get('/ExampleRoute58', function(){
        TypeFEntityRelationship::create(['type_f_entities_id'=>'1', 'type_f_entity_relation_id'=>1, 'type_f_entity_relation_type'=>'App\TypeAEntity']);
        TypeFEntityRelationship::create(['type_f_entities_id'=>'2', 'type_f_entity_relation_id'=>1, 'type_f_entity_relation_type'=>'App\TypeEEntity']);
      });
    ```
  - Create relationship records through a child
  ```php
    Route::get('/ExampleRoute58.1', function(){
      $example_variable = TypeFEntity::findOrFail(1);
      TypeAEntity::findOrFail(7)->TypeFEntities()->save($example_variable);
    });
  ```
  - Create relationship records through a child and delete any old relationships for that child
  ```php
    Route::get('/ExampleRoute58.2 ', function(){
      TypeAEntity::findOrFail(7)->TypeFEntities()->sync([2]);
    });
  ```
- Read
  - View polymorphic parents of children
    - While specifying child type 1
      - Route
      ```php
      Route::get('/ExampleRoute60', function(){
          $example_variable = TypeAEntity::find(1);
          foreach ($example_variable->TypeFEntities as $example_variable_part) {
            echo "<br><br>".$example_variable_part;
          }
      });
      ```
    - While specifying child type 2
      - Route
      ```php
      Route::get('/ExampleRoute61', function(){
          $example_variable = TypeEEntity::find(1);
          foreach ($example_variable->TypeFEntities as $example_variable_part) {
            echo "<br><br>".$example_variable_part;
          }
      });
      ```
    - Read the parent through child
    ```php
      Route::get('/ExampleRoute61.1', function(){
        $example_variable = TypeAEntity::findOrFail(7);
        foreach($example_variable->TypeFEntities as $example_variable2){
          echo $example_variable2;
        }
      });
    ```
  - View child of a specified child type of the polymorphic parent (inverse of above). Polymorphic means shared between different tables/types of data.
    - While specifying child type 1
      - Route
      ```php
        Route::get('/ExampleRoute62', function(){
          $example_variable = TypeFEntity::find(1);
          foreach ($example_variable->TypeAEntities as $example_variable_part) {
            echo "<br><br>".$example_variable_part;
          }
        });
      ```
    - While specifying child type 2
      - Route
      ```php
      Route::get('/ExampleRoute63', function(){
        $example_variable = TypeFEntity::find(1);
        foreach ($example_variable->TypeEEntities as $example_variable_part) {
          echo "<br><br>".$example_variable_part;
        }
      });
      ```
- Update
  - Update parent through child
  ```php
    Route::get('/ExampleRoute63.1', function(){
      $example_variable = TypeAEntity::findOrFail(7)->TypeFEntities->first()->update(['name'=>'updated']);
    });
  ```
- Delete
  - Delete parent 2 records
  ```php
    Route::get('/ExampleRoute57', function(){
      TypeFEntity::find(1)->forceDelete();
    });
  ```   
  - Delete parent through child
  ```php
    Route::get('/ExampleRoute57.1', function(){
      $example_variable = ExampleObject::findOrFail(7)->TypeFEntities->first()->delete();
    });
  ```
  - Delete parent 2 records
  ```php
    Route::get('/ExampleRoute59', function(){
      TypeFEntityRelationship::find(1)->forceDelete();
    });
  ```  

###  <a name="6.5."></a>  Model testing environment

#### General
- A queries testing environment is a place to test your controller queries before you add them to your script. The one that comes with Laravel is called Tinker.
#### To open it
- In git bash command line and run `cd C:/laravel-apps/fundamental-mechanisms-app` then `php artisan tinker`
#### To close it
- Run the command `exit`
#### Basic ORM queries
- Create a record
  - In one go
    - Run the command `$example_variable = App\TypeAEntity::create(['data_field_a'=>'data_value_a', 'data_field_b'=>'data_value_b', 'data_field_c'=>1]);`
  - In multiple steps
    - To create a pseudo-form that will send the record data to the db - run `$example_variable = new App\TypeAEntity`
    - To add something to that pseudo-form run `$example_variable->data_field_a = "data_value_a"`
    - To check what the pseudo-form holds so far run `$example_variable`
    - To submit your pseudo-form run `$example_variable->save()`
    - To view the information is has been given while being saved to the db run `$example_variable`
- To view a record
  - Just filtered by id - run `$example_variable = App\TypeAEntity::find(1);`
  - Using other filters
    - Where filter
      - Run `$example_variable = App\TypeAEntity::where("id", "<", 6)->orderBy('id','desc')->first();`
    - WhereId
      - Run `$example_variable = App\TypeAEntity::whereId(2)->first();`
- To update a record
  - First find the records
    - Run `$example_variable = App\TypeAEntity::find(1);`
  - Run `$example_variable->data_field_a = "data_value_a";`
  - Run `$example_variable->save()`
- To delete a record
  - If soft-delete isn't activated
    - First find the records
      - Run `$example_variable = App\TypeAEntity::find(2);`
      - Run `$example_variable->delete()`
  - If soft-delete is activated
    - Soft delete
      - Same method as shown is `To delete a record - If soft-delete isn't activated`
    - Restore
      - Run `$example_variable->restore()`
    - Hard delete
      - First soft delete item
      - Then empty your
        - Run `$example_variable = App\TypeAEntity::onlyTrashed();`
        - Run `$example_variable->forceDelete()`
#### ORM queries with relationships
- View
  - Run `$example_variable = App\TypeAEntity::find(1);`
  - Run `$example_variable->TypeEEntities`
- Create, update, delete just like u do in the `Query Testing Environment- Basic ORM Queries` section




### <a name="6.6."></a> Models with accessors and mutators

#### Table Of Content
- [Dates](#Dates)
- [Accessors](#Accessors)
- [Mutators](#Mutators)

#### <a name="Dates"></a> Dates
##### Basic Dates
- Route
```php
Route::get('/64', function (){
  $date = new DateTime('+1 weeks');
  echo $date->format('m-d-Y');
});
```

##### With Human Readable Accessors
- Setup
- Laravel comes with a library called Carbon that helps with this
- This the following code at the top of your route file
```php
  use Carbon\Carbon;
```
- Usage  
- Now (non-human readable)
  - Route
  ```php
    Route::get('/65', function (){
      echo Carbon::now();
    });
  ```
- Now
  - Route
  ```php
    Route::get('/66', function (){
      echo Carbon::now()->diffForHumans();
    });
  ```
- Ten Days from now
  - Route
  ```php
    Route::get('/67', function (){
      echo Carbon::now()->addDays(10)->diffForHumans();
    });
  ```
- 5 Months Ago
  - Route
  ```php
    Route::get('/68', function (){
      echo Carbon::now()->subMonths(5)->diffForHumans();
    });
  ```
- Yesterday
  - Route
  ```php
    Route::get('/69', function (){
      echo Carbon::now()->yesterday()->diffForHumans();
    });
  ```

#### <a name="Accessors"></a> Accessors
##### Query without an accessor
- Route
```php
  Route::get('/70', function(){
    $example_variable = TypeAEntity::find(7);
    echo $example_variable->data_field_a;
  });
```
##### Query With an accessor
- `TypeAEntity`
  - Route: Reuse route `70` for this
  - Model
    - Upper Case First Letter
    ```php
      public function getExampleColumnAttribute($value) {
        return ucfirst($value);
      }
    ```
    - Or Upper Case All Letters
      - Change the returned value to
      ```php
        strtoupper($value);
      ```

#### <a name="Mutators"></a> Mutators Model
- Route
```php
  Route::get('/71', function(){
    $example_variable = ExampleObject::find(7);
    $example_variable->data_field_a = $example_variable->data_field_a;
    $example_variable->save();
  });
```
- Model
```php
  public function setExampleColumnAttribute($value) {
    $this->attributes['data_field_a'] = strtoupper($value);
  }
```
- Database
  - The check your DB data has changed



## <a name="7."></a>Chapter 7. Views component

### Table Of Content
- [Views](#)

### Definition
  - Views are what  handle style. This is because they give style to your data.
- They are located here `C:\laravel-apps\fundamental-mechanisms-app\resources\views`.

### How to Create Them
- Using a code editor or windows explorer locate yourself to `C:\laravel-apps\fundamental-mechanisms-app\resources\views`.
- Create a new .blade.php file, the name format should be camel case e.g. `ExampleView.blade.php`.:
  - Route
  ```php
    Route::get('/ExampleRoute2', function () {
      return view('ExampleView');
    });
  ```
  - View
    - Name `ExampleView.blade.php`
    - Content
    ```php
      Hello world!
    ```

### Template Inheritance
- This enables parent templates to give default content to their assigned child templates.
- A common example for this is to wrap all your html in html tags and to insert a generic head block.
- Example:
  - Route
  ```php
    Route::get('/ExampleRoute9', function () {
      return view('ExampleView6');
    });
  ```
  - Parent template
    - Location: `C:\laravel-apps\fundamental-mechanisms-app\resources\views\layouts` (you will need to create the "layouts" folder).
    - Name: `ExampleParentView.blade.php`.
    - Content:
    ```html
      <!DOCTYPE html>
      <html>
      <head>
        <meta charset="UTF-8">
        <title>Example Title</title>
      </head>
      <body>
      <div class="container">
        @yield('content')
      </div>
        @yield('footer')
      </body>
      </html>
    ```
  - Child template
    - Location: `C:\laravel-apps\fundamental-mechanisms-app\resources\views`
    - Name: `ExampleView6.blade.php`.
    - Content:
    ```html
      @extends('layouts.ExampleParentView')
      @section('content')
        <h1>Example content</h1>
      @stop
      @section('footer')
        <script>alert('Hello world')</script>
      @stop
    ```


### Accepting Route Parameters
#### Only One Parameter
- Example:
  - Route
    - `Route::get('/ExampleRoute6/{ExampleParameter}', 'ExampleController@ExampleControllerMethod3');`
  - Controller method
    - Method 1
    ```php
      public function ExampleControllerMethod3($ExampleParameter)
      {
        return view('ExampleView3')->with('ExampleParameter',$ExampleParameter);
      }
    ```
    - Method 2 (this method can also be used in controller that have multiple parameters)
    ```php
      public function ExampleControllerMethod3($ExampleParameter)
      {
        return view('ExampleView3', compact('ExampleParameter'));
      }
    ```
  - View
    - Name `ExampleView3.blade.php`
    - Content
    ```php
      Example message with {{$ExampleParameter}}.
    ```
  - Test using something like: `fundamental-mechanisms-app.test/ExampleRoute6/example-parameter-string`.

#### Multiple Parameters
##### As a set of variables
- Example:
  - Route
  ```php
  Route::get('/ExampleRoute7/{ExampleParameter}/{ExampleParameter2}/{ExampleParameter3}', 'ExampleController@ExampleControllerMethod4');
  ```
  - Controller method
  ```php
    public function ExampleControllerMethod4($ExampleParameter, $ExampleParameter2, $ExampleParameter3)
    {
      return view('ExampleView4', compact('ExampleParameter','ExampleParameter2','ExampleParameter3'));
    }
  ```
  - View
    - Name `ExampleView4.blade.php`
    - Content
    ```html
      Example message with {{$ExampleParameter}}, {{$ExampleParameter2}} and {{$ExampleParameter3}}.
    ```
  - Test URL: `fundamental-mechanisms-app.test/ExampleRoute7/1/2/3`.


##### As an array
- Example:
  - Route
  ```php
    Route::get('/ExampleRoute8/{ExampleParameter}/{ExampleParameter2}/{ExampleParameter3}', 'ExampleController@ExampleControllerMethod5');
  ```
  - Controller Method
  ```php
    public function ExampleControllerMethod5($ExampleParameter, $ExampleParameter2, $ExampleParameter3)
    {
      $ExampleParameters = [$ExampleParameter,$ExampleParameter2,$ExampleParameter3];
      return view('ExampleView5', compact('ExampleParameters'));
    }
  ```
  - View
    - Name `ExampleView5.blade.php`
    - Content
    ```html
      Example message with {{$ExampleParameters[0]}}, {{$ExampleParameters[1]}} and {{$ExampleParameters[2]}}.
    ```
  - Test URL: `fundamental-mechanisms-app.test/ExampleRoute8/1/2/3`.

### Control Structures - Foreach Loop
- Example:
  - Route (same as in `Multiple Parameters - As an array`)
  ```php
    Route::get('/ExampleRoute10/{ExampleParameter}/{ExampleParameter2}/{ExampleParameter3}', 'ExampleController@ExampleControllerMethod6');
  ```
  - Controller (same as in `Multiple Parameters - As an array`)
  ```php
    public function ExampleControllerMethod6($ExampleParameter, $ExampleParameter2, $ExampleParameter3)
    {
      $ExampleParameters = [$ExampleParameter,$ExampleParameter2,$ExampleParameter3];
      return view('ExampleView7', compact('ExampleParameters'));
    }
  ```
  - View
    - Name `ExampleView7.blade.php`
    - Content
    ```html
      Example message with:
      @if (count($ExampleParameters))
        <ul>
        @foreach($ExampleParameters as $ExampleParameter)
          <li>{{$ExampleParameter}}</li>
        @endforeach
        </ul>
      @endif
    ```
  - Test URL: `fundamental-mechanisms-app.test/ExampleRoute10/1/2/3`

## <a name="13."></a>Chapter 15. Use common dev stratergies
### <a name="5.1.%20Intro"></a>Chapter 5.1. Intro

#### Make a new laravel powered app
##### Install
- Called it `real-world-examples-app` the method was previously demonstrated.

##### Make table-model pairs
- Create them
	- posts
	  - Command:
	    - Orientate with `cd C:/laravel-apps/real-world-examples-app`
	    - Run `php artisan make:model Post -m`
	- users
	  - Already made
	- role_user
	  - Commands:
	    - Table/Migration: `php artisan make:migration role_user --create="role_user"`
	    - Model: `php artisan make:model RoleUser`
	- roles
	  - Command: `php artisan make:model Role -m`
	- countries
	  - Command: `php artisan make:model Country -m`
	- photos
	  - Command: `php artisan make:model Photo -m`
	- videos
	  - Command: `php artisan make:model Video -m`
	- tags
	  - Command: `php artisan make:model Tag -m`
	- tag_relationships
	  - Command: `php artisan make:model TagRelationship -m`
- Configure them
	- General: Add the following column functions (to the migrations) and model methods (to the models)
	- posts
	  - Similar to
	    - Model: `type_a_entities`
	    - From the section on: Database 	
	    - Video course's section: 41s
	  - Columns
	  ```php
			$table->string('title');
			$table->text('content');
			$table->integer('user_id')->unsigned();    
			$table->softDeletes();
	  ```
	  - Model methods
	    - Part 1 (put this underneath the other `use` function)
	    ```php
	      use Illuminate\Database\Eloquent\SoftDeletes;
	    ```
	    - Part 2
	    ```php
		use SoftDeletes;
		protected $dates = ['deleted_at'];
		protected $table = 'posts';
		protected $fillable = [
		  'title',
		  'body',
		  'user_id',
		];
		public function User(){
		  return $this->belongsTo('App\User');
		}
		public function Roles(){
		  return $this->belongsToMany('App\Role')->withPivot('created_at');
		}
		public function Photos() {
		  return $this->morphMany('App\Photo', 'photo_relative');
		}
		public function Tags() {
		  return $this->morphToMany('App\Tag', 'tag_relative');
		}
	    ```
	- users
	  - Similar to
	    - Model: `type_b_entities`
	    - From the section on: Basic Relationships - One to One 	
	    - Video course's section: 62
	  - Columns: Already set
	  - Model methods
	  ```php
	      public function Post(){
		return $this->hasOne('App\Post');
	      }
	      public function Posts(){
		return $this->hasMany('App\Post');
	      }
	      public function Roles(){
		return $this->belongsToMany('App\Role')->withPivot('created_at');
	      }
	      public function Photos() {
		return $this->morphMany('App\Photo', 'photo_relative');
	      }
	  ```
	- role_user
	  - Similar to
	    - Model: `type_b_entity_type_c_entity`
	    - From the section on: Basic Relationships - Many to many 	
	    - Video course's section: 66-67
	  - Columns
	  ```php
			$table->integer('user_id');
			$table->integer('role_id');
	  ```
	  - Model methods
	  ```php
	      protected $table = 'role_user';
	      protected $fillable = [
		'user_id',
		'role_id',
	      ];
	  ```
	- roles
	  - Similar to
	    - Model:  type_c_entities
	    - From the section on: Basic Relationships - Many to many  	
	    - Video course's section: 	66-67
	  - Columns
	  ```php
			$table->string('name');
	  ```
	  - Model methods
	  ```php
	      protected $fillable = [
	      'name'
	      ];
	      public function Users(){
		return $this->belongsToMany('App\User');
	      }
	  ```
	- countries
	  - Similar to
	    - Model:  type_d_entities
	    - From the section on: Advanced Relationships - Intermediate relationship (one to many) 	
	    - Video course's section: 68-70
	  - Columns
	  ```php
			$table->string('name');
	  ```
	  - Model methods
	  ```php
	      protected $fillable = [
	      'name',
	      ];
	      public function Posts(){
		return $this->hasManyThrough('App\Post', 'App\User');
	      }
	  ```
	- photos
	  - Similar to
	    - Model:  type_e_entities (although due to a mistake it's equivalent is relatively different)
	    - From the section on: Advanced Relationships - Polymorphic Relationships - One to many 	
	    - Video course's section: 71-73
	  - Columns
	  ```php
			$table->integer('photo_relative_id');
			$table->string('photo_relative_type');
			$table->string('file');
	  ```
	  - Model methods
	  ```php
	      protected $fillable = [
		'photo_relative_id',
		'photo_relative_type',
		'file',
	      ];
	      public function photo_relative() {
		return $this->morphTo();
	      }
	  ```
	- videos
	  - Similar to
	    - Model:  type_e_entities (although due to a mistake it's equivalent is relatively different)
	    - From the section on: Advanced Relationships - Polymorphic Relationships - One to many 	
	    - Video course's section: 71-73
	  - Columns
	  ```php
			$table->string('file');
	  ```
	  - Model methods
	  ```php
	      protected $fillable = [
		'file',
	      ];
	      public function Tags() {
		return $this->morphToMany('App\Tag', 'tag_relative');
	      }
	  ```
	- tags
	  - Similar to
	    - Model:  `type_f_entities`
	    - From the section on: Advanced Relationships - Polymorphic Relationships - Many to many  	
	    - Video course's section: 	74-77
	  - Columns
	  ```php
			$table->string('name');
	  ```
	  - Model methods
	  ```php
	      protected $fillable = [
	      'name',
	      ];
	      public function Posts() {
		return $this->morphedByMany('App\Post', 'tag_relative');
	      }
	      public function Photos() {
		return $this->morphedByMany('App\Video', 'tag_relative');
	      }
	  ```
	- tag_relationships
	  - Similar to
	    - Model:  `type_f_entity_relation`
	    - From the section on: Advanced Relationships - Polymorphic Relationships - Many to many 	
	    - Video course's section: 74-77
	  - Columns
	  ```php
			$table->string('tag_id');
			$table->integer('tag_relative_id');
			$table->string('tag_relative_type');
	  ```
	  - Model methods
	  ```php
	      protected $fillable = [
	      'tag_id',
	      'tag_relative_id',
	      'tag_relative_type',
	      ];
	  ```
- Impliment them
	- Orientate yourself with `cd C:/laravel-apps/real-world-examples-app`
	- Run `php artisan migrate`

##### Create a layout view file
- Orientate yourself to you views folder
- Create and orientate yourself to a subfolder called `layouts`
- Create the file `app.blade.php`
- Add this to its contents
```html
  <!DOCTYPE html>
  <html>
  <head>
    <meta charset="UTF-8">
    <title>App</title>
  </head>
  <body>
  <div class="container">
    @yield('content')
  </div>
    @yield('footer')
  </body>
  </html>
```



### <a name="5.2.%20Forms"></a>Chapter 5.2. Forms

#### Table Of Content
- [Basics](#Basics)
- [LC Form Builder](#LC-Form-Builder)
- [Validation](#Validation)





#### <a name="Basics"></a> Basics
##### Setup

- Controller: `php artisan make:controller --resource PostsController`
- Route  
```php
  Route::resource('/posts','PostsController');
```
  - Check all the resultant routes
    - Orientate yourself `cd C:/laravel-apps/real-world-examples-app`
    - Run `php artisan route:list`
- Views
  - Orientate yourself to you views folder
  - Create and orientate yourself to a subfolder called `posts`
  - Create the following files
    - `index.blade.php`
    - `create.blade.php`
    - `show.blade.php`
    - `edit.blade.php`

##### Fine tuning
- Create Post page
	- Part 1
	  - View
	    - Orientate yourself to `create.blade.php`
	    ```html
	      @extends('layouts.app')
	      @section('content')
	      <h1>Create Post</h1>
	      <form class="" action="/posts" method="post">
		<input type="text" name="title" value=""  placeholder="Enter title">
		{{csrf_field()}}
		<input type="submit" name="submit" value="Submit">
	      </form>
	      @endsection
	    ```
	  - Controller
	    - This goes in the posts controller's "create" method
	    ```php
	      return view('posts.create');
	    ```
	- Part 2
	  - Controller
	    - Add an alias
	      - Orientate yourself to your posts controller file
	      - Add the alias `use  App\Post;`  at the top directly underneath the "namespace" function.
	    - This goes in the posts controller's "store" method
	      - Part A
		- Option 1
		```php
		  Post::create($request->all());
		```
		- Option 2
		```php
		  $input = $request->all();
		  $input['title'] = $request->title;
		  Post::create($request->all());
		```
		- Option 3
		```php
		  $post = new Post;
		  $post->title = $request->title;
		  $post->save();
		```
	      - Part B
	      ```php
		return redirect('/posts');
	      ```
	- Test URL: `../posts/create`
- Lists Posts page
	- View
	  - Orientate yourself to `index.blade.php`
	  ```html
	    @extends('layouts.app')
	    @section('content')
	    <h1>List Posts</h1>
	    <ul>
	      <li><a href="{{route('posts.create')}}">Create post</a></li>
	      @foreach($posts as $post)
	      <li><a href="{{route('posts.show',$post->id)}}">{{$post->title}}</a></li>
	      @endforeach
	    </ul>
	    @endsection
	  ```
	- Controller
	  - This goes in the posts controller's "index" method
	    - Part 1
	    ```php
	      $posts = Post::all();
	    ```
	    - Part 2
	    ```php
	      return view('posts.index', compact('posts'));
	    ```
	- Test URL: `../posts`
- View Posts page
	- View
	  - Orientate yourself to `show.blade.php`
	  ```html
	    @extends('layouts.app')
	    @section('content')
	    <h1>View Post</h1>
	    <h2><a href="{{route('posts.edit',$post->id)}}">{{$post->title}}</a></h2>
	    @endsection
	  ```
	- Controller
	  - This goes in the posts controller's "show" method
	  ```php
	    $post = Post::findorfail($id);
	    return view('posts.show', compact('post'));
	  ```
	- Test URL: `../posts/4`
- Edit/Delete Posts page
	- Part 1
	  - View
	    - Orientate yourself to `edit.blade.php`
	    ```html
	    @extends('layouts.app')
	    @section('content')
	    <h1>Edit Post</h1>
	    <form class="" action="/posts/{{$post->id}}" method="post">
	      {{csrf_field()}}
	      <input type="hidden" name="_method" value="PUT">
	      <input type="text" name="title" value="{{$post->title}}"  placeholder="Enter title">
	      <input type="submit" name="submit" value="Update">
	    </form>
	    <form class="" action="/posts/{{$post->id}}" method="post">
	      <input type="hidden" name="_method" value="DELETE">
	      {{csrf_field()}}
	      <input type="submit" value="Delete">
	    </form>
	    @endsection
	    ```
	  - Controller
	    - This goes in the posts controller's "edit" method
	    ```php
	      $post = Post::findOrFail($id);
	      return view('posts.edit', compact('post'));
	    ```
	- Part 2
	  - Controller
	    - This goes in the posts controller's "update" method
	    ```php
	      $post = Post::findOrFail($id);
	      $post->update($request->all());
	      return redirect('/posts');
	    ```
	- Part 3
	  - Controller
	    - This goes in the posts controller's "delete" method
	    ```php
	      $post = Post::whereId($id)->first()->delete();
	      return redirect('/posts');
	    ```
	- Test URL: `../posts/4/edit`

####  <a name="LC-Form-Builder"></a> LC Form Builder
##### Setup
- If you like you can see more info about the Laravel Collective Form Builder at https://laravelcollective.com/docs/5.2/html

- Install packages
	- Configure composer
	  - Oriented yourself to `composer.json` and paste `"laravelcollective/html":"^5.2.0"` as a new line in the `"require"` section. Make sure to put a comma after the previous item.
	  - If your using a Laravel version that doesn't fit into the `5.2` range then you will need to adapt the code.
	- Run composer
	  - Orientate yourself `cd C:/laravel-apps/real-world-examples-app`
	  - Run `composer update`
- Configure package
	- Configure `app.php`
	  - Part 1
	    - Orientate yourself to `config/app.php`
	    - Paste the following code directly above the existing comment
	      - The code
	      ```php
	      Collective\Html\HtmlServiceProvider::class,
	      ```
	      - The comment
	      ```php
		/*
		 * Application Service Providers...
		 */
	      ```
	  - Part 2
	    - Orientate yourself to `config/app.php` and paste the following code as a new line in the `'aliases'` section. Make sure to put a comma after the previous item.
	    ```php
	      'Form' => Collective\Html\FormFacade::class,
	      'Html' => Collective\Html\HtmlFacade::class,
	    ```

##### Usage
- Create Post page
	- View
	  - Orientate yourself to `create.blade.php`
	  - Edit the file to look like this
	  ```html
	    @extends('layouts.app')
	    @section('content')
	    <h1>Create Post</h1>
	    {!! Form::open(['method'=>'POST', 'action'=>'PostsController@store']) !!}
	      <div class="form-group">
		{!! Form::label('title', 'Title:') !!}
		{!! Form::text('title', null, ['class'=>'form-control']) !!}
	      </div>
	      <div class="form-group">
		{!! Form::submit('Create Post', ['class'=>'btn btn-primary']) !!}
	      </div>
	    {!! Form::close() !!}
	    @endsection
	  ```
- Lists Posts page
	- View
	  - Orientate yourself to `index.blade.php`
	  - Edit the file to look like this
	  ```html
	  ```
- View Posts page
	- View
	  - Orientate yourself to `show.blade.php`
	  - Edit the file to look like this
	  ```html
	  ```
- Edit/Delete Posts page
	- View
	  - Orientate yourself to `edit.blade.php`
	  - Edit the file
	    - Final result
	    ```html
	      @extends('layouts.app')
	      @section('content')
	      <h1>Edit Post</h1>
	      {!! Form::model($post, ['method'=>'PATCH', 'action'=>['PostsController@update', $post->id]]) !!}
		<div class="form-group">
		  {!! Form::label('title', 'Title:') !!}
		  {!! Form::text('title', null, ['class'=>'form-control']) !!}
		</div>
		<div class="form-group">
		  {!! Form::submit('Update', ['class'=>'btn btn-primary']) !!}
		</div>
	      {!! Form::close() !!}
	      {!! Form::open(['method'=>'DELETE', 'action'=>['PostsController@destroy', $post->id]]) !!}
		<div class="form-group">
		  {!! Form::submit('Delete', ['class'=>'btn btn-danger']) !!}
		</div>
	      {!! Form::close() !!}
	      @endsection
	    ```
	    - How we got the final result
	      - Edit part
		- Replaced the first form with the same form content as we used in the recent `create.blade.php`
		- Adaptions
		  - but used the method `PATCH` not `POST`
		  - and used the action `PostsController@update` not `PostsController@store`
		  - Used the submit text `Update` not `Create Post`
		  - For the opening form function
		    - Used the opening form function `model` not `open` and add a new parameter of `$post` which goes first
		    - Made the action an array so that it can also include `$post->id`
		    - So it looks like this
		    ```html
		    {!! Form::model($post, ['method'=>'PATCH', 'action'=>'PostsController@update']) !!}
		    ```
	      - Delete part
		- Replaced the second form also with the same form content as we used in the recent `create.blade.php`
		- Adaptions
		  - but used the method `DELETE` not `POST`
		  - and used the action `PostsController@destroy` not `PostsController@store`
		  - Used the submit text `Delete` not `Create Post`
		  - Used the css class text `btn-danger` not `btn-primary`
		  - And removed the title text, title label and their form group
		  - For the opening form function
		    - Made the action an array so that it can also include `$post->id`
		    - So it looked like this
		    ```html
		    {!! Form::open(['method'=>'DELETE', 'action'=>['PostsController@destroy', $post->id]]) !!}
		    ```

##### LC Form Builder Snippets
- Intro
  - To make the writing of commonly used LC Form Builder code samples easier we will make them into snippets
  - If you're using the Atom IDE the method of doing this was demonstrated in the Development Tools part of this course
- Submit button
  - Type of code: `php`
  - Name: `LC Form Builder Sumbit Button`
  - Shortcut: `LCsumbit`
  - Sample:
  ```html
    '''
      <div class="form-group">
        {!! Form::submit('$1', ['class'=>'btn btn-$2']) !!}
      </div>
    '''
  ```
- Text input
  - Type of code: `php`
  - Name: `LC Form Builder Text input`
  - Shortcut: `LCtextinput`
  - Sample:
  ```html
    '''
      <div class="form-group">
        {!! Form::label('$1', '$2:') !!}
        {!! Form::text('$1', null, ['class'=>'form-control']) !!}
      </div>
    '''
  ```
- Form
  - Type of code: `php`
  - Name: `LC Form Builder Form`
  - Shortcut: `LCform`
  - Sample:
  ```html
    '''
    {!! Form::open(['method'=>'$1', 'action'=>'PostsController@$2']) !!}
      <div class="form-group">
        {!! Form::label('$3', '$4:') !!}
        {!! Form::text('$3', null, ['class'=>'form-control']) !!}
      </div>
      <div class="form-group">
        {!! Form::submit('$5', ['class'=>'btn btn-$6']) !!}
      </div>
    {!! Form::close() !!}
    '''
  ```

#### <a name="Validation"></a> Validation
#####

- Intro
  - We will use Laravel's automatic validation errors messages (e.g. "please enter a password with more that 5 characters")
  - This is thought of as setting constraints to the type of requests the user is allowed to make
- Validation message plus basic request validator
  - Create Post page
    - "Store" controller
      - Add the `basic request validator` code below to the store method and make sure it goes above it's sibling functions
      ```php
        $this->validate($request, [
          'title'=>'required|max:50',
        ]);
      ```
        - This code we will just use temporarily to demonstrate how it works
    - View
      - Orientate yourself to `create.blade.php`
      - Add the following code after the form
      ```html
        @if(count($errors) > 0)
          <div class="alert alert-danger">
            <ul>
              @foreach($errors->all() as $error)
                <li>{{$error}}</li>
              @endforeach
            </ul>
          </div>
        @endif
      ```
- Prebuilt request validator
  - Request
    - Make new one
      - Orientate with
      ```shell
        cd C:/laravel-apps/real-world-examples-app
      ```
      - Run
      ```shell
        php artisan make:request CreatePostRequest
      ```
    - Edit it
      - Orientate yourself to
      ```html
        app\Http\Requests\CreatePostRequest.php
      ```
      - In the authorize method set the return value to
        - `true`
        - This sets it so that everyone can make request with the form (not just privileged members)
      - In the rules method add the following to the returned array
        - `'title'=>'required'`
  - Controller Method (Create Posts Page Store Controller Method)
    - Remove the `basic request validator` code
    - Using the request
      - Option 1
        - Change the first part of the store method's parameter (the `Request` part) to `Requests\CreatePostRequest` so it looks like
        ```php
          public function store(Requests\CreatePostRequest $request)
        ```
      - Option 2
        - Change the first part of the store method's parameter (the `Request` part) to `CreatePostRequest` so it looks like
          ```php
            public function store(CreatePostRequest $request)
          ```
        - Add the alias to the top of this file (directly under the "namespace" function)
        ```php
          use App\Http\Requests\CreatePostRequest;
        ```
