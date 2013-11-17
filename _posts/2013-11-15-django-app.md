---
layout: article
title: Building a Django App
published: true
categories: [tutorials, django]
---

This article covers building a Django application on [Nitrous.IO](http://www.nitrous.io) with Python 3.3.

### Prerequisites

* A [Nitrous.IO account](https://www.nitrous.io)
* A [Box](http://help.action.io/customer/portal/articles/802603-create-a-box) on Nitrous.IO. The Django box template will include Python 2.7 with the use of Virtualenv.

### Creating a isolated environment with Virtualenv

Virtualenv allows you to create an isolated environment in order to install specific versions and dependencies.

To view the available versions of Python available, run `ls /usr/bin/python*`. Create a new environment with Python 3.3 by running the following 2 commands:

    $ virtualenv -p /usr/bin/python2.7 py27env

You will now want to connect to this environment:
    
    $ source py27env/bin/activate

Since you are in a isolated environment, you will need to install Django and any other dependencies that were available outside of your environment. You can check which modules are installed with `pip freeze`, and you will want to install Django if not available:

    $ pip install django

>If you decide you want to disconnect from this environment at any point, type `deactivate` in the console.

### Creating a new project

For this example, we will first want to create a project. You can create multiple apps within the project, but we will get to that later. cd into your `~/workspace/` folder and run the following command to create a new project:

    $ django-admin.py startproject mysite

This will setup a new project within the `mysite/` folder. Navigate into this folder by running `cd mysite/`. You can now test out your site by running the following command:

    $ python manage.py runserver 0.0.0.0:3000

After a moment you should see that the app is running on port 3000. Navigate in the menu bar to **Preview > Port 3000**.

![Preview Port 3000](/images/articles/preview-port-3000.png)

>Note: To preview apps on Nitrous.IO, you will need to ensure it is running with the host 0.0.0.0 instead of localhost/127.0.0.1. You can also run it on any port between 1024 - 9999.

### Configuring MySQL (Optional)

The Django project is configured to use SQLite by default, but you can change this to use other databases such as MySQL and PostgreSQL. If you you want to go the MySQL route, you will first need to install it. Nitrous offers a package manager, [Autoparts](/autoparts/), which will allow you to install [MySQL](http://help.nitrous.io/mysql/) directly on your Nitrous box. Run the following command to install MySQL:

    $ parts install mysql

Once installed, start up MySQL:

    $ parts start mysql

Next, install the mysql-python library next for Python 2.7. Python 3.x is not supported for this library at the time this article was written.

    $ pip install mysql-python

Open `mysite/settings.py` in the editor and adjust the database configurations as seen below:

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.mysql',
            'NAME': 'mysite',
            'USER': 'root',
        		'HOST': '0.0.0.0',
        }
    }

Once the changes have been saved, run the MySQL console and create a new database:

    $ mysql -u root
    mysql> CREATE DATABASE mysite;
    mysql> quit;

Next, create the tables for the installed apps (found in `mysite/settings.py`) by running the following command within your project folder:

    $ python manage.py syncdb

If all runs smoothly you should see the following lines after running the command. When prompted to setup a superuser, select yes and remember the credentials you use. You will use these later.

    Creating tables ...
    Creating table django_admin_log
    Creating table auth_permission
    Creating table auth_group_permissions
    Creating table auth_group
    Creating table auth_user_groups
    Creating table auth_user_user_permissions
    Creating table auth_user
    Creating table django_content_type
    Creating table django_session

    You just installed Django's auth system, which means you don't have any superusers defined.
    Would you like to create one now? (yes/no): yes

### Creating an App

You already have the project `mysite` setup, along with an established database. This section will summarize part 1 and 2 of [Djangoproject's tutorial](https://docs.djangoproject.com/en/dev/intro/tutorial01/) to help you get started with it on Nitrous, but we strongly encourage you to follow that tutorial for the best learning experience. 

Let's create a polls app by navigating into the `/mysite` folder and running the following command:

    python manage.py startapp polls

Within `~/workspace/mysite/polls/models.py` define the models by replacing the existing code with the following:

    from django.db import models

    class Question(models.Model):
        question_text = models.CharField(max_length=200)
        pub_date = models.DateTimeField('date published')

    class Choice(models.Model):
        question = models.ForeignKey(Question)
        choice_text = models.CharField(max_length=200)
        votes = models.IntegerField(default=0)

You will need to add the blog app to your project. To to this, edit `mysite/settings.py` and include the string 'polls' within the INSTALLED_APPS setting:

    INSTALLED_APPS = (
	    'django.contrib.admin',
	    'django.contrib.auth',
	    'django.contrib.contenttypes',
	    'django.contrib.sessions',
	    'django.contrib.messages',
	    'django.contrib.staticfiles',
	    'polls',
    )

Build the necessary tables for the polls model by running syncdb within the project folder again:

    python manage.py syncdb

You will also need to add the polls app with question and choice objects to the admin page. Edit `polls/admin.py`, and replace the content with the following:

    from django.contrib import admin
    from polls.models import Choice, Question


    class ChoiceInline(admin.StackedInline):
        model = Choice
        extra = 3


    class QuestionAdmin(admin.ModelAdmin):
        fieldsets = [
            (None,               {'fields': ['question_text']}),
            ('Date information', {'fields': ['pub_date'],
                                  'classes': ['collapse']}),
        ]
        inlines = [ChoiceInline]

    admin.site.register(Question, QuestionAdmin)

>If you want a more in depth explanation on how the `polls/admin.py` builds the admin form, read the tutorial at [djangoproject.com](https://docs.djangoproject.com/en/dev/intro/tutorial02/).

### Connecting to the app

Run your project again with the following command:

    python manage.py runserver 0.0.0.0:3000

Navigate in the menu bar to **Preview > Port 3000**, and add `/admin` to the end of the URL within the address bar. You should see the login page below.

![Django Admin Login](/images/articles/django-admin-login.png)

Use the superuser login credentials you created earlier. If you did not select your own username then the default is `action`, and the password was created by you when running syncdb.

![Django Admin Page](/images/articles/django-admin-page.png)

Once you are in the Admin section, click **Questions** within the Polls section. Add a question to this section along with 3 choices, and save your changes.

![Django Poll Admin](/images/articles/django-poll-admin.png)

You have now built your fist question within the app. 

At this point you have configured an app which utilizes [MySQL](/mysql/) and has the admin section established. You should be familiar with [Autoparts](/autoparts/), Virtualenv, and how to [preview](/preview/) your app on Nitrous. To learn about the next steps on creating the public interface, jump back to [part 3](https://docs.djangoproject.com/en/dev/intro/tutorial03/) of DjangoProject's guide.

### Deployment

To deploy to production, we recommend using [Google App Engine](https://developers.google.com/appengine/). To learn how to deploy to App Engine, take a look at our [deployment guide](http://help.nitrous.io/app-engine/).
