Dokku Expressjs and jQuery File Upload
=================

An example of how you can persist data on a dokku server using `dokku storage` command.

Install
-------

* Download or clone this repo
* run ```npm install```
* run ```node bin/www```

for debug messages
* run ```DEBUG=express:* node app.js```


Deploy
-------
With our application created, we can push it to the Dokku server. We just need to add the Dokku server as a remote on this project.

```bash
git remote add remote_name dokku@dokku_server_domain:app_name
```

to deploy, we simply push our code to the Dokku server:

```bash
git push remote_name master
```

You should see quite a bit of output as Dokku builds the dependencies and environment and then deploys your app. At the end, you should see see something like this:

```bash
-----> Releasing app_name ...
-----> Deploying app_name ...
-----> Cleaning up ...
=====> Application deployed:
       http://app_name.domain_name.com

To dokku@domain_name.com:app_name 
```

finally inside of your dokku server run the following command:

```bash
$ dokku storage:mount app_name /var/lib/dokku/data/storage/app_name/uploaded:/app/public/uploaded
```

enjoy!

**NOTE**: original code from [expressjs-fileupload](https://github.com/arvindr21/expressjs-fileupload) example.