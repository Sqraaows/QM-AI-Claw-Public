# Database Commands

**Source**: Custom workspace skill

SQL queries and database management commands.

## PostgreSQL

```bash
# Connect
psql -U username -d database
psql -h localhost -p 5432 -U user -d db

# Commands
\l              # List databases
\dt             # List tables
\d table_name   # Describe table
\du             # List users
\di             # List indexes
\df             # List functions

# Query
SELECT * FROM users LIMIT 10;
SELECT name, email FROM users WHERE active = true;
INSERT INTO users (name, email) VALUES ('John', 'john@example.com');
UPDATE users SET active = false WHERE id = 1;
DELETE FROM users WHERE id = 1;

# Export
pg_dump -U user -d dbname > backup.sql
pg_dump -U user -d dbname --table=users > users.sql

# Import
psql -U user -d dbname < backup.sql
```

## MySQL

```bash
# Connect
mysql -u root -p
mysql -h localhost -u user -p dbname

# Commands
SHOW DATABASES;
USE database_name;
SHOW TABLES;
DESCRIBE table_name;
SHOW COLUMNS FROM table_name;

# Query
SELECT * FROM users LIMIT 10;
SELECT COUNT(*) FROM users;
INSERT INTO users (name, email) VALUES ('John', 'john@example.com');

# Export
mysqldump -u root -p dbname > backup.sql
mysqldump -u root -p dbname table_name > table.sql

# Import
mysql -u root -p dbname < backup.sql
```

## SQLite

```bash
# Connect
sqlite3 database.db

# Commands
.databases
.tables
.schema table_name

# Query
SELECT * FROM users LIMIT 10;
.headers on
.mode column

# Export
sqlite3 database.db ".dump" > backup.sql

# Import
sqlite3 database.db < backup.sql
```

## MongoDB

```bash
# Connect
mongosh "mongodb://localhost:27017"
mongosh "mongodb://user:pass@host:27017/db"

# Commands
show dbs
use database_name
show collections

# Query
db.users.find()
db.users.find({active: true})
db.users.findOne({email: "john@example.com"})
db.users.countDocuments({active: true})

# Insert/Update
db.users.insertOne({name: "John", email: "john@example.com"})
db.users.updateOne({_id: ObjectId("...")}, {$set: {active: true}})
db.users.deleteOne({_id: ObjectId("...")})
```

## Redis

```bash
# Connect
redis-cli

# Commands
KEYS *                 # List all keys
GET key               # Get value
SET key value         # Set value
DEL key               # Delete key
EXISTS key            # Check exists

# Hash
HSET user:1 name "John"
HGET user:1 name
HGETALL user:1

# List
LPUSH list item
LRANGE list 0 -1
RPOP list

# Database
SELECT 0              # Switch db
FLUSHDB              # Clear current db
FLUSHALL             # Clear all dbs
```

---

*Install date: 2026-04-27*
