# CTON

CTON 源自 CSV、HTTP、JSON，学习参考了 Markdown，它是一种轻量级的数据交换格式。

## 1 例子

### 1.1 不包含嵌套

#### 1.1.1 Markdown 格式

| id  | name         | age |
| :-: | :----------- | --: |
|  1  | adam         |  28 |
|  2  | caichongjian |  28 |
|  3  | ccj          |  28 |

#### 1.1.2 CSV 格式

- 数据中不包含分隔符：`id,name,age\n1,adam,28\n2,caichongjian,28\n3,ccj,28\n`
- 数据中包含分隔符：`id,name,age\n1,adam,28\n2,"cai\nchongjian",28\n3,"c,cj",28\n`

#### 1.1.3 JSON 格式(压缩前)

```json
[
  {
    "id": 1,
    "name": "adam",
    "age": 28
  },
  {
    "id": 2,
    "name": "caichongjian",
    "age": 28
  },
  {
    "id": 3,
    "name": "ccj",
    "age": 28
  }
]
```

#### 1.1.4 CTON 格式

- 数据中不包含分隔符：`id\t\tname\t\tage\r\n\n1\t\tadam\t\t28\r\n\n2\t\tcaichongjian\t\t28\r\n\n3\t\tccj\t\t28\r\n\n`
- 数据中包含`,`或`\n`：`id\t\tname\t\tage\r\n\n1\t\tadam\t\t28\r\n\n2\t\tcai\nchongjian\t\t28\r\n\n3\t\tc,cj\t\t28\r\n\n`

### 1.2 包含嵌套

JSON 原生支持嵌套。  
可以在 CSV、CTON 单元格内使用 JSON 字符串；可以在 JSON 中使用 CSV、CTON 字符串。

## 2 优缺点

### 2.1 优点

CTON 只在极少数极端的情况下有微不足道的优势，建议大家谨慎谨慎谨慎使用。

### 2.2 缺点

CTON 有以下缺点：

- 难以在编辑器中手写
- 难以阅读
- 数据量少时比 CSV 和 JSON 占用更多的空间
- 数据量多时比 CSV 占用更多的空间
- 格式比 JSON 死板，格式复杂的数据不适合用 CTON
- 在数据中包含"\t\t"及"\r\n\n"时需要程序员转义成其他字符；可能存在注入漏洞
- 用户输入数据时在文本框末尾加了个"\t"符号需要程序员处理一下
- 单元格中 null、"null"、空字符串不太好处理，且为空时占用更多的空间
- 其他未知的缺点

## 3 许可证

MIT  
截止到目前为止我没有获得 CSV、HTTP、JSON、Markdown 的授权。如有侵权，请联系我的电子邮箱，我会尽快删除 Git 仓库。
