# Simple Python 3, Django 1.8 Server
Use this Vagrant & Ansible setup to quickly spin up an Ubuntu 14.04.3 server with Python 3 and Django 1.8 already installed in a virtual environment.

## Installation
We need to install a few things first:    
- [VirtualBox](https://www.virtualbox.org) (v5.0.2 at the time of writing)
- [Vagrant](https://www.vagrantup.com/) (v1.7.4 at the time of writing)
- [Ansible](http://www.ansible.com/) (v.1.9.2 at the time of writing)

Once the above prerequisites have been installed, copy the following files and directories from this repo:
````bash
/project
/provision
requirements.txt
Vagrantfile
````
to the directory where you want your Django project to live (e.g `~/sites/demo-django-project`.)

`cd` into your project directory and run `vagrant up`. This will initialize the Vagrant box, configure the server and install our Python dependencies.

Once the Vagrant installation is done, connect to the box via `vagrant ssh`. Your terminal prompt should look similar to `(default) vagrant@vagrant-ubuntu-trusty-64:~$`. That `(default)` part at the beginning means that the `default` virtual environment is active. You can deactivate it via the `deactivate` command. You can reactivate it via `source ~/.virtualenvs/default/bin/activate`, or by logging back into the Vagrant box.

## Start a new Django project
The Django project should live within the virtual server's `~/project` directory.    
````bash
cd ~/project
django-admin startproject my_django_project
cd my_django_project
````

Use the `runserver` alias to start a Django development server. `runserver` is just a shortcut to `python3 manage.py runserver 0.0.0.0:8000`. We bind the server address to `0.0.0.0` so that we may access it from our host machine.

From your host machine, open `http://127.0.0.1:8001/` in a browser (notice the port is **8001**, not 8000) and you should see a page that says "*It worked! Congratulations on your first Django-powered page.*"

Now you can start building your Django project, knowing that it's entirely self-contained within a virtual environment and a virtual server.