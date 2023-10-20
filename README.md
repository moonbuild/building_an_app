# building_an_app
## Steps to setup ->
#### Create & then activate Python Virtual environment:
```
python -m venv haru
source haru/bin/activate
```
#### Install necessary packages
`pip install Flask`
##### Install PostgreSQL Arch Linux
`sudo pacman -S postgres`
#### Setting up Postgres
Now after installation of postgres we need to set it up a bit
```
sudo su -postgres
initdb --locale en_US.UTF-8 -E UTF8 -D '/var/lib/postgres/data'
systemctl start postgresql
systemctl enable postgresql
```
#### Create DB and Table in Postgres
Now with this postgres is ready and set up but we need to create a database and table 
(caution dont exit yet) we are still in the postgres user 
```
psql
```
*DONT FORGET THE SEMICOLON AT THE END FROM NEXT :)*
```
CREATE DATABASE testing;
CREATE TABLE weather(
  id SERIAL PRIMARY KEY,
  city VARCHAR(255) NOT NULL,
  temp int NOT NULL
);
```
