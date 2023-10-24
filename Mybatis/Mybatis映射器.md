# namespace

用于指定映射器（Mapper）接口的命名空间，通常是映射器接口的全类名。

> example:
>
> ```xml
> <mapper namespace="com.test.mapper.UserMapper">
> ```

# mapper元素

## select

| select属性    | 描述                                                       |
| ------------- | ---------------------------------------------------------- |
| id            | id值为dao接口中的方法名                                    |
| resultType    | 返回结果集的全类名                                         |
| resultMap     |                                                            |
| parameterType | 传入SQL参数的类名或别名。**可选参数**，Mybatis能够自动推断 |

> example:
>
> ```xml
> <select id ="findById" parameterType="String" resultType="com.example.model.User">
>     select * from user
>     where id=#{id}
> </select>
> ```
>
> 该语句被称为为`findById`，接受一个String类型的参数，并返回一个User类型的对象。参数#{id}告诉Mybatis创建一个预处理语句参数。通过JDBC，转为一个PreparedStatement对象。

## insert



## update



## delete



## sql 元素

# SQL占位符

在Mybatis映射器中，sql语句有两种参数的使用`#{parameter}`和`${parameter}`

- `#{parameter}`将传入的数据都生成一个字符串，会自动添加引号

  ```sql
  order by #{id}
  //id=11
  order by "11"
  ```

  

- `${parameter}`将传入的数据直接生成在sql中

  ```sql
  order by ${id}
  //id=11
  order by 11
  ```

  > #方式能够避免sql注入，$无法防止sql注入