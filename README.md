Server IP address : 13.126.98.37
Server SSH Port : 2200

URL for Item-Catalog project : http://13.126.98.37/catalog

SUMMARY OF SOFTWARES INSTALLED:-

Apache2
	Installed apache2 server using the command
	sudo apt-get install apache2

mod_wsgi
	Installed mod_wsgi for apache2 using command
	sudo apt-get install libapache2-mod-wsgi

Postgresql
	Installed Postgresql database using command
	sudo apt-get install postgresql

Python-pip
	Installed Python-pip installer using command
	sudo apt-get install python-pip

Virtualenv
	Installed virtualenv virtual environment for the project using command
	sudo pip install virtualenv
	
__Some libraries for python required for Item catalog project__

Flask
	Installed Flask using command
	sudo pip install flask
	
Sqlalchemy
	Installed sqlalchemy using command
	sudo pip install sqlalchemy
	
Requests
	Installed requests using command
	sudo pip install requests

oauth2client
	Installed oauth2client for google sign in using command
	sudo pip install oauth2client
	
CONFIGURATION CHANGES:-

- Added file named item-catalog.conf to the path /etc/apache2/sites-available containing following code

		<VirtualHost *:80>
                ServerName localhost
                ServerAdmin pawanpsharma1996@gmail.com
                WSGIScriptAlias / /var/www/itemCatalog/itemCatalog.wsgi
                <Directory /var/www/itemCatalog/itemCatalog/>
                        Order allow,deny
                        Allow from all
                </Directory>
                Alias /static /var/www/itemCatalog/itemCatalog/static
                <Directory /var/www/itemCatalog/itemCatalog/static/>
                        Order allow,deny
                        Allow from all
                </Directory>
                ErrorLog logs/error.log
                LogLevel warn
                CustomLog ${APACHE_LOG_DIR}/access.log combined
		</VirtualHost>

for this I have to make a logs folder in /etc/apache2 directory and make a file named error.log so that it can provide all the error logs.

Then to enable this this project in Apache2 server following command is used
sudo a2ensite item-catalog
and to disable the default website following command is used
sudo a2dissite 000-default.conf

Restarting apache now should run the project on the above given URL.

LOCATION OF SSH KEY FOR USER 'grader'
/home/grader/.ssh/authorized_keys




