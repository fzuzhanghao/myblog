## 懒得按以前格式写了，纯粘代码

几点注意：
1、冲突问题，官网的配置未解决curator问题；（P.S. 最新版5.0.0α也没有处理好spring cloud 2.x+的问题，会造成no value bound，详见issue#8299

> https://github.com/apache/shardingsphere/issues/8299

2、配置问题，官网的配置文档还停留在4.0.0的配置，看源码，配置的读取代码为

```
@Generated
    public void setOrchestration(Map<String, YamlCenterRepositoryConfiguration> orchestration) {
        this.orchestration = orchestration;
    }
```
可以看到接受的配置为Map<String, YamlCenterRepositoryConfiguration> orchestration，
所以配置应该是spring.shardingsphere.orchestration.名称.属性，而不是旧的spring.shardingsphere.orchestration.registry.xxx,这点具体可以看github的example
另：nacos居然只能做config center，配置为registry_center会报错，没有该枚举类型。有点尴尬，这样我还要额外再引入zk，那我何不一次性zk搞定呢。
```
spring.shardingsphere.orchestration.<String>.orchestration-type=registry_center,config_center
spring.shardingsphere.orchestration.<String>.instance-type=zookeeper
spring.shardingsphere.orchestration.<String>.server-lists=localhost:2181
spring.shardingsphere.orchestration.<String>.namespace=sharding-test
spring.shardingsphere.orchestration.<String>.props.overwrite=false
```
3、shardingsphere-ui运行的问题，官网提供的ui下载包有点问题，解压出来缺少jar，主要是缺胳膊少腿，如图，需要自己把jar包补充进去
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7982ee86672455b705fcc17ab018acd8.png)


## 具体代码如下（非生产代码，抽空额外做了个测试DEMO）
application.properties

```

mybatis.type-aliases-package=team.zhh.**.entity
mybatis.mapperLocations=classpath:mybatis/**/*Mapper.xml
logging.level.team.zhh.dao=info

spring.shardingsphere.datasource.names=master39,slave136,slave137
spring.shardingsphere.masterslave.name=testcloud
spring.shardingsphere.masterslave.master-data-source-name=master39
spring.shardingsphere.masterslave.slave-data-source-names=slave136,slave137
spring.shardingsphere.masterslave.load-balance-algorithm-type=random
spring.shardingsphere.datasource.master39.type=com.zaxxer.hikari.HikariDataSource
spring.shardingsphere.datasource.master39.driver-class-name=com.mysql.jdbc.Driver
spring.shardingsphere.datasource.master39.jdbcUrl=jdbc:mysql://192.168.10.39:3306/testbase?autoReconnect=true&useUnicode=true&characterEncoding=utf8&useSSL=false&serverTimezone=CTT&allowMultiQueries=true
spring.shardingsphere.datasource.master39.username=root
spring.shardingsphere.datasource.master39.password=123456
spring.shardingsphere.datasource.master39.minimum-idle=8
spring.shardingsphere.datasource.master39.max-lifetime=1800000
spring.shardingsphere.datasource.master39.connection-timeout=30000
spring.shardingsphere.datasource.master39.idle-timeout=30000
spring.shardingsphere.datasource.master39.validation-timeout=3000
spring.shardingsphere.datasource.master39.connection-init-sql=SELECT 1
spring.shardingsphere.datasource.master39.maximum-pool-size=8
spring.shardingsphere.datasource.master39.pool-name=masterPool
spring.shardingsphere.datasource.master39.auto-commit=true
spring.shardingsphere.datasource.master39.enabled=true

spring.shardingsphere.datasource.slave136.type=com.zaxxer.hikari.HikariDataSource
spring.shardingsphere.datasource.slave136.driver-class-name=com.mysql.jdbc.Driver
spring.shardingsphere.datasource.slave136.jdbcUrl=jdbc:mysql://192.168.10.136:3306/testbase?autoReconnect=true&useUnicode=true&characterEncoding=utf8&useSSL=false&serverTimezone=CTT&allowMultiQueries=true
spring.shardingsphere.datasource.slave136.username=root
spring.shardingsphere.datasource.slave136.password=123456
spring.shardingsphere.datasource.slave136.minimum-idle=8
spring.shardingsphere.datasource.slave136.max-lifetime=1800000
spring.shardingsphere.datasource.slave136.connection-timeout=30000
spring.shardingsphere.datasource.slave136.idle-timeout=30000
spring.shardingsphere.datasource.slave136.validation-timeout=3000
spring.shardingsphere.datasource.slave136.connection-init-sql=SELECT 1
spring.shardingsphere.datasource.slave136.maximum-pool-size=8
spring.shardingsphere.datasource.slave136.pool-name=s1pool
spring.shardingsphere.datasource.slave136.auto-commit=true
spring.shardingsphere.datasource.slave136.enabled=true

spring.shardingsphere.datasource.slave137.type=com.zaxxer.hikari.HikariDataSource
spring.shardingsphere.datasource.slave137.driver-class-name=com.mysql.jdbc.Driver
spring.shardingsphere.datasource.slave137.jdbcUrl=jdbc:mysql://192.168.10.137:3306/testbase?autoReconnect=true&useUnicode=true&characterEncoding=utf8&useSSL=false&serverTimezone=CTT&allowMultiQueries=true
spring.shardingsphere.datasource.slave137.username=root
spring.shardingsphere.datasource.slave137.password=123456
spring.shardingsphere.datasource.slave137.minimum-idle=8
spring.shardingsphere.datasource.slave137.max-lifetime=1800000
spring.shardingsphere.datasource.slave137.connection-timeout=30000
spring.shardingsphere.datasource.slave137.idle-timeout=30000
spring.shardingsphere.datasource.slave137.validation-timeout=3000
spring.shardingsphere.datasource.slave137.connection-init-sql=SELECT 1
spring.shardingsphere.datasource.slave137.maximum-pool-size=8
spring.shardingsphere.datasource.slave137.pool-name=s2pool
spring.shardingsphere.datasource.slave137.auto-commit=true
spring.shardingsphere.datasource.slave137.enabled=true

spring.shardingsphere.props.sql.show=true

#spring.shardingsphere.orchestration.testsharding.orchestration-type=
#spring.shardingsphere.orchestration.testsharding.instance-type=nacos
#spring.shardingsphere.orchestration.testsharding.server-lists=localhost:8848
#spring.shardingsphere.orchestration.testsharding.namespace=sharding-test
#spring.shardingsphere.orchestration.testsharding.props.overwrite=true


spring.shardingsphere.orchestration.testsharding2.orchestration-type=registry_center,config_center
spring.shardingsphere.orchestration.testsharding2.instance-type=zookeeper
spring.shardingsphere.orchestration.testsharding2.server-lists=localhost:2181
spring.shardingsphere.orchestration.testsharding2.namespace=sharding-test
spring.shardingsphere.orchestration.testsharding2.props.overwrite=false
```

