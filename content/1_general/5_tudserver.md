---
title: Hosting with TU Delft webserver 🌶
short_title: TUD server 🌶
# subtitle: Using the GitHub Integrated Development Environment to write and edit content
authors:
    - id: FreekPols
    - id: RonaldLigteringen

--- 

> Here we describe how to host your Jupyter Book project on a TU Delft webserver, including requesting the server and setting it up as a webserver.

## Requesting a TU Delft (web)server
Talk to your department's IT support to ask for support in setting up a virtual TUD linux server (Faculty Managed Servers). If agreed upon, you can request a [FMS](https://tudelft.topdesk.net/tas/public/ssp/content/serviceflow?unid=3a67785f-b4c9-4601-949d-bc8c9cb6b0eb), specifically a linux (Ubuntu) server with ports **22** (ssh), **80** (http) and **443** (https) open. Faculty domain specific servers are preferred (e.g. somesite.tnw.tudelft.nl over somesite.tudelft.nl).

When approved and made available, an email is sent with the first details: 

## Setup TU Delft webserver
1. Use [putty](https://www.putty.org/) to connect to the server via ssh. HostName is given under Step A (connect to linux-bastion). Click `Open`.
````{aside} 
```{figure} ../images/putty.png
:width: 100%
```
```` 
2. Click accept, allowing the computer to connect to the server.
3. Login with your netID (without \@tudelft.nl)
4. Use the information under Step B (use SSH Key-Based Authentication). (`ssh <servername>.tudelft.nl`)

You are now logged in to the server. 

5. We first install the webserver (apache). Run `sudo apt install apache2`. 
6. We can check whether it successfully installed by going to the server's IP address in a web browser. You should see the default apache page. Or confirm by running `sudo systemctl status apache2` and checking whether the service is active (running).

7. Make a second user `sudo adduser web`, make a password (14 characters) for this user.
 
Everything that is in home/web/ will be visible on the webserver. You can use `cd /home/web` to navigate to this directory.

8. Assign your self the web user: `sudo -u web bash -` and navigate to home/web. 

9. Make a directory call `.ssh` by running `mkdir .ssh` and navigate to it.

10. Create an ssh key by running `ssh-keygen`. Do not use a passphrase. This a vulnerability but is necessary for the webserver to be able to pull from GitHub without manual input.

Two keys are generated: `id_rsa` (private key) and `id_rsa.pub` (public key). The public key needs to be copied to an authorized_keys file.

11. Run `cp id_rsa.pub authorized_keys` to do this. You will need the private key later to add it to GitHub/GitLab.

We are now ready with setting up the server, but need to secure it.

12. Run `sudo -i` to open become a superuser. We need to install a firewall which can be done by running `apt install ufw`.

13. We need to allow ssh, http and https traffic through the firewall. This can be done by running `ufw allow ssh`, `ufw allow http` and `ufw allow https`. Enable the firewall by running `ufw enable`. You can check the status of the firewall by running `ufw status`.

14. Run `apt install fail2ban` to install fail2ban, which is a software that protects against brute-force attacks. It works by monitoring the log files for failed login attempts and banning the IP address after a certain number of failed attempts. You can check the status of fail2ban by running `systemctl status fail2ban`.

If you decided to maintain your server yourself, you will need to regularly check for updates and security patches. This can be done by running `apt update` and `apt upgrade`. You can also set up automatic updates by running `apt install unattended-upgrades` and configuring it to your needs.

## Change start dir

Apache has set the home folder to `var/www` where we want it to be `home/web`. Using the terminal:

1. Run `sudo nano /etc/apache2/sites-available/000-default.conf`

2. Change `DocumentRoot /var/www/html` to `DocumentRoot /home/web`.

3. Add: 

```{code-block} apache
<Directory /home/web>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>
```

4. Save the changes `Ctrl+O, Enter, Ctrl+X` and run `sudo systemctl restart apache2`

5. Follow steps 2-4 after: `sudo nano /etc/apache2/sites-available/default-ssl.conf`

6. Run
```{code-block} bash
sudo a2ensite default-ssl.conf
sudo a2enmod ssl
sudo systemctl reload apache2
```

7. Check whether `Syntax OK` is shown after running: `sudo apache2ctl configtest`, else: `sudo systemctl restart apache2`

## Request SSL-certificate
We need to request an SSL-certificate:

```{code-block} bash
sudo apt update
sudo apt install certbot python3-certbot-apache
sudo certbot --apache -d <server>
```

and test:
```{code-block} bash
sudo apache2ctl configtest
sudo systemctl reload apache2
```

### Useful linux commands
|command | |
| --- | --- |
| `ls` | list files in the current directory |
| `ls -a` | list all files (hidden) in the current directory |
| `ls -l` | list files in long format (permissions, owner, size, date) |
| `cd` | change directory |
| `cd ~` | change to home directory |
| `pwd` | print working directory |
| `q` | quit |
| `exit` | exit the terminal / logout |
| `sudo` | run a command with superuser privileges |
| `sudo -s` | open a root shell |
| `cat` | concatenate and display file content |
| `reboot` | reboot the server |
