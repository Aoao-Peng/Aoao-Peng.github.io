# MongoDB

## 一、NoSQL简介

### 1、什么是NoSQL?

* NoSQL，指的是非关系型的数据库。NoSQL有时也称作Not Only SQL的缩写，是对不同于传统的关系型数据库的数据库管理系统的统称。

* NoSQL用于超大规模数据的存储。（例如谷歌或Facebook每天为他们的用户收集万亿比特的数据）。这些类型的数据存储不需要固定的模式，无需多余操作就可以横向扩展。

### 2、为什么使用NoSQL ?

今天我们可以通过第三方平台（如：Google,Facebook等）可以很容易的访问和抓取数据。用户的个人信息，社交网络，地理位置，用户生成的数据和用户操作日志已经成倍的增加。我们如果要对这些用户数据进行挖掘，那SQL数据库已经不适合这些应用了, NoSQL 数据库的发展却能很好的处理这些大的数据。

### 3、CAP定理（CAP theorem）

在计算机科学中, CAP定理（CAP theorem）, 又被称作 布鲁尔定理（Brewer's theorem）, 它指出对于一个分布式计算系统来说，不可能同时满足以下三点:

- **一致性(Consistency)** (所有节点在同一时间具有相同的数据)
- **可用性(Availability)** (保证每个请求不管成功或者失败都有响应)
- **分隔容忍(Partition tolerance)** (系统中任意信息的丢失或失败不会影响系统的继续运作)

CAP理论的核心是：一个分布式系统不可能同时很好的满足一致性，可用性和分区容错性这三个需求，最多只能同时较好的满足两个。

因此，根据 CAP 原理将 NoSQL 数据库分成了满足 CA 原则、满足 CP 原则和满足 AP 原则三 大类：

- CA - 单点集群，满足一致性，可用性的系统，通常在可扩展性上不太强大。
- CP - 满足一致性，分区容忍性的系统，通常性能不是特别高。
- AP - 满足可用性，分区容忍性的系统，通常可能对一致性要求低一些。

### 4、NoSQL的优点/缺点

优点:

- \- 高可扩展性
- \- 分布式计算
- \- 低成本
- \- 架构的灵活性，半结构化数据
- \- 没有复杂的关系

缺点:

- \- 没有标准化
- \- 有限的查询功能（到目前为止）
- \- 最终一致是不直观的程序

### 5、NoSQL 数据库分类

| 类型          | 部分代表                                         | 特点                                                         |
| ------------- | ------------------------------------------------ | ------------------------------------------------------------ |
| 列存储        | HbaseCassandraHypertable                         | 顾名思义，是按列存储数据的。最大的特点是方便存储结构化和半结构化数据，方便做数据压缩，对针对某一列或者某几列的查询有非常大的IO优势。 |
| 文档存储      | MongoDBCouchDB                                   | 文档存储一般用类似json的格式存储，存储的内容是文档型的。这样也就有机会对某些字段建立索引，实现关系数据库的某些功能。 |
| key-value存储 | Tokyo Cabinet / TyrantBerkeley DBMemcacheDBRedis | 可以通过key快速查询到其value。一般来说，存储不管value的格式，照单全收。（Redis包含了其他功能） |
| 图存储        | Neo4JFlockDB                                     | 图形关系的最佳存储。使用传统关系数据库来解决的话性能低下，而且设计使用不方便。 |
| 对象存储      | db4oVersant                                      | 通过类似面向对象语言的语法操作数据库，通过对象的方式存取数据。 |
| xml数据库     | Berkeley DB XMLBaseX                             | 高效的存储XML数据，并支持XML的内部查询语法，比如XQuery,Xpath。 |

## 二、MongoDB简介

### 1、什么是MongoDB ?

* MongoDB 是由C++语言编写的，是一个基于分布式文件存储的开源数据库系统。

* 在高负载的情况下，添加更多的节点，可以保证服务器性能。

* MongoDB 旨在为WEB应用提供可扩展的高性能数据存储解决方案。

* MongoDB 将数据存储为一个文档，数据结构由键值(key=>value)对组成。MongoDB 文档类似于 JSON 对象。字段值可以包含其他文档，数组及文档数组。

### 2、主要特点

- 你可以在MongoDB记录中设置任何属性的索引 (如：FirstName="Sameer",Address="8 Gandhi Road")来实现更快的排序。
- MongoDB 是一个面向文档存储的数据库，操作起来比较简单和容易。
- MongoDb 使用update()命令可以实现替换完成的文档（数据）或者一些指定的数据字段 。
- Mongodb中的Map/reduce主要是用来对数据进行批量处理和聚合操作。
- Map和Reduce。Map函数调用emit(key,value)遍历集合中所有的记录，将key与value传给Reduce函数进行处理。
- GridFS是MongoDB中的一个内置功能，可以用于存放大量小文件。

