# Sample Project Repository for adding DrupalVM to your projects

Note: This is pre-built setup for demo.

If you want to add Drupal VM to your projects via composer, use the following steps.

## Steps

First you need to [install composer](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx).

> Note: The instructions below refer to the [global composer installation](https://getcomposer.org/doc/00-intro.md#globally).
You might need to replace `composer` with `php composer.phar` (or similar) 
for your setup.

After that you can create the project:

```
composer create-project drupal-composer/drupal-project:8.x-dev some-dir --stability dev --no-interaction
```

With `composer require ...` you can download new dependencies to your 
installation.

```
cd some-dir
composer require drupal/devel:~1.0
```

The `composer create-project` command passes ownership of all files to the 
project that is created. You should create a new git repository, and commit 
all files not excluded by the .gitignore file.

Second Command is to add drupal vm via composer
```
cd some-dir
composer require --dev geerlingguy/drupal-vm

```
This will add Drupal VM to your project. You can check by visiting `some-dir/vendor/geerlingguy` directory.

## Adding config.yml and Vagrant files

1. [config.yml](https://github.com/mohit-rocks/drupalcamp-pune/blob/master/vm/config.yml) allows various attributes and tools that are required for project.
  You can use `config.yml` from this project or can create your own.
2. To create your own `config.yml`
    - Goto `some-dir/vendor/geerlingguy/drupal-vm`.
    - Copy `default.configy.yml` and paste it to `some-dir/vm/config.yml`
    Note that, you will need to create `vm` directory in your project root.
    - Modify all the settings in `config.yml` as per your requirement.
3. Create delegating file called `Vagrantfile`, which will tell Vagrant about where it should find Drupal VM, config.yml and other required files.
4.  Ignore vagrant files, because they are not supposed to be committed in repo. You can add this to your `.gitignore`
    -  ```
         # Ignore Vagrant related files and folders.
         .vagrant/
4. Once these files are created, you are good to use vagrant. Run following commands.
    - Composer install
    - vagrant up
5. Note: Make sure that you have installed all the required dependencies for vagrant and drupal vm. You can check that on [Drupal VM](https://github.com/geerlingguy/drupal-vm) project page.    
    
## For other operations like adding modules etc.
1. To perform drupal related changes like adding module, theme, patches etc. you can refer README file for [Drupal Composer](https://github.com/drupal-composer/drupal-project) project template's readme file.
