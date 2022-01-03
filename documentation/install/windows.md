---
description: >-
    How to install Athena in any Windows Environment
---

# Install on Windows

Installing on windows is very straight forward but you will need to do a handful of things to ensure your environment is setup correctly. There is a lot to cover when installing Athena but these instructions cover nearly everything you need to do in a Windows Environment to get Athena running.

Read them carefully, read them twice, and double check your steps.

# Table of Contents

- [Install on Windows](#install-on-windows)
- [Table of Contents](#table-of-contents)
- [Dependencies](#dependencies)
  - [GIT](#git)
  - [NodeJS 16+](#nodejs-16)
  - [MongoDB](#mongodb)
  - [Create a Github Account](#create-a-github-account)
  - [VSCode*](#vscode)
  - [Windows Terminal](#windows-terminal)
- [Setup SSH Key](#setup-ssh-key)
  - [Open Git Bash](#open-git-bash)
  - [Create the SSH Key](#create-the-ssh-key)
  - [Start ssh-agent](#start-ssh-agent)
  - [Add the SSH Key](#add-the-ssh-key)
  - [Add the SSH Key to Github](#add-the-ssh-key-to-github)
- [Ensure MongoDB Running as a Service](#ensure-mongodb-running-as-a-service)
- [Port Forwarding](#port-forwarding)
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
  - [Development Test Mode](#development-test-mode)
  - [Development Vue Mode](#development-vue-mode)
- [Checking Ports](#checking-ports)
- [Connecting](#connecting)
  - [What IP to use?](#what-ip-to-use)
- [Installing Mods](#installing-mods)
  - [Where to Install Mods](#where-to-install-mods)
  - [Updating Configurations](#updating-configurations)
- [Successful Installation](#successful-installation)

# Dependencies

Install or perform all actions in this section.

## GIT

Grab the latest version of GIT from the official website.

[Download GIT](https://git-scm.com/downloads)

## NodeJS 16+

Grab the latest version of NodeJS from the official website.

[Download NodeJS 16+](https://nodejs.org/en/download/)

## MongoDB

Install MongoDB Community Server with all default settings.

[Download MongoDB Community Server](https://www.mongodb.com/try/download/community)

## Create a Github Account

Yes you are going to need a Github account. You are also going to need to setup an SSH key for your Github account. It is covered below.

[Sign Up with Github](https://github.com/signup)

## VSCode*

VSCode is optional but recommended for editing, and modifying code.

[Download VSCode](https://code.visualstudio.com/download)

## Windows Terminal

This is a great tool for inputting commands like the ones you will see below. Highly recommended to install and pin it to your desktop somewhere.

[Download Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701#activetab=pivot:overviewtab)

# Setup SSH Key

Github has really good [SSH Setup Instructions](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) but they may not be entirely clear for newer developers. If you are comfortable with normal documentation give the above link a try. Make sure to select the `windows` tab.

## Open Git Bash

Git Bash is something that should come with GIT by default. Enter `Git Bash` in your windows search to open it.

![](https://thumbs.gfycat.com/SeveralSleepyBarracuda-size_restricted.gif)

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

# Ensure MongoDB Running as a Service

MongoDB does not have to be installed locally but if it is this is an important step. Open your Task Manager and ensure that you see MongoDB running as a service.

![](https://i.imgur.com/2Osus8S.png)

# Port Forwarding

At the very least you will need to open port 7788 for your main server.

You may need to Forward Ports in your Server Panel, Router, etc. If you are running Athena on a server it is likely you will need to add 7788 to an additional Firewall somewhere in your server providers panel.

You will need to open the following ports in your **Windows Firewall** and **Router**.

* 7788

Here's a `.bat` script that will open both ports in your **Windows Firewall.**

```text
ECHO OFF

echo Opening 7788 for TCP
netsh advfirewall firewall add rule name="alt:V-7788-IN-TCP" dir=in action=allow protocol=TCP localport=7788
netsh advfirewall firewall add rule name="alt:V-7788-OUT-TCP" dir=out action=allow protocol=TCP localport=7788

echo Opening 7788 for UDP
netsh advfirewall firewall add rule name="alt:V-7788-IN-UDP" dir=in action=allow protocol=UDP localport=7788
netsh advfirewall firewall add rule name="alt:V-7788-OUT-UDP" dir=out action=allow protocol=UDP localport=7788

pause
```

If you need additional help with port forwarding in your router you should check out this[ Port Forward Website](https://portforward.com/router.htm) where you can find instructions for your router based on brand.

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
npm run windows
```

## Development Test Mode

This is the mode you should use when you are having a limited set of users connect with `debug` mode on.

Enter the following in a terminal:

```
npm run devtest
```

## Development Vue Mode

This is the mode you should use when you want to work on Vue interfaces, and have very fast reconnections to your server. Limited to 1 user.

**THIS ONLY WORKS IF THE SERVER + GAME ARE RUNNING ON SAME MACHINE**

**THIS WILL NOT WORK FOR REMOTE SERVERS**

This is the fastest way to develop your game mode and requires the least amount of compile time to test things.

Enter the following in a terminal:

```
npm run dev
```

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