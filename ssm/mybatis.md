### 重大bug

mybatis的mapper.xml文件写错了，但是在部署到tomcat的时候不报错，就是不能部署成功，部署情况如图所示，没有deploy successfully日志输出
![1](https://user-images.githubusercontent.com/34411304/71875263-dc3ea000-315e-11ea-998b-af00e3f6728a.png)
正常情况如下图所示
![2](https://user-images.githubusercontent.com/34411304/71875765-12305400-3160-11ea-82f3-6ad0d3ca7a13.png)

### 造成原因

    <resultMap id="MyProductCategory" type="om.ngj.tmall.pojo.Product">//此处的type的应该是com.开头，少写了字母“c”
        <id column="id" jdbcType="INTEGER" property="id"/>
        <result column="name" jdbcType="VARCHAR" property="name"/>
        <result column="subTitle" jdbcType="VARCHAR" property="subTitle"/>
        <result column="originalPrice" jdbcType="REAL" property="originalPrice"/>
        <result column="promotePrice" jdbcType="REAL" property="promotePrice"/>
        <result column="stock" jdbcType="INTEGER" property="stock"/>
        <result column="cid" jdbcType="INTEGER" property="cid"/>
        <result column="createDate" jdbcType="TIMESTAMP" property="createDate"/>
        <association property="category" javaType="com.ngj.tmall.pojo.Category">
            <id column="id1" jdbcType="INTEGER" property="id"/>
            <result column="name1" jdbcType="VARCHAR" property="name"/>
        </association>
    </resultMap>

### 解决方法
type="com.ngj.tmall.pojo.Product"就好了 

### 总结
以后写马培培而文件一定要检查类的路径名是不是写正确了，idea 不会帮忙自动检查

'''java
nihao
'''

