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