### 3、MongoDB 下载

* 你可以在mongodb官网下载该安装包，地址为：https://www.mongodb.com/download-center#community。

* 安装前我们需要安装各个 Linux 平台依赖包。

  * **Red Hat/CentOS：**

    ```
    #yum install libcurl openssl
    ```

    ```
    
    
    ```

**MongoDB 源码下载地址：https://www.mongodb.com/download-center#community**

![img](https://www.runoob.com/wp-content/uploads/2013/10/0D72BC20-1D77-437E-972C-286EB5EFB183.jpg)



![屏幕截图 2022-04-07 164734](E:/Maven%E6%95%99%E7%A8%8B%E5%9B%BE%E7%89%87/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202022-04-07%20164734.png)选择 tgz 下载，下载完安装包，并解压 **tgz**（以下演示的是 64 位 Linux上的安装) 。

```
wget https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-rhel70-5.0.6.tgz    # 下载
tar -zxvf mongodb-linux-x86_64-rhel70-5.0.6.tgz                                    # 解压

mv mongodb-linux-x86_64-rhel70-5.0.6.tgz  /usr/local/mongodb                          # 将解压包拷贝到指定目录local下命名为mongodb
```

MongoDB 的可执行文件位于 bin 目录下，所以可以将其添加到 **PATH** 路径中（命令：vim /etc/profile)：

```
export PATH=<mongodb-install-directory>/bin:$PATH
```

**<mongodb-install-directory>** 为你 MongoDB 的安装路径。(vim /etc/profile#修改环境配置 )如本文的 **/usr/local/mongodb4* 。环境配置完毕要输入 source /etc/profile刷新

```
export PATH=/usr/local/mongodb/bin:$PATH
```

* 创建数据库目录

  默认情况下 MongoDB 启动后会初始化以下两个目录：

  - 数据存储目录：/var/lib/mongodb
  - 日志文件目录：/var/log/mongodb

  我们在启动前可以先创建这两个目录并设置当前用户有读写权限：

  ```
  sudo mkdir -p /var/lib/mongo
  sudo mkdir -p /var/log/mongodb
  sudo chown `root` /var/lib/mongo     # 设置权限
  sudo chown `root` /var/log/mongodb   # 设置权限(root指的是用户名)
  ```

  接下来在/uer/local/monfodb/bin中启动 Mongodb 服务：

  ```
  mongod --dbpath /var/lib/mongo --logpath /var/log/mongodb/mongod.log --fork
  ```

  打开 /var/log/mongodb/mongod.log 文件看到以下信息，说明启动成功。

  ```
  # tail -10f /var/log/mongodb/mongod.log
  2020-07-09T12:20:17.391+0800 I  NETWORK  [listener] Listening on /tmp/mongodb-27017.sock
  2020-07-09T12:20:17.392+0800 I  NETWORK  [listener] Listening on 127.0.0.1
  2020-07-09T12:20:17.392+0800 I  NETWORK  [listener] waiting for connections on port 27017
  ```

* 如果要停止 mongodb 可以使用以下命令：

```
mongod --dbpath /var/lib/mongo --logpath /var/log/mongodb/mongod.log --shutdown
```

​      也可以在 mongo 的命令出口中实现：

```

> use admin
switched to db admin
> db.shutdownServer()
```

* 强制删除文件或者目录：

  rm -rf 文件名

### 4、概念

| MongoDB术语/概念 | 解释/说明   |                                     |
| :--------------- | :---------- | ----------------------------------- |
| database         | database    | 数据库                              |
| table            | collection  | 数据库表/集合                       |
| row              | document    | 数据记录行/文档                     |
| column           | field       | 数据字段/域                         |
| index            | index       | 索引                                |
| table joins      |             | 表连接,MongoDB不支持                |
| primary key      | primary key | 主键,MongoDB自动将_id字段设置为主键 |

* MongoDB的默认数据库为"db"，该数据库存储在data目录中。

* 数据库也通过名字来标识。数据库名可以是满足以下条件的任意UTF-8字符串

  不能是空字符串（"")。

​        不得含有' '（空格)、.、$、/、\和\0 (空字符)。

​        应全部小写。

​        最多64字节。

|        DBMS        | MongoDB                           |
| :----------------: | :-------------------------------- |
|       数据库       | 数据库                            |
|        表格        | 集合                              |
|         行         | 文档                              |
|         列         | 字段                              |
|       表联合       | 嵌入文档                          |
|        主键        | 主键 (MongoDB 提供了 key 为 _id ) |
| 数据库服务和客户端 |                                   |
|   Mysqld/Oracle    | mongod                            |
|   mysql/sqlplus    | mongo                             |

