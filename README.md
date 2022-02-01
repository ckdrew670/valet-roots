# Valet - Bedrock - Sage

## Laravel Valet

Laravel Valet is a development environment that runs without Nginx and Apache. It’s installed on your physical machine and uses the Caddy server and DnsMasq to re-route requests to locally stored websites. You will still need to install pre-requisite softwares such as MySQL and it only works on OSX. If you've not set up Valet on your machine then use the following instructions to do so:

### Install Valet on your Machine

Installation docs: https://laravel.com/docs/8.x/valet#installation

* Update to the latest Homebrew version using `brew update`
* Use Homebrew to install PHP too `brew install php` 
* Add Valet using Composer `composer global require laravel/valet`
* Run `valet install` 

Valet will automatically start its required services each time your machine boots. You can also do this manually with `valet start` and `valet stop`. See `valet list` for all available commands. 

### Serve sites contained in a specific directory

For more info see: https://laravel.com/docs/8.x/valet#serving-sites

Once Valet is installed, you're ready to start serving your Laravel applications. Valet provides two commands to help you serve your applications: `park` and `link`.

* Create a directory to keep all you Valet sites in `mkdir /sites/valet`
* `cd /sites/valet`
* `valet park`

#### valet park

The `park` command registers a directory on your machine that contains your applications. Once the directory has been "parked" with Valet, all of the directories within that directory will be accessible in your web browser at **http://directory-name.test**. 

#### valet link

The `link` command can be used if you want to serve a single site within a directory: https://laravel.com/docs/8.x/valet#the-link-command

#### valet forget

To 'unpark' a directory, run `valet forget`.

#### valet domain

The default domain suffix is `.test`. You can change this using `valet domain <my-custom-suffix>`

### Managing PHP versions

You can manage different versions of PHP in different projects using a `.valetphprc` file at each project root. This file should specify the version of PHP needed for the project, eg.

```
php@7.4
```

Then you just need to run `valet use` in the project root to switch to that version. 

### Databases

Install MySQL or MariaDB globally using Homebrew. 

* `brew install mysql` or `brew install mariadb`

Once you have MySQL or MariaDB installed, simply create a new database for the project in MySQL, configure your project's `.env` with the correct database settings and it should work fine with Valet.

To crete a database in MySQL run `brew services start mysql` and use the usual `mysql` commands. The default user is `root` and you can also set up a password.

### Useful notes on Valet

https://www.digitalocean.com/community/tutorials/use-laravel-valet-for-a-super-quick-dev-server

## Bedrock and Sage

This repo is set up with PHP 7.4 and Sage 9. 

### Set up an existing site with Bedrock and Sage 9

* Clone this repo
* Create a new database in MySQL (see above)
* cd into the project root and `valet use`
* `composer install`
* Set up `.env` file to match MySQL database and local url (which will be `http://your-project-directory.test`)
* Copy over plugins/uploads and existing Sage 9 theme and make sure `composer.json` packages all match up with original project (at both project root level and theme level) so you have all the correct plugins etc.
* if you need to downgrade WP use (eg. to downgrade to 5.8.2) `wp core update --version=5.8.2 --force`
* make sure to update `config.json` to use new local url for proxy.
* add an `.nvmrc` file to the root with the correct Node version and run `nvm use` before running `yarn start` 


### Set up a brand new Bedrock and Sage site

If you want to set up a brand new Bedrock and Sage configuration from scratch simply run `composer create-project roots/bedrock` in the project folder and pull the files out of the `bedrock` folder that gets created. Use the Bedrock setup docs to setup the `.env` variables and add composer packages: https://docs.roots.io/bedrock/master/installation/#installation

Similarly, you can set up a fresh Sage install within the Bedrock `/themes` directory using:

* for Sage 9 https://docs.roots.io/sage/9.x/installation/ (needs PHP 7.4)
* for Sage 10 https://docs.roots.io/sage/10.x/installation/ (needs PHP 8)
