dokku-npm
=========

Run npm to install global packages globally.

dokku-npm is a plugin for [dokku](https://github.com/dokku/dokku) that installs apt packages in your dokku environment.
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

### npm-packages
This file should contain npm packages to install, accepts one package per line, and multiple lines.

Example:
```
puppeteer
```

### wget-packages
This file should contain command lines that install additional packages using wget, accepts one package per line, and multiple lines.

Example:
```
sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.py | sudo python -c "import sys; main=lambda:sys.stderr.write('Download failed\n'); exec(sys.stdin.read()); main()"

```
