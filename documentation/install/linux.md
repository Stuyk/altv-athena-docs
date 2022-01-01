---
description: >-
    How to install Athena on Ubuntu 18.04 or 20+
---

# Linux

Linux installation should be using Ubuntu 18.04 or greater. The author of this documentation has used Ubuntu 18.04 without any issues.

# Table of Contents

- [Linux](#linux)
- [Table of Contents](#table-of-contents)
- [Dependencies](#dependencies)
  - [GIT](#git)
  - [CURL](#curl)
  - [wget](#wget)
  - [UFW](#ufw)
  - [NodeJS 16+ through NVM](#nodejs-16-through-nvm)
    - [Uninstall Older Versions*](#uninstall-older-versions)
    - [Install Latest Version of NVM](#install-latest-version-of-nvm)
  - [MongoDB](#mongodb)
  - [libatomic1](#libatomic1)
  - [Create a Github Account](#create-a-github-account)
- [Setup SSH Key](#setup-ssh-key)
  - [Create the SSH Key](#create-the-ssh-key)
  - [Start ssh-agent](#start-ssh-agent)
  - [Add the SSH Key](#add-the-ssh-key)
  - [Add the SSH Key to Github](#add-the-ssh-key-to-github)
- [Port Forwarding](#port-forwarding)
  - [UFW Instructions](#ufw-instructions)
- [Setup Private Repo](#setup-private-repo)
  - [Set Private Repo Main Branch to Master](#set-private-repo-main-branch-to-master)
  - [Download from Private Repo](#download-from-private-repo)
  - [Enter the Directory](#enter-the-directory)
  - [Add Upstream](#add-upstream)
- [Installing Dependencies](#installing-dependencies)
- [Installing Server Files](#installing-server-files)
- [License Key Activation](#license-key-activation)
- [Starting the Server](#starting-the-server)
  - [Update the server.cfg](#update-the-servercfg)
  - [Production Mode](#production-mode)
- [Checking Ports](#checking-ports)
- [Connecting](#connecting)
  - [What IP to use?](#what-ip-to-use)
- [Installing Mods](#installing-mods)
  - [Where to Install Mods](#where-to-install-mods)
  - [Updating Configurations](#updating-configurations)
- [Successful Installation](#successful-installation)


# Dependencies

Install or perform all actions in this section. Copy the entire code block and paste it.

## GIT

Grab the latest version of GIT.

```sh
sudo apt update && sudo apt install git
```

## CURL

Grab the latest version of Curl.

```sh
sudo apt update && sudo apt install curl
```

## wget

Grab the latest version of wget.

```sh
sudo apt update && sudo apt install wget
```

## UFW

Grab the latest verson of UFW (Uncomplicated Firewall)

```sh
sudo apt-get install ufw
```

## NodeJS 16+ through NVM

Grab at least version 16+ for NodeJS through nvm.

### Uninstall Older Versions*

This step only applies if you installed NVM in the past.

```sh
nvm uninstall OLD_VERSION_HERE
```

### Install Latest Version of NVM

Install the NVM script for selecting NodeJS versions.

```sh
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.0/install.sh | bash \
    && export NVM_DIR="$HOME/.nvm" \
    && [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" \
    && [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
```

```sh
nvm install 16
nvm use 16
```

## MongoDB

Keep in mind this is optional if you use MongoDB Atlas for your database. If you are using a local database please install MongoDB server here.

```sh
curl -fsSL https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
```

```sh
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
```

```sh
sudo apt update
```

```sh
sudo apt install mongodb-org
```

```sh
sudo systemctl start mongod.service
```

```sh
sudo systemctl status mongod
```

Instructions pulled from [here](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/).

## libatomic1

Grab the libatomic1 library.

```
sudo apt-get update && sudo apt-get install libatomic1
```

## Create a Github Account

Yes you are going to need a Github account. You are also going to need to setup an SSH key for your Github account. It is covered below.

[Sign Up with Github](https://github.com/signup)


# Setup SSH Key

Github has really good [SSH Setup Instructions](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) but they may not be entirely clear for newer developers. If you are comfortable with normal documentation give the above link a try. Make sure to select the `windows` tab.

## Create the SSH Key

Enter the following in a terminal:

```
ssh-keygen -t ed25519 -C "your_email@example.com"
```

When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

It may ask you for a password. Hitting enter twice will automatically default to `no password`.

## Start ssh-agent

Enter the following in a terminal:

```
eval "$(ssh-agent -s)"
```

_It should respond with 'Agent pid XYZ'_

## Add the SSH Key

Enter the following in a terminal:

```
ssh-add ~/.ssh/id_ed25519
```

## Add the SSH Key to Github

It is highly recommended you follow the Github instructions for the rest of this tutorial. They cover / update how to add SSH keys very well.

[Github Instructions for Adding SSH Key to Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

# Port Forwarding

At the very least you will need to open port 7788 for your main server.

You may need to Forward Ports in your Server Panel, Router, etc. If you are running Athena on a server it is likely you will need to add 7788 to an additional Firewall somewhere in your server providers panel.

## UFW Instructions

Be very careful about doing this because you need to ensure port `22` is setup for UFW. 

We're going to do each of these commands one at a time.

```text
sudo ufw allow 22
```

```
sudo ufw allow ssh
```

```
sudo ufw allow 7788
```

```
sudo ufw enable
``` 

_You can verify that ports have been opened successfully after you setup the rest of Athena._


# Setup Private Repo

Open a Windows Terminal such as command line or powershell. The author personally recommends [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701#activetab=pivot:overviewtab) from the Microsoft Store.

Enter the following in a terminal:


```bash
git clone https://github.com/Stuyk/altv-athena --bare altv-athena-bare
```

Create a new private repistory on Github. Let's call it altv-athena-private

![](https://i.imgur.com/y1Lxqwn.png)

Copy your URL from github.

![](https://i.imgur.com/Dd7Zrke.png)

Enter the following in a terminal:

```bash
cd altv-athena-bare
```

Mirror the bare repository to your private mirror.

Enter the following in a terminal:

```bash
git push --mirror <your_github_url_here>
```

Delete the bare repository folder you have just created.

## Set Private Repo Main Branch to Master

This is important and **DO NOT SKIP THIS STEP**.

![](https://i.imgur.com/FXae1k2.png)

![](https://i.imgur.com/czfpchr.png)

## Download from Private Repo

Clone the new repository you created from Github.

Enter the following in a terminal:

```bash
git clone <your_github_url_here>
```

## Enter the Directory

You need to enter the directory to run the next few commands.

Enter the following in a terminal:

```bash
cd <your_repo_name>
```

## Add Upstream

Add the upstream of the original athena repository.

```bash
git remote add upstream https://github.com/Stuyk/altv-athena
git remote set-url --push upstream DISABLE
```

# Installing Dependencies

This installs all NodeJS packages and dependencies that help run the server.

```text
npm install
```

# Installing Server Files

From this point forward you can simply run this `npm` command to update dependencies.

```text
npm run update
```

# License Key Activation

The license key is unique to your Gumroad Transaction. The license key should be kept a secret.

The [Official alt:V Athena Discord](https://discord.gg/pZvbJmKN8Y) will allow you to manage your license key and IP(s) which can use it through the Athena Key Manager Bot.

Open a Private Message with `Athena Key Manager Bot` and type `!help`.

![](https://thumbs.gfycat.com/HandmadeRegularIsabellinewheatear-size_restricted.gif)

_This should open a private message window with the Key Manager_

Send the bot the following information:

```
!refresh your_gumroad_email your_license_key
```

After binding the license you can append the IP of your server, computer, etc. to the license key. Please make sure you actually know what your own computer's IP is. **It is not** `127.0.0.1` and **it is not** `192.168.1.1`.

Google -> `What is my IP?`

Send the bot the following information:

```
!append your_license_key your_server_ip
```

_You can have 5 IPs which can be removed or added at any time._

# Starting the Server

**Hey Listen,** normally you start the server through altv-server.exe but **we do not do that with Athena**. There are other programs that run along-side Athena that allow it to function. You will need to run one of the commands below.

## Update the server.cfg

<p style="font-size: 16px; color: red; font-weight: 800;">Do not modify the server.cfg, yes you are reading this correctly.</p>

Instead, you should do the following.

Open 1 of the 3 configuration(s) in the `configs` folder.

You should see any of the following configurations:

* dev.json
* devtest.json
* prod.json

Edit all of these but remember this very important rule.

<p style="font-size: 16px; color: red; font-weight: 800;">Do not change 'host' because 0.0.0.0 is correct.</p>

## Production Mode

This is the mode you should use when you are having users connect.

Enter the following in a terminal:

```
npm run linux
```

_Linux only supports production mode as you should be doing most of your development on Windows based computers._

# Checking Ports

Check if the ports are currently open **while the server is running**. Check port `7788`.

[Check Ports with YouGetSignal](https://www.yougetsignal.com/tools/open-ports/)

# Connecting

Remember to get the [https://altv.mp/](https://altv.mp) client and connect.

## What IP to use?

If you are running this on your local machine you should connect to `127.0.0.1:7788`.

If you are running this on an external server you should connect to the server's IP address.

# Installing Mods

You should refer to the official [alt:V Docs](https://docs.altv.mp/) on installing modifications.

However, there is one thing that is different.

## Where to Install Mods

You should **always** install modifications in the `src` folder. 

They should be isolated in their own folders.

## Updating Configurations

When you add a modification you must append it to your `configs`.

You should always load your modifications before you load `core` or `webviews`.

# Successful Installation

A successful installation and bootup will look like the following:

![](https://i.imgur.com/jGxBXLC.png)