### 5、MongoDB 数据类型

下表为MongoDB中常用的几种数据类型。

| 数据类型           | 描述                                                         |
| :----------------- | :----------------------------------------------------------- |
| String             | 字符串。存储数据常用的数据类型。在 MongoDB 中，UTF-8 编码的字符串才是合法的。 |
| Integer            | 整型数值。用于存储数值。根据你所采用的服务器，可分为 32 位或 64 位。 |
| Boolean            | 布尔值。用于存储布尔值（真/假）。                            |
| Double             | 双精度浮点值。用于存储浮点值。                               |
| Min/Max keys       | 将一个值与 BSON（二进制的 JSON）元素的最低值和最高值相对比。 |
| Array              | 用于将数组或列表或多个值存储为一个键。                       |
| Timestamp          | 时间戳。记录文档修改或添加的具体时间。                       |
| Object             | 用于内嵌文档。                                               |
| Null               | 用于创建空值。                                               |
| Symbol             | 符号。该数据类型基本上等同于字符串类型，但不同的是，它一般用于采用特殊符号类型的语言。 |
| Date               | 日期时间。用 UNIX 时间格式来存储当前日期或时间。你可以指定自己的日期时间：创建 Date 对象，传入年月日信息。 |
| Object ID          | 对象 ID。用于创建文档的 ID。                                 |
| Binary Data        | 二进制数据。用于存储二进制数据。                             |
| Code               | 代码类型。用于在文档中存储 JavaScript 代码。                 |
| Regular expression | 正则表达式类型。用于存储正则表达式。                         |

###  6、ObjectId

ObjectId 类似唯一主键，可以很快的去生成和排序，包含 12 bytes，含义是：

- 前 4 个字节表示创建 **unix** 时间戳,格林尼治时间 **UTC** 时间，比北京时间晚了 8 个小时

- 接下来的 3 个字节是机器标识码

- 紧接的两个字节由进程 id 组成 PID

- 最后三个字节是随机数

- MongoDB 中存储的文档必须有一个 _id 键。这个键的值可以是任何类型的，默认是个 ObjectId 对象

  由于 ObjectId 中保存了创建的时间戳，所以你不需要为你的文档保存时间戳字段，你可以通过 

### 7、常见命令：

#### 7.1**"show dbs"** 命令可以显示所有数据的列表。

```
> show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
test    0.000GB
```

#### 7.2执行 **"db"** 命令可以显示当前数据库对象或集合。

```
>./mongo
> db
test
```

#### 7.3运行"**use**"命令，可以连接到一个指定的数据库

```
>./mongo
> use local
switched to db local
(local是你要连接的数据库)
```

#### 7.4getTimestamp 函数来获取文档的创建时间

```
> var newObject = ObjectId()
> newObject.getTimestamp()
ISODate("2022-04-07T09:27:12Z")
```

#### 7.5ObjectId 转为字符串

```
> newObject.str
```

#### 7.6日期

表示当前距离 Unix新纪元（1970年1月1日）的毫秒数。日期类型是有符号的, 负数表示 1970 年之前的日期。

```
> var mydate = new Date()//格林尼治时间
> mydate
ISODate("2022-04-07T09:44:36.754Z")
> typeof mydate
object
```

```
> var mydatestr = mydate.toString()
> mydatestr
Thu Apr 07 2022 17:44:36 GMT+0800 (CST)
> typeof mydatestr
string
```

```
> Date()
Thu Apr 07 2022 17:43:58 GMT+0800 (CST)
```

## 三、MongoDB的基本操作

### 1、MongoDB 创建数据库

* 语法

  MongoDB创建数据库的语法格式如下：

  ```
  use DATABASE_NAME
  ```

* 实例

  创建数据库runoob:

  ```
  >use runoob
  switched to db runoob
  >db
  runoob
  >
  ```

  使用show dbs命令可以查看所有数据库，然而刚创建的数据库，因为没有插入数据，所以即使你使用 show dbs ，新建数据库也不会显示；

  ```
  >db.runoob.insert({"name":"教程"})
  WriteResult({"nInserted":1})
  ```

  MongoDB中默认的数据库是test，如果你没有创建新的数据库，集合将存放在test数据库中；

  **注意：在MongoDB中，集合只有在内容插入之后才会创建！所以创建集合后要再插入一个文档（记录），集合才会真正创建。**

### 2、MongoDB 删除数据库

* 语法

  MongoDB删除数据库的语法格式如下：

  ```
  db.dropDatabase()
  ```

  删除当前数据库，默认为test，可以通过db来查询当前数据库的名称；

