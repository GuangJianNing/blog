### 自己造成的bug1

mybatis的mapper.xml文件写错了，但是在部署到tomcat的时候不报错，就是不能部署成功，部署情况如图所示，没有deploy successfully日志输出
![1](https://user-images.githubusercontent.com/34411304/71875263-dc3ea000-315e-11ea-998b-af00e3f6728a.png)
正常情况如下图所示
![2](https://user-images.githubusercontent.com/34411304/71875765-12305400-3160-11ea-82f3-6ad0d3ca7a13.png)

#### 造成原因
```xml
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
```
#### 解决方法
type="com.ngj.tmall.pojo.Product"就好了 

#### 总结
以后写mybatis文件一定要检查类的路径名是不是写正确了，写错了也不会报错，很恐怖


### 自己造成的bug2
这是sql ，c表的查询的字段的c.*(id,name)
```sql
select p.*,c.*
        from category c
        inner JOIN product p
        ON p.cid=c.id
        HAVING p.id=#{id}
```
这是上述sql在navicat查询结果
![navicat查询结果](https://user-images.githubusercontent.com/34411304/72140670-31331e00-33cc-11ea-8b72-8964eea3c051.png)
这是结果映射，注意 column的值的id1 和name1，没指定别名，根据navicat查询的结果写的字段名
```xml
<resultMap id="MyProductCategory" type="om.ngj.tmall.pojo.Product">
    <association property="category" javaType="com.ngj.tmall.pojo.Category">
        <id column="id1" jdbcType="INTEGER" property="id"/>
        <result column="name1" jdbcType="VARCHAR" property="name"/>
    </association>
</resultMap>

```
最后的结果就是Category没被复制  category=null，百思不得其解，最后才幡然醒悟，需要自己自定别名

如下
```sql
select p.*,c..id as 'ccid' ,c.name as 'cname'
        from category c
        inner JOIN product p
        ON p.cid=c.id
        HAVING p.id=#{id}
```
```xml
<resultMap id="MyProductCategory" type="om.ngj.tmall.pojo.Product">
    <association property="category" javaType="com.ngj.tmall.pojo.Category">
        <id column="ccid" jdbcType="INTEGER" property="id"/>
        <result column="cname" jdbcType="VARCHAR" property="name"/>
    </association>
</resultMap>

```
映射成功
![image](https://user-images.githubusercontent.com/34411304/72141128-347ad980-33cd-11ea-9e83-85264d449b6a.png)
#### 总结
以后多表查询有字段名重名要显示的自己指定别名，不要偷懒
