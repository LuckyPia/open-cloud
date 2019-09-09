## 什么是Open Cloud
### 简介
[Open Cloud](https://gitee.com/liuyadu/open-cloud/)是基于Spring Cloud、OAuth2、Nacos打造的微服务开放平台. 利于企业分布式开发,集中管理微服务接口,SpringSecurity深度拓展,为微服务接口资源保驾护航。

它的基础架构是Spring Cloud Alibaba , 他推荐使用的持久层框架为Mybatis-Plus。搭建基于OAuth2的开放平台、为APP端、应用服务提供统一接口管控平台、为第三方合作伙伴的业务对接提供授信可控的技术对接平台
  - Nacos(服务注册+配置中心)、Fegin(RPC服务调用)
  - 统一API网关（参数验签、身份认证、接口鉴权、接口调试）
  - 微服务间身份传递.使用Oauth2协议,统一认证管理!

简单来说，它搭建一些基础微服务并提供了通用问题解决方案，比如`网关微服务`，`用户微服务`，`基础微服务`等，还有一些公共类和方法。也就是说，`注册登录`、`用户管理`、`身份认证`、`权限管理`、`服务注册`、`网关路由`等这些都已经帮我们做好了，我们只需要写自己的服务就行了。

### Open Cloud技术选型
#### 依赖环境

*   nodejs
*   redis(缓存服务)
*   rabbitMq(消息服务)
*   nacos(阿里巴巴服务注册和配置管理)
*   mysql(数据库)

#### 后端技术

*   maven
*   springcloud
*   spring-security-oauth2
*   mybatis
*   mybatis-plus
*   swagger2
*   ...

#### 前端技术

*   vue.js
*   iview（前端框架）

#### 后端部署

*   jar包形式部署,使用undertow代替原有tomcat
*   jenkins持续集成

#### 前端部署

*   nginx

---
## 为什么选择Open Cloud
以前说的Spring Cloud通常指的是Spring Cloud Netflix，但是就在昨年（`2018-12-12`），Netflix宣布Spring Cloud Netflix进入维护期，就是不再添加新特性，也就是不再更新了。

所以我们只能选择其他微服务解决方案，目前市面上主流微服务架构还有`Spring Boot + Dubbo + Zookeeper`、`Spring Cloud Alibaba`这两套。如何选择？

这就要涉及到微服务一定会遇到的四个问题
- 这么多服务，客户端怎么访问
- 这么多服务，服务之间如何通信
- 这么多服务，如何治理
- 服务挂了，怎么办

**1. [Spring Cloud Netflix](https://spring.io/projects/spring-cloud-netflix)**
- API网关：`Zuul`
- 服务注册与发现：`Eureka`
- 服务通信：`Feign -> Http Client -> HTTP方式，同步并阻塞`
- 熔断机制：`Hystrix`

**2. [Apache Dubbo Zookeeper](http://zookeeper.apache.org/)**
- 服务通信：`Dubbo -> 高性能Java RPC通信框架` 
- 服务注册与发现：`Zookeeper`
- API网关：没有，找第三方
- 熔断机制：没有，找第三方
**注：这里指的是Dubbo 2.x版本**

**3. [Spring Cloud Alibaba](https://spring.io/blog/2018/10/30/spring-cloud-for-alibaba-0-2-0-released)**
**致力于微服务开发一站式解决方案** 
### 主要功能
- 服务限流降级：默认支持 Servlet、Feign、RestTemplate、Dubbo 和 RocketMQ 限流降级功能的接入，可以在运行时通过控制台实时修改限流降级规则，还支持查看限流降级 Metrics 监控。

- 服务注册与发现：适配 Spring Cloud 服务注册与发现标准，默认集成了 Ribbon 的支持。

- 分布式配置管理：支持分布式系统中的外部化配置，配置更改时自动刷新。

- 消息驱动能力：基于 Spring Cloud Stream 为微服务应用构建消息驱动能力。

- 阿里云对象存储：阿里云提供的海量、安全、低成本、高可靠的云存储服务。支持在任何应用、任何时间、任何地点存储和访问任意类型的数据。

- 分布式任务调度：提供秒级、精准、高可靠、高可用的定时（基于 Cron 表达式）任务调度服务。同时提供分布式的任务执行模型，如网格任务。网格任务支持海量子任务均匀分配到所有 Worker（schedulerx-client）上执行。
### 组件
- Sentinel：把流量作为切入点，从流量控制、熔断降级、系统负载保护等多个维度保护服务的稳定性。

- Nacos：一个更易于构建云原生应用的动态服务发现、配置管理和服务管理平台。

- RocketMQ：一款开源的分布式消息系统，基于高可用分布式集群技术，提供低延时的、高可靠的消息发布与订阅服务。

- Alibaba Cloud ACM：一款在分布式架构环境中对应用配置进行集中管理和推送的应用配置中心产品。

- Alibaba Cloud OSS: 阿里云对象存储服务（Object Storage Service，简称 OSS），是阿里云提供的海量、安全、低成本、高可靠的云存储服务。您可以在任何应用、任何时间、任何地点存储和访问任意类型的数据。

- Alibaba Cloud SchedulerX: 阿里中间件团队开发的一款分布式任务调度产品，提供秒级、精准、高可靠、高可用的定时（基于 Cron 表达式）任务调度服务。

Open Cloud又在Spring Cloud Alibaba的基础上搭建了基础微服务和基本解决方案，省去了搭建这些微服务的麻烦，只需要少量的配置，就可以写出自己**微服务**

---
## Open Cloud快速上手
**[参考资料](https://gitee.com/liuyadu/open-cloud/wikis/pages)**
**前提是项目环境已经配置好，项目包已(install)到本地仓库或发布(deploy)到私服仓库，[查看环境配置→](https://gitee.com/liuyadu/open-cloud/wikis/pages?sort_id=1337070&doc_id=256893)**

1. 新建父工程maven项目
   - 父工程groupId:`com.公司名`
   - 父工程artifactId:自己的项目名
2. 在父工程下新建子工程客户端和服务端
   - 子工程客户端artifactId:`项目名-client`
   - 子工程服务端artifactId:`项目名-server`
3. 父工程pom.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.公司名</groupId>
    <artifactId>项目名</artifactId>
    <packaging>pom</packaging>
    <version>1.0.0</version>
    <modules>
        <module>项目名-server</module>
        <module>项目名-client</module>
    </modules>

    <!--本地仓库地址-->
    <repositories>
        <repository>
            <id>maven-releases</id>
            <name>nexus release repo</name>
            <url>http://192.168.6.22:8081/repository/maven-public/</url>
        </repository>
    </repositories>
    <!--属性配置-->
    <properties>
        <java.version>1.8</java.version>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <maven.compiler.encoding>UTF-8</maven.compiler.encoding>
        <maven-compiler-plugin.version>3.6.2</maven-compiler-plugin.version>
        <maven-resources-plugin.version>3.1.0</maven-resources-plugin.version>
        <maven-source-plugin.version>3.0.1</maven-source-plugin.version>
        <maven-surefire-plugin.version>2.22.0</maven-surefire-plugin.version>
        <maven-assembly-plugin.version>3.1.0</maven-assembly-plugin.version>
        <dockerfile-maven-plugin.version>1.4.10</dockerfile-maven-plugin.version>
        <spring-boot.version>2.1.4.RELEASE</spring-boot.version>
        <spring-boot-admin.version>2.1.4</spring-boot-admin.version>
        <spring-cloud.version>Greenwich.SR1</spring-cloud.version>
        <alibaba.cloud.version>0.9.0.RELEASE</alibaba.cloud.version>
        <alibaba.fastjson.version>1.2.37</alibaba.fastjson.version>

        <apache.commons-lang3.version>3.3.2</apache.commons-lang3.version>
        <apache.commons-io.version>2.5</apache.commons-io.version>
        <apache.commons.beanutils>1.9.3</apache.commons.beanutils>

        <mybatis-plus.version>3.1.1</mybatis-plus.version>
        <hutool.version>4.1.19</hutool.version>
        <com.google.zxing.version>3.1.0</com.google.zxing.version>
        <swagger2.version>2.9.2</swagger2.version>
        <oracle.version>10.2.0.4.0</oracle.version>

        <!--自定义版本-->
        <opencloud.common.version>3.0.0-SNAPSHOT</opencloud.common.version>
        <opencloud.base-client.version>3.0.0-SNAPSHOT</opencloud.base-client.version>
        <opencloud.msg-client.version>3.0.0-SNAPSHOT</opencloud.msg-client.version>
        <opencloud.bpm-client.version>3.0.0-SNAPSHOT</opencloud.bpm-client.version>
        <opencloud.task-client.version>3.0.0-SNAPSHOT</opencloud.task-client.version>
        <!--镜像前缀-->
        <docker.image.prefix>open</docker.image.prefix>
    </properties>

    <!-- 环境，需配置自己的Nacos信息 -->
    <profiles>
        <profile>
            <id>public</id>
            <properties>
                <!--当前环境-->
                <profile.name>public</profile.name>
                <!--Nacos配置中心地址-->
                <config.server-addr>192.168.6.22:8848</config.server-addr>
                <!--Nacos配置中心命名空间,用于支持多环境.这里必须使用ID，不能使用名称,默认为空-->
                <config.namespace></config.namespace>
                <!--Nacos服务发现地址-->
                <discovery.server-addr>192.168.6.22:8848</discovery.server-addr>
                <!--Nacos服务注册IP前缀配置-->
                <inetutils.preferred-networks>192.168.6</inetutils.preferred-networks>
            </properties>
        </profile>
        <!-- 开发 -->
        <profile>
            <id>dev</id>
            <properties>
                <!--当前环境-->
                <profile.name>dev</profile.name>
                <!--Nacos配置中心地址-->
                <config.server-addr>192.168.6.22:8848</config.server-addr>
                <!--Nacos配置中心命名空间,用于支持多环境.这里必须使用ID，不能使用名称,默认为空-->
                <config.namespace>c0d73078-55cd-4f63-a36c-29811da8683e</config.namespace>
                <!--Nacos服务发现地址-->
                <discovery.server-addr>192.168.6.22:8848</discovery.server-addr>
                <!--Nacos服务注册IP前缀配置-->
                <inetutils.preferred-networks>192.168.6</inetutils.preferred-networks>
            </properties>
        </profile>
        <!-- 测试 -->
        <profile>
            <id>test</id>
            <properties>
                <!--当前环境-->
                <profile.name>test</profile.name>
                <!--Nacos配置中心地址-->
                <config.server-addr>192.168.6.22:8848</config.server-addr>
                <!--Nacos配置中心命名空间,用于支持多环境.这里必须使用ID，不能使用名称,默认为空-->
                <config.namespace>7d58d1a0-4b5c-4e68-ae40-1bf34376446a</config.namespace>
                <!--Nacos服务发现地址-->
                <discovery.server-addr>192.168.6.22:8848</discovery.server-addr>
                <!--Nacos服务注册IP前缀配置-->
                <inetutils.preferred-networks>192.168.6</inetutils.preferred-networks>
            </properties>
        </profile>
        <!-- 生产 -->
        <profile>
            <id>pro</id>
            <activation>
                <!--默认激活配置-->
                <activeByDefault>true</activeByDefault>
            </activation>
            <properties>
                <!--当前环境,生产环境为空-->
                <profile.name>pro</profile.name>
                <!--Nacos配置中心地址-->
                <config.server-addr>192.168.6.22:8848</config.server-addr>
                <!--Nacos配置中心命名空间,用于支持多环境.这里必须使用ID，不能使用名称,默认为空-->
                <config.namespace>ce78c4f6-0405-45ed-8b6b-483210c2995e</config.namespace>
                <!--Nacos服务发现地址-->
                <discovery.server-addr>192.168.6.22:8848</discovery.server-addr>
                <!--Nacos服务注册IP前缀配置-->
                <inetutils.preferred-networks>192.168.6</inetutils.preferred-networks>
            </properties>
        </profile>
    </profiles>

    <!--依赖管理-->
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-alibaba-dependencies</artifactId>
                <version>${alibaba.cloud.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-dependencies</artifactId>
                <version>${spring-boot.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-dependencies</artifactId>
                <version>${spring-cloud.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
    <build>
        <resources>
            <!-- 先指定 src/main/resources下所有文件及文件夹为资源文件 -->
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>**/*</include>
                </includes>
                <filtering>true</filtering>
            </resource>
        </resources>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>${maven-compiler-plugin.version}</version>
                <configuration>
                    <source>${java.version}</source>
                    <target>${java.version}</target>
                    <encoding>${maven.compiler.encoding}</encoding>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-resources-plugin</artifactId>
                <version>${maven-resources-plugin.version}</version>
            </plugin>
            <plugin>
                <!--打包跳过测试-->
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>${maven-surefire-plugin.version}</version>
                <configuration>
                    <skipTests>true</skipTests>
                </configuration>
            </plugin>

        </plugins>
    </build>


</project>
```

4. 子工程客户端pom.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>项目名</artifactId>
        <groupId>com.公司名</groupId>
        <version>1.0.0</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>项目名-client</artifactId>

    <version>1.0.0</version>
    <packaging>jar</packaging>
    <description>项目资源服务接口</description>

    <dependencies>
        <!-- 引入公共包,需(install)到本地仓库或发布(deploy)到私服仓库 -->
        <dependency>
            <groupId>cn.recse</groupId>
            <artifactId>open-cloud-common-core</artifactId>
            <version>${opencloud.common.version}</version>
        </dependency>

    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-source-plugin</artifactId>
                <version>${maven-source-plugin.version}</version>
                <executions>
                    <execution>
                        <id>attach-sources</id>
                        <goals>
                            <goal>jar</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>


</project>
```

5. 子工程服务端pom.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>项目名</artifactId>
        <groupId>com.公司名</groupId>
        <version>1.0.0</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>项目-server</artifactId>
    <description>项目资源服务</description>
    <packaging>jar</packaging>

    <dependencies>
        <!-- 引入公共包,需(install)到本地仓库或发布(deploy)到私服仓库 -->
        <dependency>
            <groupId>cn.recse</groupId>
            <artifactId>open-cloud-common-starter</artifactId>
            <version>3.0.0-SNAPSHOT</version>
        </dependency>
        <!--引入客户端依赖-->
        <dependency>
            <groupId>com.公司名</groupId>
            <artifactId>项目名-client</artifactId>
            <version>1.0.0</version>
        </dependency>

    </dependencies>
    <build>
        <!-- 打包名称 -->
        <finalName>${project.artifactId}</finalName>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <version>${spring-boot.version}</version>
                <executions>
                    <execution>
                        <goals>
                            <goal>repackage</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>

            <!-- docker打包插件 -->
            <plugin>
                <groupId>com.spotify</groupId>
                <artifactId>dockerfile-maven-plugin</artifactId>
                <version>${dockerfile-maven-plugin.version}</version>
                <configuration>
                    <repository>${docker.image.prefix}/${project.artifactId}</repository>
                    <buildArgs>
                        <JAR_FILE>target/${project.build.finalName}.jar</JAR_FILE>
                    </buildArgs>
                </configuration>
            </plugin>

        </plugins>

    </build>

</project>
```

6. 在Nacos对应环境上添加自己的配置文件(Nacos地址:`192.168.6.22:8848/nacos`)
Data Id:`项目名.properties`
```properties
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://127.0.0.1:3306/数据库名?useSSL=false&useUnicode=true&characterEncoding=utf-8&serverTimezone=Asia/Shanghai
spring.datasource.username=用户名
spring.datasource.password=密码
#\u4F7F\u7528springboot\u9ED8\u8BA4HikariCP\u8FDE\u63A5\u6C60
spring.datasource.type=com.zaxxer.hikari.HikariDataSource

#oracle
#spring.datasource.driver-class-name=oracle.jdbc.driver.OracleDriver
#spring.datasource.url=jdbc:oracle:thin:@localhost:1521:open-platform
```

7. 在服务端下创建bootstrap.yml（这里的`项目名.properties`需与Nacos上的`Data ID`一致）
```yaml
server:
  port: 8100
spring:
  application:
    name: ${artifactId}
  cloud:
    nacos:
      config:
        namespace: ${config.namespace}
        refreshable-dataids: common.properties,项目名.properties,redis.properties,rabbitmq.properties
        server-addr: ${config.server-addr}
        shared-dataids: common.properties,项目名.properties,redis.properties,rabbitmq.properties
      discovery:
        server-addr: ${discovery.server-addr}
        namespace: ${config.namespace}
    # IP前缀选择，不配置可能会导致微服务注册错误的IP地址
    inetutils:
      preferred-networks: ${inetutils.preferred-networks}

  main:
    allow-bean-definition-overriding: true
  mvc:
    throw-exception-if-no-handler-found: true
  resources:
    add-mappings: false
  profiles:
    active: ${profile.name}

management:
  endpoints:
    web:
      exposure:
        include: '*'

mybatis-plus:
  #实体扫描，多个package用逗号或者分号分隔
  typeAliasesPackage: com.公司名.项目名.client.model.entity
  mapper-locations: classpath:mapper/*.xml
  global-config:
    db-config:
      logic-delete-value: 1
      logic-not-delete-value: 0

opencloud:
  swagger2:
    description: 微服务描述
    enabled: true
    title: 微服务标题
```

8. 在服务端下创建启动类 `项目名Application.java`
```java
import org.mybatis.spring.annotation.MapperScan;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.client.discovery.EnableDiscoveryClient;
import org.springframework.cloud.openfeign.EnableFeignClients;

// 开启feign
@EnableFeignClients
// 开启服务发现
@EnableDiscoveryClient
// Mapper扫描
@MapperScan(basePackages = "com.公司名.项目名.server.mapper")
@SpringBootApplication
public class 项目名Application {

    public static void main(String[] args) {
        SpringApplication.run(项目名Application.class,args);
    }
}
```
![客户端目录结构](https://upload-images.jianshu.io/upload_images/15247235-757f49dc9c3af53c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![服务端目录结构](https://upload-images.jianshu.io/upload_images/15247235-21e50080c6b103c3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

9. 在服务端下创建`ResourceServerConfiguration.java` 资源服务器安全配置
```java
import com.opencloud.common.exception.OpenAccessDeniedHandler;
import com.opencloud.common.exception.OpenAuthenticationEntryPoint;
import com.opencloud.common.security.OpenHelper;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.actuate.autoconfigure.security.servlet.EndpointRequest;
import org.springframework.context.annotation.Configuration;
import org.springframework.data.redis.connection.RedisConnectionFactory;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.http.SessionCreationPolicy;
import org.springframework.security.oauth2.config.annotation.web.configuration.EnableResourceServer;
import org.springframework.security.oauth2.config.annotation.web.configuration.ResourceServerConfigurerAdapter;
import org.springframework.security.oauth2.config.annotation.web.configurers.ResourceServerSecurityConfigurer;

@Configuration
@EnableResourceServer
public class ResourceServerConfiguration extends ResourceServerConfigurerAdapter {
    @Autowired
    private RedisConnectionFactory redisConnectionFactory;

    @Override
    public void configure(ResourceServerSecurityConfigurer resources) throws Exception {
        // 构建redis获取解析token
        resources.tokenServices(OpenHelper.buildRedisTokenServices(redisConnectionFactory));
    }

    @Override
    public void configure(HttpSecurity http) throws Exception {
        http.sessionManagement().sessionCreationPolicy(SessionCreationPolicy.IF_REQUIRED)
                .and()
                .authorizeRequests()
                // 注意：根据业务需求,指定接口访问权限, fegin方式调用的接口,可以直接放行. 考虑到通过网关也可以直接访问,在接口管理中设置“禁止公开访问”即可
                .antMatchers().permitAll()
                // 指定监控访问权限
                .requestMatchers(EndpointRequest.toAnyEndpoint()).permitAll()
                .anyRequest().authenticated()
                .and()
                //认证鉴权错误处理,为了统一异常处理。每个资源服务器都应该加上。
                .exceptionHandling()
                .accessDeniedHandler(new OpenAccessDeniedHandler())
                .authenticationEntryPoint(new OpenAuthenticationEntryPoint())
                .and()
                .csrf().disable();
    }

}
```

**微服务调用**
接口调用方式分为：

- 外部调用 - 通过网关统一入口调用,通过oauth2协议获取access_token,统一验证调用接口权限,验证参数签名。
- 内部调用 - fegin+rabbion方式,负载到目标服务,由微服务自身验证权限,无需验证参数签名。
1. 客户端创建资源服务fegin接口 ITestClient.interface
```java
public interface ITestClient{
    /**
     * 你好
     * @return
     */
    @PostMapping("/say/hi")
    ResultBody<String> sayHi(
         @RequestParam String message
    );
}
```

2. 服务端实现 项目名-client fegin接口
```java
@RestController
@Api(value = "测试", tags = "测试")
public class TestController implements ITestClient {

    @ApiOperation(value = "打招呼",notes = "招呼")
    @PostMapping("/say/hi")
    @Override
    public ResultBody<String> sayHi(@RequestParam String message) {
        return ResultBody.ok().data("你好！");
    }

}
```

3. 服务消费者-fegin调用 在使用方项目中创建fegin使用类,继承服务提供方接口
```java
@Component
@FeignClient(value = "项目名-server")
public interface TestServiceClient extends ITestClient {


}

//fegin 接口注入与调用
@Autowired
private TestServiceClient testServiceClient;

public void customer(){
    testServiceClient.sayHi("你好啊");
}
```

**服务启动后网关配置**
1. 进入后台管理 - API网关 - 网关路由 
![添加路由](https://upload-images.jianshu.io/upload_images/15247235-4d4bd07b02846401.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 配置相关接口信息
![编辑接口](https://upload-images.jianshu.io/upload_images/15247235-7d9a955dbe24a996.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**用Postman调试接口**
1. Postman获取access_token
- `post:`192.168.6.22:8888/admin/login/token
- username:`admin`
- password:`123456`
![获取access_token](https://upload-images.jianshu.io/upload_images/15247235-95fc1ca0b234409c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. Postman设置access_token
在Authorization中选中Bearer Token，然后输入获取到的access_token，就可以进行接口调试了
![设置access_token](https://upload-images.jianshu.io/upload_images/15247235-8f498569e3441380.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 统一标准参考
**数据库设计**
1. 数据库命名以及字段命名为小写字母，字母之间使用`_`隔开
2. 数据库和表格字符集采用`utfmb4`
3. 表格类型为`InnoDB`
3. 数据库字段和表格均要写`描述`
4. 主键`id`为`varchar(32)`(使用`IdWorker.getIdStr()`生成)
6. 每个表格统一有`create_time`,`update_time`,`del_type`字段，分别表示`创建事件`，`更新时间`，`删除标记`(0未删1已删)
7. 时间类型使用`datetime`
8. 布尔类型使用`tinyint`
9. 关联其他表`id`使用`表名_id`

![数据库表设计](https://upload-images.jianshu.io/upload_images/15247235-9bd5a367bd0fe45f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**代码规范**
推荐使用插件[MybatisCodeHelperPro](https://plugins.jetbrains.com/plugin/9837-mybatiscodehelperpro)（付费，可试用7天）
-  类与方法，均要写注释，复杂的方法需要给出步骤思路
- entity规范（不是必须）
   1. 继承`AbstractEntity`类(AbstractEntity中有createTime和updateTime)，实现`Serializable`接口
   2. 时间类型采用`Date`
   3. 实例类前要加`@ApiModel(value = "com.公司名.项目名.client.model.entity.实例名")`
   4. 每个变量前要加@ApiModelProperty(value = "变量说明")
- service接口需继承IBaseService<Config>类（不是必须）
- service实现需继承BaseServiceImpl<ConfigMapper, Config>，实现ConfigService接口（不是必须）
- mapper需实现SuperMapper<Config>接口（不是必须）

以Config为例
```java
import com.baomidou.mybatisplus.annotation.IdType;
import com.baomidou.mybatisplus.annotation.TableField;
import com.baomidou.mybatisplus.annotation.TableId;
import com.baomidou.mybatisplus.annotation.TableName;
import com.fasterxml.jackson.annotation.JsonIgnore;
import com.opencloud.common.mybatis.base.entity.AbstractEntity;
import io.swagger.annotations.ApiModel;
import io.swagger.annotations.ApiModelProperty;
import java.io.Serializable;

import lombok.Data;

@ApiModel(value = "com.myproject.test.client.model.entity.Config")
@Data
@TableName(value = "config")
public class Config extends AbstractEntity implements Serializable {
    @TableId(value = "id", type = IdType.ID_WORKER)
    @ApiModelProperty(value = "null")
    private String id;

    /**
     * key为保留字，设为key查询会报错
     */
    @TableField(value = "key_")
    @ApiModelProperty(value = "key为保留字，设为key查询会报错")
    private String key;

    /**
     * 值
     */
    @TableField(value = "value")
    @ApiModelProperty(value = "值")
    private String value;

    /**
     * 别名
     */
    @TableField(value = "alias")
    @ApiModelProperty(value = "别名")
    private String alias;

    /**
     * 删除标记(0未删1已删)
     */
    @TableField(value = "del_type")
    @TableLogic // 逻辑删除注解
    @ApiModelProperty(value = "删除标记(0未删1已删)")
    @JsonIgnore
    private Integer delType;

    private static final long serialVersionUID = 1L;

    public static final String COL_ID = "id";

    public static final String COL_KEY_ = "key_";

    public static final String COL_VALUE = "value";

    public static final String COL_ALIAS = "alias";

    public static final String COL_DEL_TYPE = "del_type";

}
```

ConfigDto
```java
import io.swagger.annotations.ApiModel;
import io.swagger.annotations.ApiModelProperty;
import java.io.Serializable;

import lombok.Data;

@ApiModel(value = "com.swstsoft.birds.client.model.dto.ConfigDto")
@Data
public class Config implements Serializable {

    @ApiModelProperty(value = "null")
    private String id;

    /**
     * key为保留字，设为key查询会报错
     */
    @ApiModelProperty(value = "key为保留字，设为key查询会报错")
    private String key;

    /**
     * 值
     */
    @ApiModelProperty(value = "值")
    private String value;

    /**
     * 别名
     */
    @ApiModelProperty(value = "别名")
    private String alias;

    private static final long serialVersionUID = 1L;

}
```
- 接口规范
   接口swagger接口类说明@Api(tags = "信息管理")
```java
/**
 * @author my
 * @date 2019-08-28 09:29:11
 **/
@Api(tags = "配置管理")
@RestController
@RequestMapping("/config")
@Slf4j
```

---
   接口swagger方法说明@ApiOperation(value = "获取搜索分页数据", notes = "获取搜索分页数据")
   1. **分页搜索数据接口**
controller
```java
    @Resource
    private ConfigService configService;

    /**
     * 功能描述:获取搜索分页数据
     *
     * @param map
     * @return ResultBody<com.baomidou.mybatisplus.core.metadata.IPage < com.myproject.test.client.model.dto. ConfigDto>>
     * @author my
     * @date 2019-08-28 09:22:32
     */
    @ApiOperation(value = "获取搜索分页数据", notes = 获取搜索分页数据")
    @GetMapping("/list")
    public ResultBody<IPage<ConfigDto>> list(@RequestParam(required = false) Map map) {
        return ResultBody.ok(configService.findListPage(new PageParams(map)));
    }
```
serviceImpl
```java
    @Resource
    private ConfigMapper configMapper;

    @Override
    public IPage<ConfigDto> findListPage(PageParams pageParams) {

        // 1。 获取查询参数
        Config query = pageParams.mapToObject(Config.class);
        // 2。 获取分页参数
        Page<BirdDto> page = pageParams.getIPage();
        // 3. 查询并返回
        return page.setRecords(birdMapper.findListPage(page, query));
    }
```
mapper
```java
// @Param一定要写
List<ConfigDto> findListPage(@Param("page") Page page, @Param("query") Bird query);
```
xml
```xml
<select id="findListPage"
            resultType="com.公司名.项目名.client.model.dto.ConfigDto">
        select
        a.id as id,
        a.key_ as key,
        a.value as value,
        a.alias as alias,
        from config a
        where a.del_type=0
        <if test="query.alias != null and query.alias != ''">
            and a.alias like concat('%',#{query.alias,jdbcType=VARCHAR},'%')
        </if>
    </select>
```
   2. **全部数据接口**
controller
```java
    @Resource
    private ConfigService configService;

    @ApiOperation(value = "获取全部配置数据", notes = "获取全部配置数据")
    @GetMapping("/all")
    public ResultBody<List<ConfigDto>> all() {
        return ResultBody.ok(configService.list());
    }
```

   3. **数据详情接口**
controller
```java
    @Resource
    private ConfigService configService;

    @GetMapping("/detail/{id}")
    public ResultBody<Config> detail(@PathVariable("id") String id) {
        if (!configService.isExist(id)) {
            throw new OpenAlertException("所要查找的鸟类不存在!请尝试刷新列表");
        }
        return ResultBody.ok(configService.getById(id));
    }
```

   4. **添加数据接口**
controller
```java
    @Resource
    private ConfigService configService;

    @PostMapping("/add")
    public ResultBody add(Config config) {
        return configService.addConfig(config) ? ResultBody.ok().msg(config.getAlias() + " 添加成功") : ResultBody.failed().msg("添加失败");
    }
```
service接口
```java
boolean addConfig(Config config);
```
serviceImpl
```java
    @Override
    public boolean addConfig(Config config) {
        config.setId(IdWorker.getIdStr());
        return save(config);
    }
```

   5. **修改数据接口**
controller
```java
    @Resource
    private ConfigService configService;

    @PostMapping({"/update/{id}","/edit/{id}"})
    public ResultBody update(@PathVariable("id") String id, Config config) {
        if (!configService.isExist(id)) {
            return ResultBody.failed().msg("所要编辑的配置不存在!请尝试刷新列表");
        }
        config.setId(id);
        boolean b = configService.save(config);
        return b ? ResultBody.ok() : ResultBody.failed();
    }
```

   6. **删除数据接口**
controller
```java
    @Resource
    private ConfigService configService;

    @PostMapping({"/remove/{id}", "/delete/{id}"})
    public ResultBody remove(@PathVariable("id") String id) {
        // 1. 根据id判断信息是否存在
        if (!configService.isExist(id)) {
            return ResultBody.failed().msg("所要删除的配置不存在!请尝试刷新列表");
        }
        return configService.removeById(id) ? ResultBody.ok() : ResultBody.failed().msg("删除失败");
    }
```
   7. **批量删除数据接口(有问题)**
controller
```java
    @Resource
    private ConfigService configService;

    @PostMapping({"/remove-batch", "/delete-batch"})
    public ResultBody removeBatch(List<String> idList) {
        if (idList!= null) {
            return configService.removeByIds(idList) ? ResultBody.ok() : ResultBody.failed();
        }
        return ResultBody.failed().msg("数据不能为空");
    }
```

   8. **检查数据唯一性接口**
controller
```java
    @Resource
    private ConfigService configService;

    @PostMapping("/check-unique")
    public ResultBody<Boolean> checkUnique(Config config) {
        return configService.checkUnique(config) ? ResultBody.ok(true) : ResultBody.ok(false);
    }
```
serviceImpl
```java
    @Override
    public boolean checkUnique(Config config) {
        return 0 == lambdaQuery()
                .eq(StringUtils.isNotBlank(config.getKey()), Config::getKey, config.getKey())
                .eq(StringUtils.isNotBlank(config.getAlias()), Config::getAlias, config.getAlias())
                .notIn(StringUtils.isNotBlank(config.getId()), Config::getId, config.getId())
                .count();
    }
```
---
   9. **检查数据是否存在接口**
controller
```java
    @Resource
    private ConfigService configService;

    @PostMapping("/is-exist")
    public ResultBody<Boolean> isExist(String id) {
        return configService.isExist(id) ? ResultBody.ok(true) : ResultBody.ok(false);
    }
```
serviceImpl
```java
    @Override
    public boolean isExist(String id) {
        return lambdaQuery().eq(true, Config::getId, id).count() > 0;
    }
```
---

**注意：我的`ResultBody`和`PageParams`在原来地1基础上做了一些修改**
ResultBody
```java
import com.alibaba.fastjson.annotation.JSONField;
import com.fasterxml.jackson.annotation.JsonIgnore;
import com.google.common.collect.Maps;
import com.opencloud.common.constants.ErrorCode;
import io.swagger.annotations.ApiModel;
import io.swagger.annotations.ApiModelProperty;
import java.io.Serializable;
import java.util.Map;
import java.util.ResourceBundle;

@ApiModel("响应结果")
public class ResultBody<T> implements Serializable {
    private static final long serialVersionUID = -6190689122701100762L;
    @ApiModelProperty("响应编码:0-请求处理成功")
    private int code = 0;
    @ApiModelProperty("提示消息")
    private String message;
    @ApiModelProperty("请求路径")
    private String path;
    @ApiModelProperty("响应数据")
    private T data;
    private int httpStatus;
    @ApiModelProperty("附加数据")
    private Map<String, Object> extra;
    @ApiModelProperty("响应时间")
    private long timestamp = System.currentTimeMillis();
    @JSONField(
        serialize = false,
        deserialize = false
    )
    @JsonIgnore
    private static ResourceBundle resourceBundle = ResourceBundle.getBundle("error");

    public ResultBody() {
    }
    
    // 增加了构造方法
    private ResultBody(int code, String message) {
        this.code = code;
        this.message = message;
    }

    // 增加了构造方法
    private ResultBody(int code, String message, T data) {
        this.code = code;
        this.message = message;
        this.data = data;
    }

    public int getCode() {
        return this.code;
    }

    public String getMessage() {
        return this.message;
    }

    public String getPath() {
        return this.path;
    }

    public T getData() {
        return this.data;
    }

    public Map<String, Object> getExtra() {
        return this.extra;
    }

    public long getTimestamp() {
        return this.timestamp;
    }

    @JSONField(
        serialize = false,
        deserialize = false
    )
    @JsonIgnore
    public int getHttpStatus() {
        return this.httpStatus;
    }

    @JSONField(
        serialize = false,
        deserialize = false
    )
    @JsonIgnore
    public boolean isOk() {
        return this.code == ErrorCode.OK.getCode();
    }

    // 修改了此方法，不会再出现警告
    public static ResultBody ok() {
        return new ResultBody(ErrorCode.OK.getCode(), ErrorCode.OK.getMessage());
    }

    // 增加了此方法
    public static <T> ResultBody<T> ok(T data) {
        return new ResultBody(ErrorCode.OK.getCode(), ErrorCode.OK.getMessage(), data);
    }

    public static ResultBody failed() {
        return new ResultBody(ErrorCode.FAIL.getCode(), ErrorCode.FAIL.getMessage());
    }

    public ResultBody code(int code) {
        this.code = code;
        return this;
    }

    public ResultBody msg(String message) {
        this.message = i18n(ErrorCode.getResultEnum(this.code).getMessage(), message);
        return this;
    }

    public ResultBody<T> data(T data) {
        this.data = data;
        return this;
    }

    public ResultBody path(String path) {
        this.path = path;
        return this;
    }

    public ResultBody httpStatus(int httpStatus) {
        this.httpStatus = httpStatus;
        return this;
    }

    public ResultBody put(String key, Object value) {
        if (this.extra == null) {
            this.extra = Maps.newHashMap();
        }

        this.extra.put(key, value);
        return this;
    }

    public String toString() {
        return "ResultBody{code=" + this.code + ", message='" + this.message + '\'' + ", path='" + this.path + '\'' + ", data=" + this.data + ", httpStatus=" + this.httpStatus + ", extra=" + this.extra + ", timestamp=" + this.timestamp + '}';
    }

    @JSONField(
        serialize = false,
        deserialize = false
    )
    @JsonIgnore
    private static String i18n(String message, String defaultMessage) {
        return resourceBundle.containsKey(message) ? resourceBundle.getString(message) : defaultMessage;
    }
}
```
PageParams
```java
import com.baomidou.mybatisplus.extension.plugins.pagination.Page;
import com.google.common.collect.Maps;
import com.opencloud.common.utils.BeanConvertUtils;
import com.opencloud.common.utils.StringUtils;
import java.io.Serializable;
import java.util.Map;

public class PageParams extends Page implements Serializable {
    private static final long serialVersionUID = -1710273706052960025L;
    private int page;
    private int limit;
    private String sort;
    private String order;
    private Map<String, Object> requestMap;
    private String orderBy;

    public PageParams() {
        this.page = 1;
        this.limit = 10;
        this.requestMap = Maps.newHashMap();
        this.requestMap = Maps.newHashMap();
    }

    public PageParams(Map map) {
        this.page = 1;
        this.limit = 10;
        this.requestMap = Maps.newHashMap();
        if (map == null) {
            map = Maps.newHashMap();
        }

        this.page = Integer.parseInt(((Map)map).getOrDefault("page", 1).toString());
        this.limit = Integer.parseInt(((Map)map).getOrDefault("limit", 10).toString());
        this.sort = (String)((Map)map).getOrDefault("sort", "");
        this.order = (String)((Map)map).getOrDefault("order", "");
        super.setCurrent((long)this.page);
        super.setSize((long)this.limit);
        ((Map)map).remove("page");
        ((Map)map).remove("limit");
        ((Map)map).remove("sort");
        ((Map)map).remove("order");
        this.requestMap.putAll((Map)map);
    }

    public PageParams(int page, int limit) {
        this(page, limit, "", "");
    }

    public PageParams(int page, int limit, String sort, String order) {
        this.page = 1;
        this.limit = 10;
        this.requestMap = Maps.newHashMap();
        this.page = page;
        this.limit = limit;
        this.sort = sort;
        this.order = order;
    }

    public int getPage() {
        if (this.page <= 0) {
            this.page = 1;
        }

        return this.page;
    }

    public void setPage(int page) {
        this.page = page;
    }

    public int getLimit() {
        if (this.limit > 999) {
            this.limit = 999;
        }

        return this.limit;
    }

    public void setLimit(int limit) {
        this.limit = limit;
    }

    public String getSort() {
        return this.sort;
    }

    public void setSort(String sort) {
        this.sort = sort;
    }

    public String getOrder() {
        return this.order;
    }

    public void setOrder(String order) {
        this.order = order;
    }

    public String getOrderBy() {
        if (StringUtils.isBlank(this.order)) {
            this.order = "asc";
        }

        if (StringUtils.isNotBlank(this.sort)) {
            this.setOrderBy(String.format("%s %s", StringUtils.camelToUnderline(this.sort), this.order));
        }

        return this.orderBy;
    }

    public void setOrderBy(String orderBy) {
        this.orderBy = orderBy;
    }
    
    // 增加了该方法
    public <T> Page<T> getIPage() {
        Page<T> p = new Page();
        p.setSize((long)this.limit);
        p.setCurrent((long)this.page);
        if ("asc".equals(this.order)) {
            p.setAsc(new String[]{StringUtils.camelToUnderline(this.sort)});
        } else {
            p.setDesc(new String[]{StringUtils.camelToUnderline(this.sort)});
        }

        return p;
    }

    public <T> T mapToObject(Class<T> t) {
        return BeanConvertUtils.mapToObject(this.requestMap, t);
    }

    public Map<String, Object> getRequestMap() {
        return this.requestMap;
    }

    public void setRequestMap(Map<String, Object> requestMap) {
        this.requestMap = requestMap;
    }
}
```

## 扩展
### Maven deploy部署jar到远程私服仓库
**1. 配置私服账号密码**
修改maven配置文件，在$MAVEN_HOME/conf/setting.xml中增加如下配置：

```xml
<servers>
  <server>  
    <id>releases</id>  
    <username>admin</username>  
    <password>admin123</password>  
  </server>  
 <server>  
  <id>snapshots</id>  
  <username>admin</username>  
  <password>admin123</password>  
  </server> 
</servers>
```

**2. 配置远程发布到私服**
修改项目pom文件，增加如下配置: 

```xml
<!--发布到私服: 设置 version 后，选择 maven 的 deploy 命令-->
<distributionManagement>
    <repository>
        <id>releases</id>
        <name>nexus Repository RELEASES</name>
        <url>http://192.168.6.22:8081/repository/maven-releases/</url>
    </repository>
    <snapshotRepository>
        <id>snapshots</id>
        <name>nexus Repository SNAPSHOTS</name>
        <url>http://192.168.6.22:8081/repository/maven-snapshots/</url>
    </snapshotRepository>
</distributionManagement>
```
**注意:这里的id就是之前配置的id**

**3. 执行部署操作**
- 方式一:直接使用`mvn deploy`命令
- 方式二:使用IDE中的maven快捷操作，以idea为例，双击deploy即可


[参考资料](https://www.funtl.com/zh/spring-cloud-alibaba/#%E6%9C%AC%E8%8A%82%E8%A7%86%E9%A2%91)

