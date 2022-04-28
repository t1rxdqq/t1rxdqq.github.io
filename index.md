## Welcome to Docs

This module was created for convenient work with the GitHub repository. Create a cloud database from a regular GitHub repository to store information in json files.

### Get started

First you need to install the library

`pip install db-kirosake`

`pip3 install db-kirosake`

Let's start setting up the working environment itself:
> First you need to create a private repository in which your database will be located.

> After that, in your profile, you must create an access token that will be used to connect to your account.

```py
# setting in the file itself test.py
from db_kirosake import dbkirosake
DB=dbkirosake.DBKirosake(
    actoken, # your access token
    't1rxdqq/test' #this repository
)
```

### Data methode

#### create_db - create database in your repository

| FIELD      | TYPE | DESCRIPTION                           |
|------------|:----:|---------------------------------------|
| `nameDB`   | str  | name your database                    |
| `folder`   | str  | folder where the data file is located |
| `ids`      | str  | get information for id in file        |
| `database` | dict | structure for data storage            |

```py
db={
    'lvl':1,
    'cash':10
}
await DB.create_db(
    nameDB='test',
    folder='01',
    ids='001',
    database=db
)
```

#### insert_one - insert to database 1 data

| FIELD    | TYPE          | DESCRIPTION                                          |
|----------|:-------------:|------------------------------------------------------|
| `nameDB` | str           | name your database                                   |
| `folder` | str           | folder where the data file is located                |
| `ids`    | str           | get information for id in file                       |
| `insert` | str           | specify what to change                               |
| `value`  | str/int/float | data to be entered                                   |
| `method` | str           | method to entered `('r' or 'a'; 'replace' or 'add')` |

```py
await DB.insert_one(
    nameDB='test',
    folder='01',
    ids='001',
    insert='lvl',
    value=10,
    method='r'
    )
```

#### insert_many - insert to database 2 or many data

| FIELD     | TYPE            | DESCRIPTION                                          |
|-----------|:---------------:|------------------------------------------------------|
| `nameDB`  | str             | name your database                                   |
| `folder`  | str             | folder where the data file is located                |
| `ids`     | str             | get information for id in file                       |
| `inserts` | dict            | specify what to change                               |

```py
await DB.insert_many(
    nameDB='test',
    folder='01',
    ids='001',
    inserts={'lvl':88,'cash':250}
    )
```

#### get - return database

| FIELD    | TYPE          | DESCRIPTION                                          |
|----------|:-------------:|------------------------------------------------------|
| `nameDB` | str           | name your database                                   |
| `folder` | str           | folder where the data file is located                |
| `ids`    | str           | get information for id in file                       |

```py
data=await DB.get(
    nameDB='test',
    folder='01',
    ids='001',
    )
print(data)
```

#### get_sorted - return sorted database

| FIELD     | TYPE          | DESCRIPTION                             |
|-----------|:-------------:|-----------------------------------------|
| `nameDB`  | str           | name your database                      |
| `folder`  | str           | folder where the data file is located   |
| `key`     | str           | data to be sorted                       |
| `reverse` | str           | sort method                             |

```py
data=await DB.get_sorted(
    nameDB='test',
    folder='01',
    key='cash',
    reverse=True
    )
print(data)
```

#### datainfo - return size and length database

| FIELD    | TYPE          | DESCRIPTION                                          |
|----------|:-------------:|------------------------------------------------------|
| `nameDB` | str           | name your database                                   |
| `folder` | str           | folder where the data file is located                |
| `ids`    | str           | get information for id in file                       |

```py
data=await DB.datainfo(
    nameDB='test',
    folder='01',
    ids='001'
    )
print(data)
```
