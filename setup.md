# Set Up

### Drupal VM

Follow instructions as per [https://www.drupalvm.com/](https://www.drupalvm.com/)and initiate a VM

Login to virtual machine

```
vagrant ssh
```

### platform.sh

Create an account on [https://platform.sh/](https://platform.sh/)and initiate a project

##### Platform CLI in Vagrant VM

```
vagrant ssh
cd ~
curl -sS https://platform.sh/cli/installer | php
platform
```

> If you don't have Vagrant, SSH into your virtual machine

### 

##### On local machine

```
platform get \[project-id\] \[folder-name\]
cd drupal
platform build
```

create local.settings.php and add drupal VM credentials

add hash by going to vagrant ssh and type

```
drush cget system.site

get default\_config\_hash code and copy
```

Copy contents to settings.local.php under web/sites/default

    `settings['hash_salt'] = 'myhash';        
    config_directories[CONFIG_SYNC_DIRECTORY] = '../config/sync';` 

> note You should never commit a settings.local.php file to your repository. The file will always be overwritten by Platform.sh \(when using the drupal build flavor\).

## Bitbucket

Create an account on [https://bitbucket.org/](https://bitbucket.org/)and an empty repo

Get bitbucket url

##### On local machine

```
git remote add bitbucket https://USERNAME@bitbucket.org/USERNAME/REPO.git
git remote -v
```

##### Add SSH keys on virtual machine

Login into VM with vagrant ssh and follow the instructions on. You need to do this process twice, one logged from local drupalVM and other from your local machine. Therefore, bitbucket will have two keys under account/settings

[https://confluence.atlassian.com/bitbucket/set-up-ssh-for-git-728138079.html](https://confluence.atlassian.com/bitbucket/set-up-ssh-for-git-728138079.html)

##### platform.sh and Bitbucket integration

Go to bitbucket and add platform sh as integration and select your new project