* 实例

  首先查看所有数据库

  ```
  >show dbs
  ```

  接下来切换到要删除的数据库（runoob)

  ```
  >use runoob
  ```

  执行删除命令

  ```
  >db.dropDatabase()
  ```

  最后，通过show dbs命令来核查一下数据库删除是否成功：

  ```
  >show dbs
  ```

### 3、MongoDB 创建集合

语法格式：

db.createCollecion(name,options)

* name:要创建的集合名称

* options:可选参数，指定有关内存大小及索引的选项

  options可以是如下参数：

| 字段        | 类型 | 描述                                                         |
| :---------- | :--- | :----------------------------------------------------------- |
| capped      | 布尔 | （可选）如果为 true，则创建固定集合。固定集合是指有着固定大小的集合，当达到最大值时，它会自动覆盖最早的文档。 **当该值为 true 时，必须指定 size 参数。** |
| autoIndexId | 布尔 | 3.2 之后不再支持该参数。（可选）如为 true，自动在 _id 字段创建索引。默认为 false。 |
| size        | 数值 | （可选）为固定集合指定一个最大值，即字节数。 **如果 capped 为 true，也需要指定该字段。** |
| max         | 数值 | （可选）指定固定集合中包含文档的最大数量                     |

（在插入文档时，MongoDB首先检查固定集合的size字段，然后检查max字段）

* 查看集合可以使用show collections 或show tables命令

  ```
  > use test
  switched to db test
  > db.createCollection("site")
  { "ok" : 1 }
  > show collections#show tables
  site
  ```

* 在 MongoDB 中，你不需要创建集合。当你插入一些文档时，MongoDB 会自动创建集合。

  ```
  > use test
  switched to db test
  > db.col.insert({"name":"彭奥"})
  WriteResult({ "nInserted" : 1 })
  > show collections#show tables
  col
  ```

```
> use test
switched to db test
> db.createCollection("mycol",{capped : true,autoIndexId : true, size :6142800, max : 10000})
{
        "note" : "The autoIndexId option is deprecated and will be removed in a future release",
        "ok" : 1
}
> show tables
mycol
```

### 4、MongoDB 删除集合

集合删除语法格式如下：

```
db.collection.drop()
```

以下实例删除了runoob数据库中的集合site：

```
> use runoob #创建集合runoob
switched to db runoob
> db.createCollection("site")#创建集合site
{ "ok" : 1 }
> show tables#查询集合
site
> db.site.drop()#删除集合
true
> show tables#查询集合
>
```

### 5、MongoDB 插入文档

MongoDB 使用 insert() 或 save() 方法向集合中插入文档，语法如下：

```
db.COLLECTION_NAME.insert(document)
或
db.COLLECTION_NAME.save(document)
```

- save()：如果 _id 主键存在则更新数据，如果不存在就插入数据。该方法新版本中已废弃，可以使用 **db.collection.insertOne()** 或 **db.collection.replaceOne()** 来代替。

- insert(): 若插入的数据主键已经存在，则会抛 **org.springframework.dao.DuplicateKeyException** 异常，提示主键重复，不保存当前数据。

- db.collection.insertOne() 用于向集合插入一个新文档，语法格式如下：

  ```
  db.collection.insertOne(
     <document>,
     {
        writeConcern: <document>
     }
  )
  ```

- db.collection.insertMany() 用于向集合插入一个多个文档，语法格式如下：

  ```
  db.collection.insertMany(
     [ <document 1> , <document 2>, ... ],
     {
        writeConcern: <document>,
        ordered: <boolean>
     }
  )
  ```

参数说明：

- document：要写入的文档。
- writeConcern：写入策略，默认为 1，即要求确认写操作，0 是不要求。
- ordered：指定是否按顺序写入，默认 true，按顺序写入。

实例：

在数据库test的集合mycol中插入文档：

* 方法一：

```
> show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
test    0.000GB
> use test
switched to db test
> show tables
mycol
> use mycol
switched to db mycol
> db.mycol.insert({
... title: '教程',
... description: '是一个数据库',
... by: '1',
... url: 'http://wwww.test.com',
... tages: ['mongodb','database','NoSQL'],
... likes: 100
... })
WriteResult({ "nInserted" : 1 })
```

查看已插入文档：

```
> db.mycol.find()
{ "_id" : ObjectId("624f7a3c19c8c92ade4dbe2e"), "title" : "教程", "description" : "是一个数据库", "by" : "1", "url" : "http://wwww.test.com", "tages" : [ "mongodb", "database", "NoSQL" ], "likes" : 100 }
```

