# 常用注解

## CRUD

- @Select
- @Insert
- @Update
- @Delete

## @Param

在dao接口中为方法中的参数设置名字，映射器中将使用该名字代替默认的映射关系

`@Param`声明在形参中，value为该形参的别名。

- dao接口：

  ```java
  List<User> findById (@Param("id") String user_id)
  ```

- mapper

  ```java
  @Select("select * from user where id=#{id}")
  List<User> findById (@Param("id") String user_id)
  ```

  

