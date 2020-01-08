## 最近在学习ssm框架第想使用java8的LocaDateTime时候遇到一些问题

### 最初现象
#### pojo的属性日期的类型从Date类型改成LocalDateTime类型
#### 在update时，报错，使用的是mybatis框架
    
```log
    Caused by: java.lang.IllegalStateException: No typehandler found for property createTime
        at org.apache.ibatis.mapping.ResultMapping$Builder.validate(ResultMapping.java:151)
        at org.apache.ibatis.mapping.ResultMapping$Builder.build(ResultMapping.java:140)
        at org.apache.ibatis.builder.MapperBuilderAssistant.buildResultMapping(MapperBuilderAssistant.java:382)
        at org.apache.ibatis.builder.xml.XMLMapperBuilder.buildResultMappingFromContext(XMLMapperBuilder.java:378)
        at org.apache.ibatis.builder.xml.XMLMapperBuilder.resultMapElement(XMLMapperBuilder.java:280)
        at org.apache.ibatis.builder.xml.XMLMapperBuilder.resultMapElement(XMLMapperBuilder.java:252)
        at org.apache.ibatis.builder.xml.XMLMapperBuilder.resultMapElements(XMLMapperBuilder.java:244)
        at org.apache.ibatis.builder.xml.XMLMapperBuilder.configurationElement(XMLMapperBuilder.java:116
```

#### 解决办法
经过一番谷歌发现需要加入slf4j-log4j12才能支持java8的LocalDate系列，并且要将mybatis更新到3.4版本以上
于是在Maven中加入以下依赖
```xml
    <dependency>
        <groupId>org.mybatis</groupId>
        <artifactId>mybatis-typehandlers-jsr310</artifactId>
        <version>1.0.2</version>
    </dependency>
```
#### 此时又出现一个bug
```log
    java.lang.AbstractMethodError: org.mybatis.spring.transaction.SpringManagedTransaction.getTimeout()Ljava/lang/Integer;
        at org.apache.ibatis.executor.SimpleExecutor.prepareStatement(SimpleExecutor.java:85)
        at org.apache.ibatis.executor.SimpleExecutor.doQuery(SimpleExecutor.java:62)
        at org.apache.ibatis.executor.BaseExecutor.queryFromDatabase(BaseExecutor.java:325)
        at org.apache.ibatis.executor.BaseExecutor.query(BaseExecutor.java:156)
        at org.apache.ibatis.executor.CachingExecutor.query(CachingExecutor.java:109)
        at org.apache.ibatis.executor.CachingExecutor.query(CachingExecutor.java:83)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:498)
```

#### 解决办法
原来3.4版本的mybatis需要和spring5.0+版本配套。这个在这个网站可以查到[mybatis官网](http://mybatis.org/spring/zh/)
于是修改maven中的spring-version为5.0以上的版本，具体版本在maven-repository里面查找，


#### 此时又出现bug
 再系统正常运行时，log4j的日志消失了，没有日志输出

#### 解决方法
在maven中饭添加slf4j-log4j12依赖，日志正常输出
```xml
    <dependency>
        <groupId>org.slf4j</groupId>
        <artifactId>slf4j-log4j12</artifactId>
        <version>1.8.0-beta0</version>
    </dependency>
```