* 方法二

  我们也可以将数据定义为一个变量

  ```
  > document=({ title: '教程', description: '是一个数据库', by: '1', url: 'http://wwww.test.com', tages: ['mongodb','database','NoSQL'], likes: 100 })
  ```

  执行后显示结果如下

  ```
  {
          "title" : "教程",
          "description" : "是一个数据库",
          "by" : "1",
          "url" : "http://wwww.test.com",
          "tages" : [
                  "mongodb",
                  "database",
                  "NoSQL"
          ],
          "likes" : 100
  }
  ```

  执行插入操作：

  (插入文档你也可以使用 db.col.save(document) 命令。如果不指定 _id 字段 save() 方法类似于 insert() 方法。如果指定 _id 字段，则会更新该 _id 的数据。)

  ```
  > db.mycol.insert(document)
  WriteResult({ "nInserted" : 1 })
  > db.mycol.find()#查看文档
  { "_id" : ObjectId("624f7a3c19c8c92ade4dbe2e"), "title" : "教程", "description" : "是一个数据库", "by" : "1", "url" : "http://wwww.test.com", "tages" : [ "mongodb", "database", "NoSQL" ], "likes" : 100 }
  { "_id" : ObjectId("624f7b9519c8c92ade4dbe2f"), "title" : "教程", "description" : "是一个数据库", "by" : "1", "url" : "http://wwww.test.com", "tages" : [ "mongodb", "database", "NoSQL" ], "likes" : 100 }
  ```

### 6、MongoDB更新文档

#### 6.1update()方法

update() 方法用于更新已存在的文档。语法格式如下：

```
db.collection.update(
   <query>,
   <update>,
   {
     upsert: <boolean>,
     multi: <boolean>,
     writeConcern: <document>
   }
)
```

**参数说明：**

- **query** : update的查询条件，类似sql update查询内where后面的。
- **update** : update的对象和一些更新的操作符（如$,$inc...）等，也可以理解为sql update查询内set后面的
- **upsert** : 可选，这个参数的意思是，如果不存在update的记录，是否插入objNew,true为插入，默认是false，不插入。
- **multi** : 可选，mongodb 默认是false,只更新找到的第一条记录，如果这个参数为true,就把按条件查出来多条记录全部更新。
- **writeConcern** :可选，抛出异常的级别。

实例：

先在数据库test下的mycol集合里插入文档

```
> db.mycol.insert({
... title: '教程',
... description: '是一个数据库',
... by: '1',
... url: 'http://wwww.test.com',
... tages: ['mongodb','database','NoSQL'],
... likes: 100
... })
WriteResult({ "nInserted" : 1 })
```

接着用update()方法来更新标题（title):

```
> db.mycol.update({'title':'教程'},{$set:{'title':'MongoDB教程'}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
#执行查询语句
> db.mycol.find().pretty()#db.mycol.find()与db.mycol.find().pretty()的区别在于：后者查询的结果更加美观条理清晰。
{
        "_id" : ObjectId("624f7a3c19c8c92ade4dbe2e"),
        "title" : "MongoDB教程",
        "description" : "是一个数据库",
        "by" : "1",
        "url" : "http://wwww.test.com",
        "tages" : [
                "mongodb",
                "database",
                "NoSQL"
        ],
        "likes" : 100
}
```

注意：

可以看到标题(title)由原来的 "教程" 更新为了 "MongoDB教程"。

以上语句只会修改第一条发现的文档，如果你要修改多条相同的文档，则需要设置 multi 参数为 true。

```
>db.col.update({'title':'教程'},{$set:{'title':'MongoDB教程'}},{multi:true})
```

#### 6.2save() 方法

save() 方法通过传入的文档来替换已有文档，_id 主键存在就更新，不存在就插入。语法格式如下：

```
db.collection.save(
   <document>,
   {
     writeConcern: <document>
   }
)
```

**参数说明：**

- **document** : 文档数据。
- **writeConcern** :可选，抛出异常的级别。

实例：

以下实例中我们替换了 _id 为 56064f89ade2f21f36b03136 的文档数据

```
> db.mycol.save({
... "_id" : ObjectId("56064f89ade2f21f36b03136"),
... "title" : "MongoDB教程",
... ...         "description" : "是一个数据库",
... ...         "by" : "1",
... ...         "url" : "http://wwww.test.com",
... ...         "tages" : [
... ...                 "mongodb",
... ...                 "database",
... ...                 "NoSQL"
... ...         ],
... ...         "likes" : 110
... })
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("56064f89ade2f21f36b03136")
})
# 查看替换后的数据
> db.mycol.find().pretty()
{
        "_id" : ObjectId("56064f89ade2f21f36b03136"),
        "title" : "MongoDB教程",
        "description" : "是一个数据库",
        "by" : "1",
        "url" : "http://wwww.test.com",
        "tages" : [
                "mongodb",
                "database",
                "NoSQL"
        ],
        "likes" : 110
}
```

