新版path有语义，更容易理解，虽然语法复杂一些，选择了对象或者数组，一目了然。

```
{
    "store": {
        "book": [
            {
                "category": "reference",
                "author": "Nigel Rees",
                "title": "Sayings of the Century",
                "price": 8.95
            },
            {
                "category": "fiction",
                "author": "Evelyn Waugh",
                "title": "Sword of Honour",
                "price": 12.99
            },
            {
                "category": "fiction",
                "author": "Herman Melville",
                "title": "Moby Dick",
                "isbn": "0-553-21311-3",
                "price": 8.99
            },
            {
                "category": "fiction",
                "author": "J. R. R. Tolkien",
                "title": "The Lord of the Rings",
                "isbn": "0-395-19395-8",
                "price": 22.99
            }
        ],
        "bicycle": {
            "color": "red",
            "price": 19.95
        }
    },
    "expensive": 10
}
```

| 新版()                                     | 原版(xmlpath)                          |
| ------------------------------------------ | -------------------------------------- |
| ${'store':{'book'}}[*]{'author'}           | $.store.book[*].author                 |
| ${'*'}{'author'}                           | $.*.author                             |
| ${'store'}                                 | $.store.*                              |
| ${'store','expensive'}                     | //                                     |
| ${'store':{'book'}}[2]                     | $.store.book[2]                        |
| ${'store':{'book'}}[-2]                    | $.store.book[-2]                       |
| ${'store':{'book'}}[0,1]                   | $.store.book[0,1]                      |
| ${'store':{'book'}}[:2]                    | $.store.book[:2]                       |
| ${'store':{'book'}}[1:2]                   | $.store.book[1:2]                      |
| ${'store':{'book'}}[-2:]                   | $.store.book[-2:]                      |
| ${'store':{'book'}}[2:]                    | $.store.book[2:]                       |
| ${'store':{'book'}}[?(@.isbn)]             | $.store.book[?(@.isbn)]                |
| ${'store':{'book'}}[?(@.price<10)]         | $.store.book[?(@.price < 10)]          |
| ${'*'}{'book'}[2]                          | $.*.book[2]                            |
| ${'*'}{'book'}[-2]                         | $.*.book[-2]                           |
| ${'*'}{'book'}[0,1]                        | $.*.book[0,1]                          |
| ${'*'}{'book'}[:2]                         | $.*.book[:2]                           |
| ${'*'}{'book'}[1:2]                        | $.*.book[1:2]                          |
| ${'*'}{'book'}[-2:]                        | $.*.book[-2:]                          |
| ${'*'}{'book'}[2:]                         | $.*.book[2:]                           |
| ${'*'}{'book'}[?(@.isbn)]                  | $.*.book[?(@.isbn)]                    |
| ${'*'}{'book'}[?(@.price<=$['expensive'])] | $.*.book[?(@.price <= $['expensive'])] |
| ${'*'}{'book'}[?(@.author=~/.*REES/i)]     | $.*.book[?(@.author =~ /.*REES/i)]     |
| ${'*'}                                     | $.*                                    |
| ${'*'}{'book'}[*].length()                 | $.*.book.length()                      |

```
[
    {
        "category":"reference",
        "author":"Nigel Rees",
        "title":"Sayings of the Century",
        "price":8.95
    },
    {
        "category":"fiction",
        "author":"Evelyn Waugh",
        "title":"Sword of Honour",
        "price":12.99
    },
    {
        "category":"fiction",
        "author":"Herman Melville",
        "title":"Moby Dick",
        "isbn":"0-553-21311-3",
        "price":8.99
    },
    {
        "category":[
            {
                "category":"reference",
                "author":"Nigel Rees",
                "title":"Sayings of the Century",
                "price":8.95
            },
            {
                "category":"fiction",
                "author":"Evelyn Waugh",
                "title":"Sword of Honour",
                "price":12.99
            },
            {
                "category":"fiction",
                "author":"Herman Melville",
                "title":"Moby Dick",
                "isbn":"0-553-21311-3",
                "price":8.99
            },
            {
                "category":"fiction",
                "author":"J. R. R. Tolkien",
                "title":"The Lord of the Rings",
                "isbn":"0-395-19395-8",
                "price":22.99
            }
        ],
        "author":"J. R. R. Tolkien",
        "title":"The Lord of the Rings",
        "isbn":"0-395-19395-8",
        "price":22.99
    }
]
```

| 新版()                                         | 原版(xmlpath)                          |
| ---------------------------------------------- | -------------------------------------- |
| $[3]{'category'}[*].author                     | $.store.book[*].author                 |
| $['*']{'author'}                               | $.*.author                             |
| $[3]                                           | $.store.*                              |
| $[3]{'category'}[*]                            | //                                     |
| $[3]{'category'}[2]                            | $.store.book[2]                        |
| $[3]{'category'}[-2]                           | $.store.book[-2]                       |
| $[3]{'category'}[0,1]                          | $.store.book[0,1]                      |
| $[3]{'category'}[:2]                           | $.store.book[:2]                       |
| $[3]{'category'}[1:2]                          | $.store.book[1:2]                      |
| $[3]{'category'}[-2:]                          | $.store.book[-2:]                      |
| $[3]{'category'}[2:]                           | $.store.book[2:]                       |
| $[3]{'category'}[?(@.isbn)]                    | $.store.book[?(@.isbn)]                |
| $[3]{'category'}[?(@.price<10)]                | $.store.book[?(@.price < 10)]          |
| $['*']{'category'}[2]                          | $.*.book[2]                            |
| $['*']{'category'}[-2]                         | $.*.book[-2]                           |
| $['*']{'category'}[0,1]                        | $.*.book[0,1]                          |
| $['*']{'category'}[:2]                         | $.*.book[:2]                           |
| $['*']{'category'}[1:2]                        | $.*.book[1:2]                          |
| $['*']{'category'}[-2:]                        | $.*.book[-2:]                          |
| $['*']{'category'}[2:]                         | $.*.book[2:]                           |
| $['*']{'category'}[?(@.isbn)]                  | $.*.book[?(@.isbn)]                    |
| $['*']{'category'}[?(@.price<=$['expensive'])] | $.*.book[?(@.price <= $['expensive'])] |
| $['*']{'category'}[?(@.author=~/.*REES/i)]     | $.*.book[?(@.author =~ /.*REES/i)]     |
| $['*']                                         | $.*                                    |
| $['*']{'category'}[*].length()                 | $.*.book.length()                      |

