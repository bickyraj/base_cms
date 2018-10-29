# Base CRM
This is a base crm setup with OAuth 2 authentication in vue.js and Laravel 5.5.

## Requirements

<ul>
	<li>PHP 7 or greater</li>
	<li>Laravel 5.5 or newer</li>
	<li>mySql mariaDB</li>
	<li>Redis not required</li>
</ul>

## Setup process

	git clone https://github.com/bickyraj/base_crm.git

	composer update
 this would load all the necessary vendor files.
 create a database named laravel_base_crm
 Also create a database on postgres name testing_base_crm
 open .env file  and edit the env variables, Default name of project folder is base_crm

	BASE_URL=localhost/YOUR_PROJECT_FOLDER_NAME/
	VUE_BASE_URL = /YOUR_PROJECT_FOLDER_NAME/

In the .env file enter the database name, username and password of your postgres in
	DB_DATABASE=laravel_base_crm
	DB_USERNAME=
	DB_PASSWORD=

In the cmd prompt run the following command sequentially
	php artisan migrate
	php artisan passport:install
	php artisan db:seed
	php artisan migrate --database=testing

now go to browser and enter your url, the project is ready.
