sudo apt -y install wget unzip
Now download daloRADIUS and cd into the newly created daloradius-1.3 folder:

wget https://github.com/lirantal/daloradius/archive/1.3.zip
unzip 1.3.zip
cd daloradius-1.3
Populate the database with the daloRADIUS schema:

sudo mysql -u root -p radius < contrib/db/fr2-mysql-daloradius-and-freeradius.sql
sudo mysql -u root -p radius < contrib/db/mysql-daloradius.sql
cd out of the daloradius-1.3 directory, and move the folder into the document root as daloradius:

cd ..
sudo mv daloradius-1.3 /var/www/html/daloradius
Next, we’ll change the owner and group for the daloradius folder to www-data:www-data, which are the user and group under which the Apache Web Server runs.

sudo chown -R www-data:www-data /var/www/html/daloradius/
Now, we’ll need to create the daloRADIUS configuration file. Right now, we’re just provided a sample file, so we’ll make a copy from that sample file:

sudo cp /var/www/html/daloradius/library/daloradius.conf.php.sample /var/www/html/daloradius/library/daloradius.conf.php
We’ll also change the permissions for the daloRADIUS configuration file:

sudo chmod 664 /var/www/html/daloradius/library/daloradius.conf.php
Next, we edit a few variables in the daloRADIUS connection file so it can connect to the FreeRADIUS database.

Open the configuration file using your favorite editor:

sudo nano /var/www/html/daloradius/library/daloradius.conf.php
Similarly to what we’ve done earlier when editing the FreeRADIUS config file, we need to adjust the variables for the database user, their password, and the database name. Those are all the edits for the scope of this tutorial.

This is how they initially look in the daloRADIUS configuration file:

$configValues['CONFIG_DB_USER'] = 'root';
$configValues['CONFIG_DB_PASS'] = '';
$configValues['CONFIG_DB_NAME'] = 'radius';
This is how it looks after editing the details for the database I created earlier:

$configValues['CONFIG_DB_USER'] = 'radius';
$configValues['CONFIG_DB_PASS'] = 'Somestrongpassword_321';
$configValues['CONFIG_DB_NAME'] = 'radius'
Lastly, restart FreeRADIUS and Apache to make sure everything works:

sudo systemctl restart freeradius.service apache2
