# Postgre_SQL_pgAdmin4_Integration

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

vim /etc/postgresql/15/main/postgresql.conf
```

### Next step is to allow incoming traffic to the PostgreSQL anywhere from the network. For that you have to make changes in the configuration file of postgresql.

```
sudo vim /etc/postgresql/15/main/postgresql.conf
```

### Make below changes:

```
Connection Settings -
listen_addresses = '*'          # what IP address(es) to listen on;
```
### Now, let us login into PostgreSQL, create an admin password, a user, that user's username and password, a datbase and grant its privileges to the newly created user.

```
sudo -i -u postgres
psql
```
### Accessing a Postgres Prompt Without Switching Accounts:
```
sudo -u postgres psql

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

### These step will download pgAdmin4 tool in your machine. Now, open the tool. On the main page click on Add New Server
## General
```
Name: Faraz-Server
```
## Connection:
```
Hostname: localhost
Port: 5432
Maintainance database: postgres
Username: postgres     or     faraz
Password: postgres@123      or      faraz@123
SAVE
```

### Clck on Server in left-side panel. Faraz-Server > Databases > test_database

### To change the privileges of user:

### Servers > Faraz-Server > Login/Group Roles > faraz (Right Click) > Properties > Privileges