更多实例：

* 只更新第一条记录：

```
db.mycol.update( { "count" : { $gt : 1 } } , { $set : { "test2" : "OK"} } );
```

全部更新：

```
db.mycol.update( { "count" : { $gt : 3 } } , { $set : { "test2" : "OK"} },false,true );
```

只添加第一条：

```
db.mycol.update( { "count" : { $gt : 4 } } , { $set : { "test5" : "OK"} },true,false );
```

全部添加进去：

```
db.mycol.update( { "count" : { $gt : 5 } } , { $set : { "test5" : "OK"} },true,true );
```

全部更新：

```
db.mycol.update( { "count" : { $gt : 15 } } , { $inc : { "count" : 1} },false,true );
```

只更新第一条记录：

```
db.mycol.update( { "count" : { $gt : 10 } } , { $inc : { "count" : 1} },false,false );
```

### 7、MongoDB删除文档

**语法**

remove() 方法的基本语法格式如下所示：

```
db.collection.remove(
   <query>,
   {
     justOne: <boolean>,
     writeConcern: <document>
   }
)
```

**参数说明：**

- **query** :（可选）删除的文档的条件。
- **justOne** : （可选）如果设为 true 或 1，则只删除一个文档，如果不设置该参数，或使用默认值 false，则删除所有匹配条件的文档。
- **writeConcern** :（可选）抛出异常的级别。

实例：

```
> db.mycol.remove({'title':'教程'})
WriteResult({ "nRemoved" : 1 })#删除了一条数据
> db.mycol.find()#函数查询数据
>#无数据
```

* 如果你只想删除第一条找到的记录可以设置 justOne 为 1，如下所示：

  ```
  >db.COLLECTION_NAME.remove(DELETION_CRITERIA,1)
  ```

* 如果你想删除所有数据，可以使用以下方式（类似常规 SQL 的 truncate 命令）：(mycol集合名)

  ```
  >db.mycol.remove({})
  >db.mycol.find()
  >
  ```

### 8、MongoDB查询文档

#### 8.1find() 方法

**以非结构化的方式来显示所有文档。**

语法：

```
db.collection.find(query, projection)
```

- **query** ：可选，使用查询操作符指定查询条件
- **projection** ：可选，使用投影操作符指定返回的键。查询时返回文档中所有键值， 只需省略该参数即可（默认省略）。
- 除了 find() 方法之外，还有一个 findOne() 方法，它只返回一个文档。

#### 8.2pretty()方法

**pretty() 方法以格式化的方式来显示所有文档。**

如果你需要以**易读**的方式来读取数据，可以使用 pretty() 方法，语法格式如下：

````
>db.mycol.find().pretty()
````

#### 8.3MongoDB 与 RDBMS Where 语句比较

如果你熟悉常规的 SQL 数据，通过下表可以更好的理解 MongoDB 的条件语句查询：

| 操作       | 格式                     | 范例                                        | RDBMS中的类似语句       |
| :--------- | :----------------------- | :------------------------------------------ | :---------------------- |
| 等于       | `{<key>:<value>`}        | `db.col.find({"by":"菜鸟教程"}).pretty()`   | `where by = '菜鸟教程'` |
| 小于       | `{<key>:{$lt:<value>}}`  | `db.col.find({"likes":{$lt:50}}).pretty()`  | `where likes < 50`      |
| 小于或等于 | `{<key>:{$lte:<value>}}` | `db.col.find({"likes":{$lte:50}}).pretty()` | `where likes <= 50`     |
| 大于       | `{<key>:{$gt:<value>}}`  | `db.col.find({"likes":{$gt:50}}).pretty()`  | `where likes > 50`      |
| 大于或等于 | `{<key>:{$gte:<value>}}` | `db.col.find({"likes":{$gte:50}}).pretty()` | `where likes >= 50`     |
| 不等于     | `{<key>:{$ne:<value>}}`  | `db.col.find({"likes":{$ne:50}}).pretty()`  | `where likes != 50`     |

#### 8.4MongoDB AND 条件

MongoDB 的 find() 方法可以传入多个键(key)，每个键(key)以逗号隔开，即常规 SQL 的 AND 条件。

语法格式如下：

```
>db.mycol.find({key1:value1, key2:value2}).pretty()
```

#### 8.5MongoDB OR 条件

MongoDB OR 条件语句使用了关键字 **$or**,语法格式如下：

```
>db.mycol.find(
   {
      $or: [
         {key1: value1}, {key2:value2}
      ]
   }
).pretty()
```

#### 8.6AND 和 OR 联合使用

