# Quickstart

```java
public void test1() throws IOException {
    InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
    //获取sqlsessionFactory
    SqlSessionFactoryBuilder sqlSessionFactoryBuilder = new SqlSessionFactoryBuilder();
    SqlSessionFactory sqlSessionFactory = sqlSessionFactoryBuilder.build(is);
    SqlSession sqlSession = sqlSessionFactory.openSession(true);
    //获取Mapper对象
    UserMapper mapper = sqlSession.getMapper(UserMapper.class);
    //测试
    int i = mapper.insertUser();
    //提交
    sqlSession.commit();
    System.out.println(i);
}
```

