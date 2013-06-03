# Rails Base Box

A development environment with Rails and some of it's friends installed.

## Getting Started

Assuming you've been provided with a copy of a packaged version of the box you'll just need to run a few commands to get up and running. 

Mac and Linux users, run these commands:

```
$ vagrant box add railsbox /path/to/railsbox.box
$ mkdir myrailsbox
$ cd myrailsbox
$ vagrant init railsbox
```

Windows users, run these commands:

```
C:\> vagarant box add railsbox C:\path\to\railsbox.box
C:\> mkdir myrailsbox
C:\> cd myrailsbox
C:\> vagrant init railsbox
C:\> vagrant up
```

Now you need to make a slight edit to `Vagrantfile` so that you can get access to your projects that are running. Change the file so that it looks *exactly* like this:

```
Vagrant.configure("2") do |config|
  config.vm.box = "railsbox"
  config.vm.network :forwarded_port, guest: 3000, host: 3000
end
```

Now you're ready to start Vagrant and log into your railsbox.

Mac and Linux users, run these commands:

```
$ vagrant up
$ vagrant ssh
```

Windows users, run these commands:

```
C:\> vagrant up
C:\> vagrant ssh
```

Now you have a railsbox that's running. Read on to learn how to work with it.

## Creating your first rails app

When you first login with `vagrant up`, you should see something that looks like this:

```
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
Welcome to your Vagrant-built virtual machine.
Last login: Fri Sep 14 06:23:18 2012 from 10.0.2.2
vagrant@precise64:~$
```

Enter the following commands to create your first rails site.

```
$ cd /vagrant
$ rails new first_app
$ cd first_app
$ rails server
```

Then on your computer, open a web browser and visit http://localhost:3000. You should see the rails "Welcome aboard" page.

## Working on your rails project

If you follow the procedure above, your files are stored both on your local computer and within your railsbox. You can edit them in either place and Vagrant will keep things in sync.

On your computer the files are stored in the same directory that contains your Vagrant file.

In your railsbox, the files are stored at `/vagrant`.
