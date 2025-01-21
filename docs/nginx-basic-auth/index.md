---
title: How to Set Up Basic Authentication for Mainsail Using NGINX
description: Learn how to add a simple access restriction to your Mainsail
  interface with NGINX using Basic Authentication. Follow this straightforward
  guide to implement lightweight access control for your Mainsail setup!
---

# Access Restriction with Basic Authentication for Mainsail
In this tutorial, I'll show you how to set up simple access restriction for
Mainsail using NGINX. This method is just a simple access restriction and is not
a security feature to protect Mainsail!

## Prerequisites
- MainsailOS installed on your Raspberry Pi or similar setup (e.g., KIAUH)
- SSH access to your Raspberry Pi
- Basic knowledge of Linux and the command line

## Step 1: Configure Basic Authentication

### Install Apache2-utils
First, install the `apache2-utils` package, which provides the `htpasswd` tool
to create and manage user files for basic authentication.

```bash
sudo apt update
sudo apt install apache2-utils
```

### Create User File
Next, create a user file with the `htpasswd` tool. Replace `username` with your
desired username.

```bash
sudo htpasswd -c /etc/nginx/.htpasswd username
```

You will be prompted to enter a password for the user. After entering the
password, the user file will be created.

### Modify File Permissions
Change the permissions of the `.htpasswd` file to prevent unauthorized access.

```bash
sudo chmod 640 /etc/nginx/.htpasswd
sudo chown root:www-data /etc/nginx/.htpasswd
```

## Step 2: Update NGINX Configuration

### Edit NGINX Configuration File
Open the NGINX configuration file in a text editor.

```bash
sudo nano /etc/nginx/sites-available/mainsail
```

Add the following lines to the `server` block.
    
```nginx
auth_basic "Restricted Access";
auth_basic_user_file /etc/nginx/.htpasswd;
```

So it looks like this:

```nginx
server {
    listen 80 default_server;
    # uncomment the next line to activate IPv6
    # listen [::]:80 default_server;

    auth_basic "Restricted Access";
    auth_basic_user_file /etc/nginx/.htpasswd;

    access_log /var/log/nginx/mainsail-access.log;
    error_log /var/log/nginx/mainsail-error.log;

    # some more lines...
```

Then save the file and exit the text editor. To save the file in Nano, press
`Ctrl + O`, then `Enter`, and to exit, press `Ctrl + X`.

## Step 3: Check and Reload NGINX
Check the NGINX configuration for syntax errors.

```bash
sudo nginx -t
```

If the configuration is correct, reload NGINX to apply the changes.

```bash
sudo systemctl reload nginx
```

## Step 4: Test Access
Open your browser and navigate to your Mainsail instance. You should now be
prompted to enter the username and password you created earlier.

## Important Notes
- This method is a simple access restriction and is not a security feature to
  protect Mainsail.
- Make sure to keep your username and password secure.
- If you forget your password, you can recreate the user file with a new
  password.
- To remove the access restriction, remove the `auth_basic` lines from the NGINX
  configuration file and reload NGINX.

