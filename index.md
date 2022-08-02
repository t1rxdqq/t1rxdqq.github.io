## Welcome to Docs kiroDB

**kiroDB** - is a small cloud database created for use in your Python projects.

### Get started

First you need to install the library

`pip install kirodb`

or

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

Token and cluster can be created on the [official website](https://kirodb.herokuapp.com/)

The library has two classes - **kiro or asynckiro**
They are similar methods, but the difference is in the function call.

**kiro** - can be used in absolutely any code.

**asynckiro** - only in asynchronous functions.

#### get() - returns information on the given key

| FIELD      | TYPE | DESCRIPTION                           |
|:-----------:|:----:|---------------------------------------|
| `key`   | str  | key to search for data in the cluster if `None` return all data                     |

```py
db.get(key="...")
```

#### get_sort() - returns sorted data

| FIELD      | TYPE | DESCRIPTION                           |
|:------------:|:----:|---------------------------------------|
| `key`   | str  | key to sorted                    |
| `reverse` | boolean | method sort from largest to smallest|

```py
db.get_sort(key="...", reverse=True)
```

#### insert_one() - insert to database 1 data

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

#### insert_many() - update multiple keys on an object

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

#### create_data() - creates an object with the specified data in your cluster

| FIELD    | TYPE          | DESCRIPTION                                          |
|:---------:|:-------------:|------------------------------------------------------|
| `id` | str           | identification name of your object in the cluster                                   |
| `data` | dict           | assigns data to an object                 |

```py
dictionary={
    "username": "Carlos"
    "age": 22,
    "cash": 45.95
}
db.create_data(
    id="...", data=dictionary
)
```

#### delete_data() - removes an object from your cluster 

| FIELD    | TYPE          | DESCRIPTION                                          |
|:---------:|:-------------:|------------------------------------------------------|
| `id` | str           | identification name of your object in the cluster                                   |

```py
db.delete_data(
    id="..."
)
```

#### cluster_info() - will return basic information about your cluster

```py
info=db.cluster_info()
```
                
