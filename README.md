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

### Next step is to allow incoming traffic to the popstgresql anywhere from the network. For that you have to make changes in the configuration file of postgresql.

```
sudo vim /etc/postgresql/15/main/postgresql.conf
```

### Make below changes:

# - Connection Settings -
```
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
```


