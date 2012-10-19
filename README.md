## XCMs: management console for XCP or XenServer


### Description

XCMs is a web based app for manage your XCP/XenServer pool.

It's alpha version, and distributed as is.

### Features

* Supports all modern browsers including mobile (iOS, Android)
* No need to modify pool.
* Can open multiple VNC console in same window(java applet now)
* Twitter bootstrap & jQueryUI on client side
* Python & Django on server side
* Ajax-based monitoring
* Role-based control
* Available in source and .xva appliance (see INSTALL paragraph)
* Licensed under the [MPL 2.0](http://www.mozilla.org/MPL/2.0/)

### Screenshots

<img src="https://dl.dropbox.com/u/14074890/monitoring.PNG" width=400>&nbsp;<img src="https://dl.dropbox.com/u/14074890/user_management.PNG" width=400>&nbsp;
<img src="https://dl.dropbox.com/u/14074890/vnc.PNG" width=400>

### Client Requirements

May not properly work in IE & Opera

JavaScript and coockes must be enabled

To use VNC [java jre](http://www.oracle.com/technetwork/java/javase/downloads/index.html) must be installed

### Server Requirements

python 2.* and django 1.3.1 must be installed(described in the INSTALL paragraph)


###How to install

XCMs installed like any other Django apps. Here is a example of installation on Ubuntu 10.04:

* Install Apache and mod_wsgi

	`sudo apt-get install apache2 libapache2-mod-wsgi`

* Install setup tools and pip

	`sudo apt-get install python-setuptools`&nbsp;	
	`sudo apt-get install python-pip`
	
* Install Django 1.3.1

	`sudo pip install http://pypi.python.org/packages/source/D/Django/Django-1.3.1.tar.gz#md5=62d8642fd06b9a0bf8544178f8500767`
	
* Edit ../xcms/apache/django.wsgi file: edit both path lines by path, where xcms located

* Edit settings.py file:
	**Enter name of you future db &nbsp;
	**Change TIME_ZONE,MEDIA_ROOT,TEMPLATE_DIRS accordingly with you path
	
* In xcms folder run:

	`python manage.py syncdb`
	
	Don't create user now!
	
* Now run:

	`python manage.py shell`&nbsp;
	`from xcms.customuser.models import CustomUser`&nbsp;
	`new_user = CustomUser.objects.create_user(username='yourname', email='', password='yourpassword')`&nbsp;
	`new_user.is_superuser=True`&nbsp;
	`new_user.save()`&nbsp;
	`exit()`&nbsp;
	
* Create the apache site:

	`sudo nano /etc/apache2/sites-available/xcms`
