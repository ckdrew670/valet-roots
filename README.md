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

The `park` command registers a directory on your machine that contains your applications. Once the directory has been "parked" with Valet, all of the directories within that directory will be accessible in your web browser at **http://<directory-name>.test**




