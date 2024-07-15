############# Odoo-Scripts##############
Important Odoo scripts (Installation, creating module, Live-server etc)


# Odoo-Installation-Script
#Odoo Installation Script (Vertual Env)

python3 -m venv odoo17_env/
cd odoo17_env/
source bin/activate 

(Download Odoo Source code from https://github.com/odoo/odoo and pest this into odoo17-env folder)

cd odoo17.0/
pip3 install wheel
pip3 install -r requirements.txt


sudo su postgres
 psql
 \du; (Optional for check)
 create user odoo17;
 alter user odoo17 with password '1234';
 alter user odoo17 with superuser createdb;
 \q
 exit

(Copy and pest conf file into odoo17.0/debian folder and give those into conf file)

[options]
db_host = localhost
db_port = 5432
db_user = odoo17
db_password = 1234
addons_path = /home/ibrahim995/odoo17_env/odoo-17.0/addons,/home/ibrahim995/odoo17_env/odoo-17.0/custom/addons
;admin_passwd = admin
http_port = 8017

(Now create custom and then addons folder under the custom folder)
to kill any runnig server command (sudo kill -9 `pidof python3`)
./odoo-bin -c odoo.conf



#After installation running odoo script
cd odoo17_env/
source bin/activate
cd odoo-17.0/
./odoo-bin -c odoo.conf





#cloudflare live server:
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64 -O cloudflared

cloudflared tunnel --url http://localhost:8017





#Scaffold command for creating custom module:
(Find path of python3 or python)
cd odoo14_env/odoo-17.0/
/home/ibrahim995/odoo17_env/bin/python3 ./odoo-bin scaffold dsl_meeting_room_m /home/ibrahim995/odoo17_env/odoo-17.0/custom/addons