以下实例演示了 AND 和 OR 联合使用，类似常规 SQL 语句为： **'where likes>50 AND (by = '菜鸟教程' OR title = 'MongoDB 教程')'**

```
>db.mycol.find({"likes": {$gt:50}, $or: [{"by": "菜鸟教程"},{"title": "MongoDB 教程"}]}).pretty()
```

### 9、MongoDB条件操作符

MongoDB中条件操作符有：

- (>) 大于 - $gt
- (<) 小于 - $lt
- (>=) 大于等于 - $gte
- (<= ) 小于等于 - $lte

实例：

* 如果你想获取"mycol"集合中 "likes" 大于100，小于 200 的数据，你可以使用以下命令：

```
db.mycol.find({likes : {$lt :200, $gt : 100}})
```

*  如果你想获取"col"集合中 "likes" 小于等于 150 的数据，你可以使用以下命令

  ```
  db.mycol.find({likes : {$lte : 150}})
  ```

### 10、MongoDB$type操作符

$type操作符是基于BSON类型来检索集合中匹配的数据类型，并返回结果。

MongoDB 中可以使用的类型如下表所示：

|                         |          |                  |
| :---------------------- | :------- | :--------------- |
| **类型**                | **数字** | **备注**         |
| Double                  | 1        |                  |
| String                  | 2        |                  |
| Object                  | 3        |                  |
| Array                   | 4        |                  |
| Binary data             | 5        |                  |
| Undefined               | 6        | 已废弃。         |
| Object id               | 7        |                  |
| Boolean                 | 8        |                  |
| Date                    | 9        |                  |
| Null                    | 10       |                  |
| Regular Expression      | 11       |                  |
| JavaScript              | 13       |                  |
| Symbol                  | 14       |                  |
| JavaScript (with scope) | 15       |                  |
| 32-bit integer          | 16       |                  |
| Timestamp               | 17       |                  |
| 64-bit integer          | 18       |                  |
| Min key                 | 255      | Query with `-1`. |
| Max key                 | 127      |                  |

实例：

如果想获取 "mycol" 集合中 title 为 String 的数据，你可以使用以下命令：

```
db.mycol.find({"title" : {$type : 2}})
或
db.mycol.find({"title" : {$type : 'string'}})
```

### 11、MongoDB Limit与Skip方法

#### 11.1MongoDB Limit() 方法

如果你需要在MongoDB中读取指定数量的数据记录，可以使用MongoDB的Limit方法，limit()方法接受一个数字参数，该参数指定从MongoDB中读取的记录条数。

语法:

```
>db.COLLECTION_NAME.find().limit(NUMBER)
```

注：如果你们没有指定limit()方法中的参数则显示集合中的所有数据。

```
> db.mycol.find({},{"title":1,_id:0}).limit(2)
{ "title" : "PHP 教程" }
{ "title" : "Java 教程" }
>
```

#### 11.2MongoDB Skip() 方法

我们除了可以使用limit()方法来读取指定数量的数据外，还可以使用skip()方法来跳过指定数量的数据，skip方法同样接受一个数字参数作为跳过的记录条数。

语法：

```
>db.COLLECTION_NAME.find().limit(NUMBER).skip(NUMBER)
```

实例：

以下实例只会显示第二条文档数据

```
>db.mycol.find({},{"title":1,_id:0}).limit(1).skip(1)
{ "title" : "Java 教程" }
>
```

**注:**skip()方法默认参数为 0 

### 12、MongoDB 排序

**MongoDB sort() 方法**:

在 MongoDB 中使用 sort() 方法对数据进行排序，sort() 方法可以通过参数指定排序的字段，并使用 1 和 -1 来指定排序的方式，其中 1 为升序排列，而 -1 是用于降序排列。

* 语法

  ```
  >db.COLLECTION_NAME.find().sort({KEY:1})
  ```

  * 实例

    ```
    >db.mycol.find({},{"title":1,_id:0}).sort({"likes":-1})
    { "title" : "PHP 教程" }
    { "title" : "Java 教程" }
    { "title" : "MongoDB 教程" }
    ```

### 13、MongoDB索引

MongoDB使用 createIndex() 方法来创建索引。

* 语法

  ```
  >db.collection.createIndex(keys, options)
  ```

  语法中 Key 值为你要创建的索引字段，1 为指定按升序创建索引，如果你想按降序来创建索引指定为 -1 即可.

* 实例

  ```
  >db.mycol.createIndex({"title":1})
  >
  ```

* createIndex() 方法中你也可以设置使用多个字段创建索引（关系型数据库中称作复合索引）。

  ```
  >db.mycol.createIndex({"title":1,"description":-1})
  >
  ```

  createIndex() 接收可选参数，可选参数列表如下：

