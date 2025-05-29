# Install and configure Postgresql

### Install postgres

##### latest
`sudo pacman -S postgresql`

##### specific version
> find version & build from source

### Check version
`postgres --version`

### Confirm psql is not running
`sudo systemctl status postgresql`  --> should not be running

### Login as the postgres user
> Note: always do this any time you are doing any type of admin work on psql

`sudo su - postgres`

### Initialize data directory
> Note: default db for psql is /var/lib/postgres/data

`initdb --locale en_US.UTF-8 -D /var/lib/postgres/data`

### Logout of **postgres** user
`exit`

### Confirm psql is still not running
`sudo systemctl status postgresql`  --> should not be running

### Start psql
`sudo systemctl start postgresql`

### Confirm psql is running
`sudo systemctl status postgresql`  --> should be active



## Create user

### 1. Access the PostgreSQL console
`sudo -iu postgres psql`

### 2. Change the postgres user password
`ALTER USER postgres WITH PASSWORD 'password';`

### 3. Create a new user with permissions
`CREATE USER name_username WITH PASSWORD 'you_password';`
`ALTER USER name_username WITH SUPERUSER CREATEDB CREATEROLE;`

### 4. Exit the PostgreSQL console
`\q`


## Another away

### Log into postgres
`sudo su - postgres`

### Create a new user
> Note: user can be called anything however if you create a PostgreSQL user with the same name as your Linux username, it allows you to access the PostgreSQL database shell without having to specify a user to login (which makes it quite convenient).

`createuser --interactive`

- Enter name of role to add: `MY_LINUX_USERNAME`
 - Shall the new role be a superuser?: `y`

### Logout of **postgres** user
`exit`

### Restart psql
`sudo systemctl restart postgresql`

### Confirm psql is running
> Note: can see that it was restarted by looking at the timestamp on the ***Active*** field

`sudo systemctl status postgresql`


