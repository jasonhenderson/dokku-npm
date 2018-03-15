dokku-npm
=========

Run npm to install global packages globally.

dokku-npm is a plugin for [dokku][dokku] that installs apt packages in your dokku environment.
This is mostly useful for instances where you have an app that depends on packages being here.

## Installation

On your dokku server:

### dokku >= 0.4.0
```sh
sudo dokku plugin:install https://github.com/jasonhenderson/dokku-npm
```

### dokku < 0.4.0

```sh
git clone https://github.com/jasonhenderson/dokku-npm -b 0.1.0 /var/lib/dokku/plugins/dokku-npm
dokku plugins-install
```

## Usage

When you deploy your project, the dokku-npm plugin will install according to your project's `.npmpackages` files. You should store this file in your projects root as the docker container will copy your project to its /app directory. This is where the dokku-npm plugin looks for `.npmpackages`.

### .npmpackages
This file should contain npm packages to install, accepts multiple packages per line, and multiple lines.

Example:
```
puppeteer
```

[dokku]: https://github.com/progrium/dokku
