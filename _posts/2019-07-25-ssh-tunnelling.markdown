---
layout: post
title:  "Accessing PostgreSQL Database hosted on EC2 using SSH tunneling"
date:   2019-07-25 15:26:16 +0500
categories: aws,linux
---


# Getting Access to IFI Database

This blog illustrates how can we get access to the IFI Claims Postgres Database. 


## Installing `pgadmin`
`pgadmin` is a SQL Query tool and can be used to query a Postgres database. Follow the steps below to install this tool.

To begin the installation of PgAdmin4, run the command below.

```
$ sudo apt-get install pgadmin4 pgadmin4-apache2
```

During the installation process, you will be prompted for an `Email address` and `Password`, provide an email and password of your choice. These will be used to login to the pgAdmin4 dashboard.

> Alternatively you could install `pgadmin4` through `Ubuntu Software` by searching for `pgadmin4` 

## Connecting to `pgAdmin4`

Now that we have successfully installed PgAdmin4, it’s time now to connect to it. Open your browser and browse your server’s IP address as shown

```
http://IP-address/pgAdmin4
```

As it is your first time to `pgAdmin4`, you will be presented with a login screen. 
Use the `email` and `password` you chose during the installation process and hit login.

You will be presented with pgAdmin4 dashboard

## Connecting to a Database

follow the steps below to connect to a IFI claims database

1. Once on the dashboard, click `Add New Server` button, a popup will appear with a form to be filled in.

2. On the `General` Tab, provide `Name` and check the `Connect Now?` checkbox

3. Move to the `Connection` Tab and fill the form as below

    - for `host name/address` enter `localhost`
    - for `port` enter `5432` (default)
    - for `Maintenance Database` enter `<name-of-database>`
    - for `Username` enter `<databse-user-name>`
    
4. Now go to `SSH Tunnel` Tab and do the following

    - toggle `Use SSH Tunneling` to `Yes`
    - for `Tunnel Host` field provide the IP Address of IFI Claims host i.e. `<ip-address-of-EC2-instance>`
    - for `Username` field provide the username as `ec2-user`
    - toggle `Authentication` button to use `Identity file`
    - click the `browse` button next to `Identity file` field and choose your private `SSH key file`
    - click `Save` button

5. After a while the database should appear in the left panel in the list of `Servers`.
