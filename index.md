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


- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/t1rxdqq/t1rxdqq.github.io/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
