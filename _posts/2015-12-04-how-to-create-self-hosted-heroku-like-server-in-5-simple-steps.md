---
title: How to create self hosted Heroku like server in 5 simple steps.
layout: post
published: true
---
<div class="message">
  Goal — `git push` and enjoy your coffee ☕️
</div>

Building a server from ground zero to host a production app could be a real pain. The whole process of installing all the dependencies one by one with their appropriate version, and keeping necessary configs in check is very tedious. There are a few tools to automate these tasks, such as, [Chef](https://www.chef.io), [Puppet](https://puppetlabs.com), [F*cking Shell Script](https://github.com/brandonhilkert/fucking_shell_scripts) etc. but they come with their own DSL which requires learning curve. None of them work out of the box.

I’m a huge fan of [Heroku](https://www.heroku.com). My mind was blown by the ease of deployment that Heroku provides when I saw it for the first time. Ever since then, I’ve become addicted to their command line tool belt. But unfortunately, this ease comes with a hefty price tag. Even a slightly dynamic project with minimal resource would cost around $50. They do offer a free plan which, according to me, is not feasible unless you’re hosting a static site. 

This pushed me to look out for a viable, cheaper, and lazy (to cater my addiction) solution, and this is how I stumbled upon Dokku-alt.

> Dokku-alt is a Docker powered mini-Heroku. The smallest PaaS implementation you’ve ever seen. It’s a fork of original dokku. The idea behind this fork is to provide complete solution with plugins covering most of use-cases which are stable and well tested.

Voila! It’s exactly what I was looking for. I grabbed a $5 DigitalOcean Ubuntu droplet and made it my playground for testing this new shiny toy. Few sets of commands, domain DNS setup, and a cup of coffee is all it took to deploy an app. The whole experience was pretty sweet and painless. Life is way simpler now.

---

Here’s how you can make yours:

### Step 1 (pre-requisites):

- You need a fresh (recommended) Ubuntu 14.04 LTS VM from any cloud provider (seriously, it doesn’t matter).
- A ready-to-use domain with DNS access. 
- Your public ssh key for password-less access to execute commands on your server. 

### Step 2 (Installation): 

Execute below ssh command on your VM after logging in via root.

```
$ sudo bash -c "$(curl -fsSL https://raw.githubusercontent.com/dokku-alt/dokku-alt/master/bootstrap.sh)"
```

It will probably take less than a minute to install all the required libs. Once the installation is done, it will run a Sinatra server on port 2000. You simply need to point your browser to `http://<your server ip>:2000/` add your domain and public ssh key to finish the configuration. 

### Step 3 (App creation):

We will now create the app that we want to host.

```
dokku apps:create (your app name here)
```

Whatever name you give to your app, it will also become the subdomain to access it. Now let’s add environment keys to the app.

```
dokku config:set (your app name) KEY1=value1 KEY2=value2 …
```

### Step 4 (Database):

Dokku-alt offers multiple databases including PostgreSQL, MySQL, MongoDB, MariaDB, Redis etc. If you don’t find yours in the list than I’m sure there must be a plugin available to install it. 

Let’s install PostgreSQL for the sake of it.

```
dokku postgresql:create (your database name here)
```

It will install and create a database with the name you provide. But we’re not done yet. There’s one more important step we need to follow before moving ahead, i.e.:

```
dokku postgresql:link (app name) (database name)
```

Only after this command that your app will be able to access the database. This will also add required database credentials as environment keys. 

### Step 5:

Now, add remote git url on your development machine inside the project folder.

```
git remote add dokku dokku@(your domain):(your app name)
git push dokku master
```

Grab a cup of coffee and wait for it to finish. If everything goes as expected, you will have a working copy of your app in a matter of minutes. 

Here is the list of commands provided by dokku-alt [](https://github.com/dokku-alt/dokku-alt#help)

P.S: if you run into memory allocation issues, follow these steps for the fix. 

P.S.S: You can also execute commands from your local machine by `ssh dokku@<your domain> "your command here"`

---
If you liked this article, [click "Recommend" on Medium](https://medium.com/@bilalbudhani/how-to-create-self-hosted-heroku-like-server-in-5-simple-steps-fd100e4e0cbd#.iylf702m6). Or, say hi to [me on Twitter](https://www.twitter.com/BilalBudhani) 👋

