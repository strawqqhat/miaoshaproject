#### UserController

#### UserDOMapper
#### UserPasswordMapper

#### UserDO
#### UserPasswordDO

#### UserService/impl/UserModel

1. quickstart新建springboot项目
2. 在pom中填写相关依赖并下载工具包
```
继承父pom
<parent>
<artifactId>spring-boot-starter-parent</artifactId>
<groupId>org.springframework.boot</groupId>
<version>2.3.1.RELEASE</version>
</parent>

<dependency>
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-starter-web</artifactId>
<version>2.3.1.RELEASE</version>
</dependency>

<dependency>
<groupId>mysql</groupId>
<artifactId>mysql-connector-java</artifactId>
<version>5.1.46</version>
</dependency>

<dependency>
<groupId>com.alibaba</groupId>
<artifactId>druid</artifactId>
<version>1.1.3</version>
</dependency>

<dependency>
<groupId>org.mybatis.spring.boot</groupId>
<artifactId>mybatis-spring-boot-starter</artifactId>
<version>1.3.2</version>
</dependency>

<plugin>
  <groupId>org.mybatis.generator</groupId>
  <artifactId>mybatis-generator-maven-plugin</artifactId>
  <version>1.4.0</version>
  <dependencies>
	<dependency>
	  <groupId>org.mybatis.generator</groupId>
	  <artifactId>mybatis-generator-core</artifactId>
	  <version>1.4.0</version>
	</dependency>
	<dependency>
	  <groupId>mysql</groupId>
	  <artifactId>mysql-connector-java</artifactId>
	  <version>5.1.46</version>
	</dependency>
  </dependencies>
  <executions>
	<execution>
	  <id>mybatis generator</id>
	  <phase>package</phase>
	  <goals>
		<goal>generate</goal>
	  </goals>
	</execution>
  </executions>
  <configuration>
	<verbose>true</verbose>
	<overwrite>true</overwrite>
	<configurationFile>
	  src/main/resources/mybatis-generator.xml
	</configurationFile>
  </configuration>
</plugin>
```
		
3. 编写mybatis-generator.xml文件并配置运行，删去dao包下的example文件
可以在网上找到此文件
```
数据库连接地址账号密码
<jdbcConnection driverClass="com.mysql.jdbc.Driver"
					connectionURL="jdbc:mysql://localhost:3306/miaosha"
					userId="root"
					password="root">
</jdbcConnection>

生成Model/DataObject类存放的位置
<javaModelGenerator targetPackage="com.miaoshaproject.dataobject" targetProject="src/main/java">
            <property name="enableSubPackages" value="true" />
            <property name="trimStrings" value="true" />
</javaModelGenerator>

生成映射文件存放位置
<sqlMapGenerator targetPackage="mapping"  targetProject="src/main/resources">
            <property name="enableSubPackages" value="true" />
</sqlMapGenerator>

生成dao类存放位置
<javaClientGenerator type="XMLMAPPER" targetPackage="com.miaoshaproject.dao"  targetProject="src/main/java">
            <property name="enableSubPackages" value="true" />
</javaClientGenerator>

其后生成表及类名

```

4. 创建controller和service包
```
先新建和编写controller文件
新建和编写service文件
新建和编写model文件
```



