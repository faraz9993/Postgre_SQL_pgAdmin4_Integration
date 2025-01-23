# PostgreSQL Installtion and Integration with pgAdmin4

### Commands for installing PostgreSQL 15 on Ubuntu Machine

```
sudo apt install wget ca-certificates

wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo tee /etc/apt/trusted.gpg.d/postgresql.asc

echo "deb https://apt.postgresql.org/pub/repos/apt/ $(lsb_release -c | awk '{print $2}')-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list

sudo apt update

sudo apt install postgresql-15 postgresql-client-15

psql --version

sudo systemctl start postgresql

sudo systemctl enable postgresql

sudo systemctl status 'postgresql*'
```

### Next step is to allow incoming traffic to the PostgreSQL database anywhere from the network. For that you have to make changes in the configuration file of PostgreSQL.

```
sudo vim /etc/postgresql/15/main/postgresql.conf
```

### Make below changes:

```
Connection Settings -
listen_addresses = '*'          # what IP address(es) to listen on;
```
### Now, let us login into PostgreSQL DATABASE, create a password for admin, create a user, assign that user a username and password, create a datbase and grant its privileges to that newly created user.

```
sudo -i -u postgres
psql
```
### Accessing a Postgres Prompt Without Switching Accounts:
```
sudo -u postgres psql
```
### Commands to run in the database:
```

ALTER USER postgres WITH PASSWORD 'postgres@123';

CREATE USER faraz WITH PASSWORD 'faraz@123';
 
CREATE DATABASE test_database;
GRANT ALL PRIVILEGES ON DATABASE test_database TO faraz;
```
### Now, next is the configuration of pgAdmin4.
### Installing pgAdmin4

```
curl -fsS https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo gpg --dearmor -o /usr/share/keyrings/packages-pgadmin-org.gpg

sudo sh -c 'echo "deb [signed-by=/usr/share/keyrings/packages-pgadmin-org.gpg] https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'
```
### Install pgAdmin4 for both desktop and web modes:
```
sudo apt-get install pgadmin4
```

### Install pgAdmin4 for desktop mode only:
```
sudo apt-get install pgadmin4-desktop
```

### Install for web mode only:
```
sudo apt-get install pgadmin4-web 
```

### These steps will download pgAdmin4 tool in your machine. Now, open the tool and on the main page click on Add New Server.
#### Go to "General" section:
```
Name: Faraz-Server
```
#### Go to "Connection" section:
```
Hostname: localhost
Port: 5432
Maintainance database: postgres
Username: postgres     or     faraz
Password: postgres@123      or      faraz@123
SAVE
```

### Now, you will be able to see all the databases in pgAdmin4. For that, click on Server in left-side panel. Faraz-Server > Databases > test_database

### Now, to change the privileges of user:

### Servers > Faraz-Server > Login/Group Roles > faraz (Right Click) > Properties > Privileges

### To access the pgAdmin4 tool on the broswer, go to pgAdmin4 tool > File > View Logs > scroll down in the logs page.

### You will see 
```
Application Server URL: http://127.0.0.1:43317/?key=xxxxx-xxxxx-xxxxx-xxxxx-xxxxx-xxxxx
```
### Open this URL in the browser, it will ask for the passord of the user. Enetr the password.