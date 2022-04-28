## Welcome to Docs

This module was created for convenient work with the GitHub repository. Create a cloud database from a regular GitHub repository to store information in json files.

### Get started

First you need to install the library:
`pip install db-kirosake`
`pip3 install db-kirosake`

Let's start setting up the working environment itself:
> First you need to create a private repository in which your database will be located.
> After that, in your profile, you must create an access token that will be used to connect to your account.

```py
# setting in the file itself test.py
from dbkirosake import DBKirosake
DB=DBKirosake(
    actoken, # your access token
    't1rxdqq/test' #this repository
)
```

### Data methods
#### create_db

| FIELD    | TYPE | DESCRIPTION                           |
|----------|------|---------------------------------------|
| nameDB   | str  | name your database                    |
| folder   | str  | folder where the data file is located |
| ids      | str  | get information for id in file        |
| database | dict | structure for data storage            |

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

#### insert_one

| FIELD  | TYPE          | DESCRIPTION                                        |
|--------|---------------|----------------------------------------------------|
| nameDB | str           | name your database                                 |
| folder | str           | folder where the data file is located              |
| ids    | str           | get information for id in file                     |
| insert | str           | specify what to change                             |
| value  | str/int/float | data to be entered                                 |
| method | str           | method to entered ('r' or 'a'; 'replace' or 'add') |

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
