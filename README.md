# Node Sequelize Poc

A POC using Node.js, Express.js, Sequelize.js and PostgreSQL.

## Setup

Create a user and db.

```sh
psql postgres --u postgres
```

Create a new user (zeno) with password (paradox) then give access for creating the database.

```
postgres-# CREATE ROLE zeno WITH LOGIN PASSWORD 'paradox';
postgres-# ALTER ROLE zeno CREATEDB;
postgres-# exit
```

Now login with the created user.

```sh
psql postgres -U zeno
```

Create a new DB and give all privileges to it.

```
postgres=> CREATE DATABASE secure_node;
postgres=> GRANT ALL PRIVILEGES ON DATABASE secure_node TO zeno;
postgres=> exit
```

Install npm modules and start.

```sh
cd node-sequelize-poc && npm i && npm run dev
```

Create DB tables.
```sh
sequelize db:migrate
``` 

## Test JSON Requests

POST http://localhost:3000/api/signup

```json
{ "username":"ada@lovelace.com", "password":"lovelace3301" }
```

POST http://localhost:3000/api/signin

```json
{ "username":"ada@lovelace.com", "password":"lovelace3301" }
```

POST http://localhost:3000/api/product

```json
{
    "prod_name": "Pan Galactic Gargle Blaster",
    "prod_desc": "Best Drink in Existence. Its effects are similar to having your brains smashed in by a slice of lemon wrapped round a large gold brick.",
    "prod_price": 42
}
```

GET http://localhost:3000/api/product


## Requiriments

sequelize-cli  
PostgreSQL



