## Welcome to Docs kiroDB

**kiroDB** - is a small cloud database created for use in your Python projects.

### Get started

First you need to install the library

`pip install kirodb`

`pip3 install kirodb`

**Connect your cluster.**
```py
from kirodb import kiro

TOKEN="..." # your token
CLUSTER="..." # name your cluster

db=kiro.Connect(
    TOKEN, CLUSTER
)
...
```

The library has two classes - **kiro or asynckiro**
They are similar methods, but the difference is in the function call.

**kiro** - can be used in absolutely any code.

**asynckiro** - only in asynchronous functions.

#### get - returns information on the given key

| FIELD      | TYPE | DESCRIPTION                           |
|:-----------:|:----:|---------------------------------------|
| `key`   | str  | key to search for data in the cluster if `None` return all data                     |

```py
db.get(key="...")
```

#### get - returns sorted data

| FIELD      | TYPE | DESCRIPTION                           |
|:------------:|:----:|---------------------------------------|
| `key`   | str  | key to sorted                    |
| `reverse` | boolean | method sort from largest to smallest|

```py
db.get_sort(key="...", reverse=True)
```

#### insert_one - insert to database 1 data

| FIELD    | TYPE          | DESCRIPTION                                          |
|:----------:|:-------------:|------------------------------------------------------|
| `id`    | str           | object in your cluster                    |
| `key` | str           | key in your object data                          |
| `data`  | str/int/float | data to be entered                                   |
| `method` | str           | method to entered `('r' or 'a')` **r - replace, a - append** |

```py
db.insert_one(
    id="...", key="...",
    data="...", method="r"
)
```

#### insert_many - update multiple keys on an object

| FIELD     | TYPE            | DESCRIPTION                                          |
|:-----------:|:---------------:|------------------------------------------------------|
| `id`  | str             | object in your cluster                                   |
| `data`  | dict             | set of keys with new data and recording methods, see example                |

```py
dictionary={
    "username": ("Carlos", "r"), # overwrites the value of the key "Carlos"
    "age": (1, "a") # adds a value to the "age" key
}
db.insert_many(
   id="...", data=dictionary
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
