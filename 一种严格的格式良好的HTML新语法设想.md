由于历史遗留原因，HTML语法是宽松的，格式糟糕的语法forgiving bad-formed html syntax。是否需要一种更加严格的格式良好的HTML语法呢？

假设严格的格式良好的HTML语法叫SHTML，strict well-formed html syntax，属于forgiving bad-formed html syntax的子集。

例如:

shtml.shtml

```html
<!DOCTYPE shtml>
 <shtml lang="en">
  <head>
   <title>Hello</title>
  </head>
  <body id="abc1">
  <p>Welcome to this example.</p>
  </body>
</shtml>
```

```
SHTML尽可能兼容所有浏览器和解析器。
```

假设有如下结构

```html
(0)<!DOCTYPE(3)HTML>(200)(1)
 <html>
 (300) (2)
 <head>
 <!-- 注释 --> (1000)
 <title abs='abcd'>Hello</title>
 </head>
 <body>
 <!-- 注释 --> (500)
 <p>Welcome to this example.</p>
 (8)
 </body>
 (9)
 </html>
 (10)
```

骨架部分:

| forgiving bad-formed html syntax                             | strict well-formed html syntax                               |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 不区分大小写<!DOCTYPE                                        | 必须大写<!DOCTYPE                                            |
| 可选的遗留字符串                                             | 没有遗留字符串                                               |
| (0)(200) (1)任意数量的ASCII空白符(最少0个),(3)任意数量的ASCII空白符(最少1个) | (0)(200) (1)无注释和ASCII空白符，(3)1个ASCII空白符，<!DOCTYPE HTML>固定写法 |
| 建议插入换行符newline(比如200位置)                           | 必须插入换行符newline(比如200位置)，html，head，body开始和结束标签都要插入换行符newline |
| (10)任意数量的注释和ASCII空白符                              | (10)无注释和ASCII空白符，必须插入换行符newline               |
| 注释可以写在任意位置                                         | 注释写在开始标签前，并插入换行符newline(html,body,head不可以加注释) |
| 可选的BOM字符(当采用UTF-16编码传输时)                        | 不包括BOM字符                                                |
| 字符串不区分大小写(case-insensitive)                         | 必须小写(除了DOCTYPE)                                        |