pom.xm

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>testCloud</artifactId>
        <groupId>team.zhh</groupId>
        <version>1.0-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>
    <artifactId>shardingJdbc</artifactId>

    <properties>
        <springboot-mybatis.version>1.1.1</springboot-mybatis.version>
        <shardingsphere.version>4.1.0</shardingsphere.version>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
            <version>${springboot-mybatis.version}</version>
        </dependency>
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-config</artifactId>
        </dependency>
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.36</version>
        </dependency>
        <dependency>
            <groupId>org.apache.commons</groupId>
            <artifactId>commons-pool2</artifactId>
        </dependency>
        <dependency>
            <groupId>commons-codec</groupId>
            <artifactId>commons-codec</artifactId>
        </dependency>

        <dependency>
            <groupId>org.apache.shardingsphere</groupId>
            <artifactId>sharding-jdbc-orchestration-spring-boot-starter</artifactId>
            <version>${shardingsphere.version}</version>
            <exclusions>
                <exclusion>
                    <groupId>org.apache.curator</groupId>
                    <artifactId>curator-framework</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
        <dependency>
            <groupId>org.apache.shardingsphere</groupId>
            <artifactId>sharding-orchestration-center-zookeeper-curator</artifactId>
            <version>${shardingsphere.version}</version>
            <exclusions>
                <exclusion>
                    <groupId>org.apache.curator</groupId>
                    <artifactId>curator-framework</artifactId>
                </exclusion>
                <exclusion>
                    <groupId>org.apache.curator</groupId>
                    <artifactId>curator-recipes</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
        <dependency>
            <groupId>org.apache.curator</groupId>
            <artifactId>curator-recipes</artifactId>
            <version>2.10.0</version>
        </dependency>
        <dependency>
            <groupId>org.apache.curator</groupId>
            <artifactId>curator-framework</artifactId>
            <version>2.10.0</version>
        </dependency>
    </dependencies>
    <build>
        <finalName>testSharding</finalName>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
</project>
```


##运行效果
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2dee950c8aeaf6c6364b97157f2bda0e.png)
主从热备情况下，如果发生故障，更改zk里面数据内容，将主服切换为从服，从服切换为主服即可，orchestration源码中watcher模块订阅了zk的事件，zk配置后会热更新datasource，也可以直接在shardingsphereUI中变更。

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/4be2b859a13fa2c802747a6e8efe589c.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/38f1bf03150952a58b91b84a58fb868e.png)
**UI变更比较方便，但是需要手动操作，最好在代码中自实现轮询校验数据库连接，并动态修改zk。**
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1650ddab3d0743920cb135bb890b70e7.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e11b1b184415f209fbb1d91c76926271.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/60011452d7aa572e9aa1ffd0ca8efb2f.png)
*代码修改效果同上*
```java
        try {
            Stat stat = zooKeeper.exists(path, false);
            if (stat != null) {
                String strData = "loadBalanceAlgorithmType: RANDOM\n" +
                        "masterDataSourceName: master39\n" +
                        "name: testcloud\n" +
                        "slaveDataSourceNames:\n" +
                        "- slave137\n" +
                        "- slave136\n";
                stat = zooKeeper.setData(path, strData.getBytes(), stat.getVersion()); // 版本号为-1时不做版本校验
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
```
