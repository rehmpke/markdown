# DigitalOcean build and deployment

Building a deployment proceedure to the web. This builds an Ubuntu 16.04.4 x64 instance. Adds NGINX web server.

## Create a server
### Setup a droplet

-   Then a droplet type which was Ubuntu 16.04.4 x64, memory 1gb, 1 vCPUs, SSD Disk 25GB, Transfer 1 TB, Price $5/month 
-   Choose a datacenter region. I used New York 3.
-   Then I added my public ssh key.
-   Choose a hostname that is appropriate and meaningful as cannot be changed. should have something to do with its purpose. ex. rehmpke_ub_webserver_01
-   Then click the create button.

### Copy the IP
-   Then I copied my ip from the new droplet

### Connect Iterm to the server and update
-   Then I opened my iterm and used z to go to the ssh folder
-   If don't have one create ssh key pairs public and private with 

        ssh-keygen -t rsa
    
-   Then I used my `ssh -i public_key root@ip.com` to get into the newly created server
       -i option means to use identity public_key to ssh in.
-   Then I used apt to update the server `apt update`
-   Then we just pulled everything down with apt update but now we need to `apt upgrade` to apply them.
-   install the package maintainer's version if that comes up in pink

## Point a domain
-   Then I pointed my Domain at godaddy to the A record for @ to my ip and cnamed the www to my @.

## Add a user
-   `adduser username`
-   give it a 'password' twice
-   return/enter(skip all other details)
-   is the information all correct then 'y'

## Make sure new user has sudo permissions
-   `usermod -aG sudo test`
-   `su test`
-   cd to `cd ~`
-   `pwd` to verify

Do a test to see if have permissions

    $ sudo cat /var/log/auth.log

## Node setup and installation
To get the node six package which is a slightly better node version we run the curl command and pipe it to bash. 
  
    $ curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -

Once that is finished.

-   $ sudo apt install nodejs
-   then check to see if have the right version of node installed `node -v`
-   v6.14.3
-   now we need to do a little trickery because of the way node installs. Check where npm is reading from `npm config get prefix`.
-   `/usr` that is not good. as if we sudo to it with npm from then on using sudo to do npm. I stress bad mojo. It would work in a few instances where we have npm doing global things but is bad to run modules with sudo.

So. We need to make a directory 
-   $ mkdir ~/.npm_global
Then we need to tell npm what directory to use
    $ npm config set prefix '~/.npm_global'

Open or create ~/.profile and add the following line with vim or nano

    export PATH=~/.npm_global/bin:$PATH

Then update the system variables in the command line

    $ source ~/.profile

Just to do a test we could do a 'npm config get prefix' but we could do an install of forever with npm to test.

    $ npm i -g forever

## Server setup
Change the working directory to the www one.    If it does not exist
      `$ sudo mkdir /var/www/`

    $ cd /var/www/

Change ownership of www to test user as we created that directory.

    $ sudo chown -R $USER:$USER /var/www

Then clone a depository into it.

    $ git clone https://github.com/rehmpke/mysite.git
  Then cd into it.
      
    $ cd fsfe2
  Then npm i to install it's package.
  
    $ npm i

## Server Security
Make a ssh directory

    $ mkdir -p ~/.ssh
I opened a new Iterm tab and copied my public_key using pbcopy

    $ pbcopy < public_key.public

and paste our Public key into a file named authorized_keys

    $ vi ~/.ssh/authorized_keys

**!!! WARNING: login to the added user test so we can be sure we can get back into the server before removing the root user password access from the command line !!!**

once we have tested the ssh -i public_key test@ip address then we need to give root a password so log back in to root and give a password

    - $ passwd

test going into the test user and then su to root to see if that works. `su root`

disable root login allow only ssh to login

    - $ sudo vi /etc/ssh/sshd_config
    - PermitRootLogin no
    - PasswordAuthentication no

restart ssh
    - $ sudo service sshd restart

to figure out what is wrong sometimes with ssh you can try `ssh -v` and it will give a much more detailed list of items it is running through.

### Firewalls
nmap YOUR_SERVER_IP

can use ufw or digitalOcean has a firewall can use.

### Automatic Updates
to help keep things updated as non updated software is the most often thing taken advantage of.
    - $ sudo apt install unattended-upgrades

may already be installed

Now make some adjustments
    $ cat /etc/apt/apt.conf.d/20auto-upgrades

    APT::Periodic::Update-Package-Lists "1";
    APT::Periodic::Unattended-Upgrade "1";

Also in the same directory make the following change. as we only want security changes upaded.
    $ sudo vi /etc/apt/apt.conf.d/50unattended-upgrades
    
    and comment out /the distro codename one at top and save.

### install Fail2ban
all the offenders people trying to break in.

    $ sudo apt install fail2ban

    then copy jail profile
      
    $ sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
    $ sudo vi /etc/fail2ban/jail.local
    
then can see the things trying to access by looking at the following log.
    
    $ sudo tail -f /var/log/fail2ban.log
    
## Shells
Study `find` and `grep`. Find looks for a file. grep looks for things in files.

zgrep to look in gziped files.

## Setup secure site with HTTPS
install nginx
    
    $ sudo apt-get install nginx
    
start nginx

    $ sudo service nginx start
    
type in to browser ip address to view welcome nginx page.

    cd /etc/nginx/

    $ cd sites-available





more goes here roger

[CertBot](https://certbot.eff.org)

Add the certbot repository

Pull in new repository information

Install certbot with nginx plugin
