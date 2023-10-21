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
sudo -i -u -postgres
initdb --locale en_US.UTF-8 -E UTF8 -D '/var/lib/postgres/data'
systemctl start postgresql
systemctl enable postgresql
```
start with `psql`

*"dont forget the username and password"*
in this case its ('api_dude', 'da7a')
```
psql
CREATE ROLE api_dude with password da7a;
CREATE DATABASE testing;
GRANT ALL PRIVILEGES ON DATABASE testing TO api_dude;
\c testing postgres
GRANT ALL ON SCHEMA public to api_dude;
exit
```
now end with `exit`.
#### Now lets check if everything is correct by creating a table: 
```
psql -U api_dude -d testing
CREATE TABLE weather(
  id SERIAL PRIMARY KEY,
  city VARCHAR(255) NOT NULL,
  temp int NOT NULL
);
```
