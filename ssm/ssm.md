# 搭建ssm框架所需要的最少jar包


## Spring+SpringMVC
整体jar包图
![ssm](https://user-images.githubusercontent.com/34411304/74657781-e925c900-51cb-11ea-9dd3-8918b3fa017f.png)

但是在maven 的pom文件中只需要输入以下两个依赖即可，因为maven会把相关依赖的的jar包给我们下载下来，不必全部不输入
```xml
 <dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>5.2.1.RELEASE</version>
</dependency>
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-webmvc</artifactId>
    <version>5.1.13.RELEASE</version>
</dependency>
```
这是加入spring-context以后Maven加载的依赖
![ss](https://user-images.githubusercontent.com/34411304/74657788-eb882300-51cb-11ea-8745-01177e2c42c5.png)

这是加入spring-webmvc以后Maven加载的依赖
![ss2](https://user-images.githubusercontent.com/34411304/74657807-f5aa2180-51cb-11ea-8a6c-6b4fba95a9aa.png)

## Spring+Mybatis
整体jar包图

![mybatisDependcy](https://user-images.githubusercontent.com/34411304/74657801-f478f480-51cb-11ea-8cec-3f1d22586d04.png)
![sm](https://user-images.githubusercontent.com/34411304/74658187-b4fed800-51cc-11ea-8ead-7dd6a76cf661.png)
```xml
<!-- 数据库连接池 -->
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid</artifactId>
    <version>${druid_version}</version>
</dependency>
<!-- mybatis -->
<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis</artifactId>
    <version>${mybatis.version}</version>
</dependency>

<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis-spring</artifactId>
    <version>${mybatis.spring.version}</version>
</dependency>
<!-- jdbc -->
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>${mysqlConnJava.version}</version>
</dependency>

<!-- 还需要两个Spring的jar包 -->
 <dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-tx</artifactId>
    <version>${spring.tx.version}</version>
</dependency>
<!--        使用 druid 整合 mybatis必须要这个包-->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-jdbc</artifactId>
    <version>${spring.jdbc.version}</version>
</dependency>
```

搭建一个能够运行的SSM框架至少需要以上jar
其他如日志，分页插件，mybatisGenerator等按需引入

这里贴上常用的jar包
```xml
 <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.source>1.7</maven.compiler.source>
        <maven.compiler.target>1.7</maven.compiler.target>
        <Gson_version>2.8.6</Gson_version>
        <!--        数据库连接池-->
        <druid_version>1.1.10</druid_version>
        <!--   mybatis 相关   -->
        <mybatis.spring.version>2.0.0</mybatis.spring.version>
        <mybatis.version>3.5.3</mybatis.version>
        <mysqlConnJava.version>5.1.6</mysqlConnJava.version>

        <generator.version>1.4.0</generator.version>
        <!--        spring整合mybatis相关-->
        <!--        json-->
        <fastJson.version>1.2.62</fastJson.version>
        <spring.tx.version>5.1.0.RELEASE</spring.tx.version>
        <spring.jdbc.version>5.1.0.RELEASE</spring.jdbc.version>
        <lombok.version>1.18.10</lombok.version>
        <!--        日志相关-->
        <log4j.version>1.2.17</log4j.version>
        <self4j.version>1.8.0-beta0</self4j.version>
        <!--        mybatis分页插件-->
        <pageHelper.version>5.1.2-beta</pageHelper.version>
    </properties>

    <dependencies>


        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13</version>
        </dependency>
        <dependency>
            <groupId>com.google.code.gson</groupId>
            <artifactId>gson</artifactId>
            <version>${Gson_version}</version>
            <scope>compile</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>5.2.1.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>5.1.13.RELEASE</version>
            <!--mybatis数据库相关-->
        </dependency>
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid</artifactId>
            <version>${druid_version}</version>
        </dependency>

        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
            <version>${mybatis.version}</version>
        </dependency>

        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis-spring</artifactId>
            <version>${mybatis.spring.version}</version>
        </dependency>
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>${mysqlConnJava.version}</version>
        </dependency>


        <!--        mybatis generator-->
        <dependency>
            <groupId>org.mybatis.generator</groupId>
            <artifactId>mybatis-generator-core</artifactId>
            <version>${generator.version}</version>
        </dependency>

        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>fastjson</artifactId>
            <version>${fastJson.version}</version>
        </dependency>
        <!--        报错缺少这个包-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-tx</artifactId>
            <version>${spring.tx.version}</version>
        </dependency>
        <!--        使用 druid 整合 mybatis必须要这个包-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
            <version>${spring.jdbc.version}</version>
        </dependency>

        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>${lombok.version}</version>
        </dependency>


        <!-- 日志相关       -->
        <!--        不要这个也可以打印出日志-->
        <!--        <dependency>-->
        <!--            <groupId>log4j</groupId>-->
        <!--            <artifactId>log4j</artifactId>-->
        <!--            <version>${log4j.version}</version>-->
        <!--        </dependency>-->
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-log4j12</artifactId>
            <version>${self4j.version}</version>
        </dependency>


        <!--        分页插件-->
        <dependency>
            <groupId>com.github.pagehelper</groupId>
            <artifactId>pagehelper</artifactId>
            <version>${pageHelper.version}</version>
        </dependency>
    </dependencies>
```


## application.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:mybatis="http://mybatis.org/schema/mybatis-spring"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd
        http://mybatis.org/schema/mybatis-spring http://mybatis.org/schema/mybatis-spring.xsd
">
    <!--    注解-->
    <context:annotation-config/>
    <context:component-scan base-package="com.ngj.service"></context:component-scan>
    <!--    数据库连接池-->
    <context:property-placeholder location="classpath:jdbc.properties"/>
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource" init-method="init" destroy-method="close">
        <property name="url" value="${url}"/>
        <property name="username" value="${jdbc.userName}"/>
        <property name="password" value="${jdbc.password}"/>
        
        <!-- 以下数据库连接配置，是在alibaba druid github 上面推荐的 -->
        <!-- 配置初始化大小、最小、最大 -->
        <property name="initialSize" value="1"/>
        <property name="minIdle" value="1"/>
        <property name="maxActive" value="20"/>

        <!-- 配置获取连接等待超时的时间 -->
        <property name="maxWait" value="60000"/>

        <!-- 配置间隔多久才进行一次检测，检测需要关闭的空闲连接，单位是毫秒 -->
        <property name="timeBetweenEvictionRunsMillis" value="60000"/>

        <!-- 配置一个连接在池中最小生存的时间，单位是毫秒 -->
        <property name="minEvictableIdleTimeMillis" value="300000"/>

        <property name="validationQuery" value="SELECT 1"/>
        <property name="testWhileIdle" value="true"/>
        <property name="testOnBorrow" value="false"/>
        <property name="testOnReturn" value="false"/>

        <!-- 打开PSCache，并且指定每个连接上PSCache的大小 -->
        <property name="poolPreparedStatements" value="true"/>
        <property name="maxPoolPreparedStatementPerConnectionSize"
                  value="20"/>
    </bean>
    <bean id="sqlSession" class="org.mybatis.spring.SqlSessionFactoryBean">
        <property name="typeAliasesPackage" value="com.ngj.pojo"/>
        <property name="dataSource" ref="dataSource"/>
        <property name="mapperLocations" value="classpath:mapper/*.xml"/>
        <!-- 配置pageHelper 插件的配置方式也是在 PageHepler 的官方github 仓库里面推荐的  还有很多用法-->
        <property name="plugins" >
            <array >
                <bean class="com.github.pagehelper.PageInterceptor">
                    <property name="properties">
                        <value>
                        </value>
                    </property>
                </bean>
            </array>
        </property>
    </bean>

<!--    以下两种写法等价-->
    <bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
        <property name="basePackage" value="com.ngj.mapper"/>

    </bean>


</beans>
```


## SpringMVC.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd http://www.alibaba.com/schema/stat http://www.alibaba.com/schema/stat.xsd http://www.springframework.org/schema/mvc https://www.springframework.org/schema/mvc/spring-mvc.xsd">
    <context:annotation-config/>
    <context:component-scan base-package="com.ngj.controller"/>
 
    <mvc:annotation-driven>
    <!-- 
        使用时@ResponseBody @RequestBpdy 需要配置 json《=》 类的转换器
        这里使用alibaba的 fastJson,需要导入相应jar依赖
    -->
        <mvc:message-converters>
            <bean class="com.alibaba.fastjson.support.spring.FastJsonHttpMessageConverter"/>
        </mvc:message-converters>
    </mvc:annotation-driven>
    <!-- 
        如果是restFul的工程 就不用配置视图解析器了，需要配置的是跨域处理 
        跨域处理一般来说有4种方式：后边专门写一篇
        一下只是其中最简单的一种方式
    -->
<!--    跨域处理-->
    <mvc:cors>
        <mvc:mapping path="/*"
                     allowed-methods="GET,POST,DELETE,PUT"
                     allowed-headers="*"
                     allowed-origins="http://localhost:8080"
                     allow-credentials="true"

        />
    </mvc:cors>

</beans>
```





