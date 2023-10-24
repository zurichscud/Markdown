# mybatis-config.xml

所有的配置项都处于`<configuration>`内


```xml
<?xml version="1.0" encoding="UTF-8" ?>  
<!DOCTYPE configuration  
PUBLIC "-//mybatis.org//DTD Config 3.0//EN"  
"http://mybatis.org/dtd/mybatis-3-config.dtd">  
<configuration>  
  <!--设置连接数据库的环境-->  
  <environments default="development">  
    <environment id="development">  
      <transactionManager type="JDBC"/>  
      <dataSource type="POOLED">  
        <property name="driver" value="com.mysql.cj.jdbc.Driver"/>  
        <property name="url" value="jdbc:mysql://localhost:3306/MyBatis"/>  
        <property name="username" value="root"/>  
        <property name="password" value="123456"/>  
      </dataSource>  
    </environment>  
  </environments>  
  <!--引入映射文件-->  
  <mappers>  
    <mapper resource="mappers/UserMapper.xml"/>  
  </mappers>  
</configuration>
```

- `environments` 数据库环境。可以声明多个`environment`，使用`default`可以指定使用哪一个`environment`
- `transactionManager`事务管理器，`type="JDBC"`指定了JDBC事务管理器
- `dataSource`数据源类型，type="POOLED"指定使用了连接池
  - `driver`数据库驱动
  - `url`数据库位置
  - `username`用户名
  - `password`密码
- `mappers` Mybatis映射器，可以声明多个`Mybatis映射器`（`mapper`）。`resource`指明映射器的路径，相对路径以`resources`目录为参考

# Configuration



## MyBatis映射器

每一个interface都有一个相应的映射文件，例如针对User表的接口`UserMapper`，它的映射器为`UserMapper.xml`。一个`mapper`对应一个xml文件。

example:

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.test.mapper.UserMapper">
    <insert id="insertUser">
        insert into user values(null,'张三','123','三明市','12344555555')
    </insert>
</mapper>
```

`id`： interface中的方法名

`insert`：SQL语言的类型。insert/update/select/delete

## properties

xml文件中可以从`properties`配置文件中获取参数进行解耦。resource指明了资源的路径

```xml
<properties resource="jdbc.properties"/>
```

```xml
            <dataSource type="POOLED">
                <property name="driver" value="${jdbc.driver}"/>
                <property name="url" value="${jdbc.url}"/>
                <property name="username" value="${jdbc.username}"/>
                <property name="password" value="${jdbc.password}"/>
            </dataSource>
```

## typeAliases

对Mybatis中的type起别名

### typeAlias



### package 

# 配置顺序

核心配置文件中的标签必须按照固定的顺序(标签可以不写，但顺序一定不能乱)：

1. `properties`
2. settings
3. `typeAliases`
4. typeHandlers
5. objectFactory
6. objectWrapperFactory
7. reflectorFactory
8. plugins
9. `environments`
10. databaseIdProvider
11. `mappers`
