#### 新建ItemModel
- 先创建领域模型，然后设计数据库。考虑性能问题，将item_stock分开存储。
- 修改pom文件，将overwrite修改为false，防止破坏以前的结果。在mybatis-generator.xml新增两个表，注释之前已经生成过的user表信息，运行生成新的do和domapper文件。要在domapper.xml中对insert和insertSelective语句新增属性useGeneratedKeys="true" keyProperty="id"，表示自增。

#### 新建ItemService/Impl
- 新建接口ItemService，定义几个接口，之后实现接口。
- 入参校验，需要引入ValidatorImpl validator。

#### 新建ItemController
- 与之前的UserController类似。难点主要在数据库ItemDOMapper中price类型上：BigDecimal与Double之间的转换要注意。