| Parameter          | Type          | Description                                                  |
| :----------------- | :------------ | :----------------------------------------------------------- |
| background         | Boolean       | 建索引过程会阻塞其它数据库操作，background可指定以后台方式创建索引，即增加 "background" 可选参数。 "background" 默认值为**false**。 |
| unique             | Boolean       | 建立的索引是否唯一。指定为true创建唯一索引。默认值为**false**. |
| name               | string        | 索引的名称。如果未指定，MongoDB的通过连接索引的字段名和排序顺序生成一个索引名称。 |
| dropDups           | Boolean       | **3.0+版本已废弃。**在建立唯一索引时是否删除重复记录,指定 true 创建唯一索引。默认值为 **false**. |
| sparse             | Boolean       | 对文档中不存在的字段数据不启用索引；这个参数需要特别注意，如果设置为true的话，在索引字段中不会查询出不包含对应字段的文档.。默认值为 **false**. |
| expireAfterSeconds | integer       | 指定一个以秒为单位的数值，完成 TTL设定，设定集合的生存时间。 |
| v                  | index version | 索引的版本号。默认的索引版本取决于mongod创建索引时运行的版本。 |
| weights            | document      | 索引权重值，数值在 1 到 99,999 之间，表示该索引相对于其他索引字段的得分权重。 |
| default_language   | string        | 对于文本索引，该参数决定了停用词及词干和词器的规则的列表。 默认为英语 |
| language_override  | string        | 对于文本索引，该参数指定了包含在文档中的字段名，语言覆盖默认的language，默认值为 language. |

在后台创建索引：

```
db.values.createIndex({open: 1, close: 1}, {background: true})
```

通过在创建索引时加 background:true 的选项，让创建工作在后台执行

### 14、MongoDB聚合

MongoDB 中聚合(aggregate)主要用于处理数据(诸如统计平均值，求和等)，并返回计算后的数据结果。

有点类似 **SQL** 语句中的 **count(\*)**。

#### 14.1aggregate() 方法:

语法

```
>db.COLLECTION_NAME.aggregate(AGGREGATE_OPERATION)
```

| 表达式    | 描述                                                         | 实例                                                         |
| :-------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| $sum      | 计算总和。                                                   | db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$sum : "$likes"}}}]) |
| $avg      | 计算平均值                                                   | db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$avg : "$likes"}}}]) |
| $min      | 获取集合中所有文档对应值得最小值。                           | db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$min : "$likes"}}}]) |
| $max      | 获取集合中所有文档对应值得最大值。                           | db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$max : "$likes"}}}]) |
| $push     | 将值加入一个数组中，不会判断是否有重复的值。                 | db.mycol.aggregate([{$group : {_id : "$by_user", url : {$push: "$url"}}}]) |
| $addToSet | 将值加入一个数组中，会判断是否有重复的值，若相同的值在数组中已经存在了，则不加入。 | db.mycol.aggregate([{$group : {_id : "$by_user", url : {$addToSet : "$url"}}}]) |
| $first    | 根据资源文档的排序获取第一个文档数据。                       | db.mycol.aggregate([{$group : {_id : "$by_user", first_url : {$first : "$url"}}}]) |
| $last     | 根据资源文档的排序获取最后一个文档数据                       | db.mycol.aggregate([{$group : {_id : "$by_user", last_url : {$last : "$url"}}}]) |

* 实例

  ```
  {
     _id: ObjectId(7df78ad8902c)
     title: 'MongoDB Overview', 
     description: 'MongoDB is no sql database',
     by_user: 'runoob.com',
     url: 'http://www.runoob.com',
     tags: ['mongodb', 'database', 'NoSQL'],
     likes: 100
  },
  {
     _id: ObjectId(7df78ad8902d)
     title: 'NoSQL Overview', 
     description: 'No sql database is very fast',
     by_user: 'runoob.com',
     url: 'http://www.runoob.com',
     tags: ['mongodb', 'database', 'NoSQL'],
     likes: 10
  },
  {
     _id: ObjectId(7df78ad8902e)
     title: 'Neo4j Overview', 
     description: 'Neo4j is no sql database',
     by_user: 'Neo4j',
     url: 'http://www.neo4j.com',
     tags: ['neo4j', 'database', 'NoSQL'],
     likes: 750
  },
  ```

  现在我们通过以上集合计算每个作者所写的文章数，使用aggregate()计算结果如下：

  ```
  > db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$sum : 1}}}])
  {
     "result" : [
        {
           "_id" : "runoob.com",
           "num_tutorial" : 2
        },
        {
           "_id" : "Neo4j",
           "num_tutorial" : 1
        }
     ],
     "ok" : 1
  }
  >
  ```

  
