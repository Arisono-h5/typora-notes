

SpringBoot入门(6)- 添加Logback日志

# SpringBoot入门 - 添加Logback日志

> SpringBoot开发中如何选用日志框架呢？ 出于性能等原因，Logback 目前是springboot应用日志的标配； 当然有时候在生产环境中也会考虑和三方中间件采用统一处理方式。@pdai

- SpringBoot入门 - 添加Logback日志
  - 日志框架的基础
    - [关于日志框架（日志门面）](https://help.aliyun.com/zh/yunxiao/user-guide/quickly-create-and-deploy-spring-boot-experience-applications?scm=20140722.S_help@@%E6%96%87%E6%A1%A3@@2797582.S_RQW@ag0+BB2@ag0+BB1@ag0.ID_2797582-RL_Springboot-LOC_search~UND~helpdoc~UND~item-OR_ser-V_4-P0_27&source=5176.29345612&userCode=ywqc0ubl)
    - [配置时考虑点](https://help.aliyun.com/zh/yunxiao/user-guide/quickly-create-and-deploy-spring-boot-experience-applications?scm=20140722.S_help@@%E6%96%87%E6%A1%A3@@2797582.S_RQW@ag0+BB2@ag0+BB1@ag0.ID_2797582-RL_Springboot-LOC_search~UND~helpdoc~UND~item-OR_ser-V_4-P0_27&source=5176.29345612&userCode=ywqc0ubl)
  - 实现范例
    - [综合范例](https://help.aliyun.com/zh/yunxiao/user-guide/quickly-create-and-deploy-spring-boot-experience-applications?scm=20140722.S_help@@%E6%96%87%E6%A1%A3@@2797582.S_RQW@ag0+BB2@ag0+BB1@ag0.ID_2797582-RL_Springboot-LOC_search~UND~helpdoc~UND~item-OR_ser-V_4-P0_27&source=5176.29345612&userCode=ywqc0ubl)
    - [在配置前可以参考如下文章](https://help.aliyun.com/zh/yunxiao/user-guide/quickly-create-and-deploy-spring-boot-experience-applications?scm=20140722.S_help@@%E6%96%87%E6%A1%A3@@2797582.S_RQW@ag0+BB2@ag0+BB1@ag0.ID_2797582-RL_Springboot-LOC_search~UND~helpdoc~UND~item-OR_ser-V_4-P0_27&source=5176.29345612&userCode=ywqc0ubl)
  - [參考文档](https://help.aliyun.com/zh/yunxiao/user-guide/quickly-create-and-deploy-spring-boot-experience-applications?scm=20140722.S_help@@%E6%96%87%E6%A1%A3@@2797582.S_RQW@ag0+BB2@ag0+BB1@ag0.ID_2797582-RL_Springboot-LOC_search~UND~helpdoc~UND~item-OR_ser-V_4-P0_27&source=5176.29345612&userCode=ywqc0ubl)

## [#](#日志框架的基础) 日志框架的基础

在学习这块时需要一些日志框架的发展和基础，同时了解日志配置时考虑的因素。

### [#](#关于日志框架-日志门面) 关于日志框架（日志门面）

> Java日志库是最能体现Java库在进化中的渊源关系的，在理解时重点理解**日志框架本身**和**日志门面**，以及比较好的实践等。要关注其历史渊源和设计（比如桥接），而具体在使用时查询接口即可， 否则会陷入JUL(Java Util Log), JCL(Commons Logging), Log4j, SLF4J, Logback，Log4j2傻傻分不清楚的境地。

关于日志框架（日志门面）这篇文章有过详细的介绍。

[常用开发库 - 日志类库详解]()

### [#](#配置时考虑点) 配置时考虑点

> 在配置日志时需要考虑哪些因素？

- 支持日志路径，日志level等配置
- 日志控制配置通过application.yml下发
- 按天生成日志，当天的日志>50MB回滚
- 最多保存10天日志
- 生成的日志中Pattern自定义
- Pattern中添加用户自定义的MDC字段，比如用户信息(当前日志是由哪个用户的请求产生)，request信息。此种方式可以通过AOP切面控制，在MDC中添加requestID，在spring-logback.xml中配置Pattern。
- 根据不同的运行环境设置Profile - dev，test，product
- 对控制台，Err和全量日志分别配置
- 对第三方包路径日志控制

## [#](#实现范例) 实现范例

> 如下两个例子基本包含了上述的考虑点:

### [#](#综合范例) 综合范例

- application.yml

```json
logging:
  level:
    root: debug
  path: C:/data/logs/springboot-logback-demo
server:
  port: 8080
spring:
  application:
    name: springboot-logback-demo
debug: false
```

- Spring-logback.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>

    <!-- 日志根目录-->
    <springProperty scope="context" name="LOG_HOME" source="logging.path" defaultValue="/data/logs/springboot-logback-demo"/>

    <!-- 日志级别 -->
    <springProperty scope="context" name="LOG_ROOT_LEVEL" source="logging.level.root" defaultValue="DEBUG"/>

    <!--  标识这个"STDOUT" 将会添加到这个logger -->
    <springProperty scope="context" name="STDOUT" source="log.stdout" defaultValue="STDOUT"/>

    <!-- 日志文件名称-->
    <property name="LOG_PREFIX" value="spring-boot-logback" />

    <!-- 日志文件编码-->
    <property name="LOG_CHARSET" value="UTF-8" />

    <!-- 日志文件路径+日期-->
    <property name="LOG_DIR" value="${LOG_HOME}/%d{yyyyMMdd}" />

    <!--对日志进行格式化-->
    <property name="LOG_MSG" value="- | [%X{requestUUID}] | [%d{yyyyMMdd HH:mm:ss.SSS}] | [%level] | [${HOSTNAME}] | [%thread] | [%logger{36}] | --> %msg|%n "/>

    <!--文件大小，默认10MB-->
    <property name="MAX_FILE_SIZE" value="50MB" />

    <!-- 配置日志的滚动时间 ，表示只保留最近 10 天的日志-->
    <property name="MAX_HISTORY" value="10"/>

    <!--输出到控制台-->
    <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
        <!-- 输出的日志内容格式化-->
        <layout class="ch.qos.logback.classic.PatternLayout">
            <pattern>${LOG_MSG}</pattern>
        </layout>
    </appender>

    <!--输出到文件-->
    <appender name="0" class="ch.qos.logback.core.rolling.RollingFileAppender">
    </appender>

    <!-- 定义 ALL 日志的输出方式:-->
    <appender name="FILE_ALL" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <!--日志文件路径，日志文件名称-->
        <File>${LOG_HOME}/all_${LOG_PREFIX}.log</File>

        <!-- 设置滚动策略，当天的日志大小超过 ${MAX_FILE_SIZE} 文件大小时候，新的内容写入新的文件， 默认10MB -->
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">

            <!--日志文件路径，新的 ALL 日志文件名称，“ i ” 是个变量 -->
            <FileNamePattern>${LOG_DIR}/all_${LOG_PREFIX}%i.log</FileNamePattern>

            <!-- 配置日志的滚动时间 ，表示只保留最近 10 天的日志-->
            <MaxHistory>${MAX_HISTORY}</MaxHistory>

            <!--当天的日志大小超过 ${MAX_FILE_SIZE} 文件大小时候，新的内容写入新的文件， 默认10MB-->
            <timeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
                <maxFileSize>${MAX_FILE_SIZE}</maxFileSize>
            </timeBasedFileNamingAndTriggeringPolicy>

        </rollingPolicy>

        <!-- 输出的日志内容格式化-->
        <layout class="ch.qos.logback.classic.PatternLayout">
            <pattern>${LOG_MSG}</pattern>
        </layout>
    </appender>

    <!-- 定义 ERROR 日志的输出方式:-->
    <appender name="FILE_ERROR" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <!-- 下面为配置只输出error级别的日志 -->
        <filter class="ch.qos.logback.classic.filter.LevelFilter">
            <level>ERROR</level>
            <OnMismatch>DENY</OnMismatch>
            <OnMatch>ACCEPT</OnMatch>
        </filter>
        <!--日志文件路径，日志文件名称-->
        <File>${LOG_HOME}/err_${LOG_PREFIX}.log</File>

        <!-- 设置滚动策略，当天的日志大小超过 ${MAX_FILE_SIZE} 文件大小时候，新的内容写入新的文件， 默认10MB -->
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">

            <!--日志文件路径，新的 ERR 日志文件名称，“ i ” 是个变量 -->
            <FileNamePattern>${LOG_DIR}/err_${LOG_PREFIX}%i.log</FileNamePattern>

            <!-- 配置日志的滚动时间 ，表示只保留最近 10 天的日志-->
            <MaxHistory>${MAX_HISTORY}</MaxHistory>

            <!--当天的日志大小超过 ${MAX_FILE_SIZE} 文件大小时候，新的内容写入新的文件， 默认10MB-->
            <timeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
                <maxFileSize>${MAX_FILE_SIZE}</maxFileSize>
            </timeBasedFileNamingAndTriggeringPolicy>
        </rollingPolicy>

        <!-- 输出的日志内容格式化-->
        <layout class="ch.qos.logback.classic.PatternLayout">
            <Pattern>${LOG_MSG}</Pattern>
        </layout>
    </appender>

    <!-- additivity 设为false,则logger内容不附加至root ，配置以配置包下的所有类的日志的打印，级别是 ERROR-->
    <logger name="org.springframework"     level="ERROR" />
    <logger name="org.apache.commons"      level="ERROR" />
    <logger name="org.apache.zookeeper"    level="ERROR"  />
    <logger name="com.alibaba.dubbo.monitor" level="ERROR"/>
    <logger name="com.alibaba.dubbo.remoting" level="ERROR" />

    <!-- ${LOG_ROOT_LEVEL} 日志级别 -->
    <root level="${LOG_ROOT_LEVEL}">

        <!-- 标识这个"${STDOUT}"将会添加到这个logger -->
        <appender-ref ref="${STDOUT}"/>

        <!-- FILE_ALL 日志输出添加到 logger -->
        <appender-ref ref="FILE_ALL"/>

        <!-- FILE_ERROR 日志输出添加到 logger -->
        <appender-ref ref="FILE_ERROR"/>
    </root>

</configuration>
```

Profile 相关的配置可以参考:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <include resource="org/springframework/boot/logging/logback/base.xml" />
    
     <!-- roll by day -->
     <appender name="FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">   
    	<rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">   
      		<fileNamePattern>logs/springboot-logback-demo.%d{yyyy-MM-dd}.log</fileNamePattern>   
      		<maxHistory>30</maxHistory>  
    	</rollingPolicy>   
    	<encoder>   
      		<pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} [%thread] %-5level %logger{35} - %msg%n</pattern>   
    	</encoder>  
  	</appender> 
   
    <!-- dev -->
	<logger name="org.springframework.web" level="INFO"/>
		<root level="INFO">
		<appender-ref ref="FILE" />
	</root>

    <!-- test or production -->
    <springProfile name="test,prod">
        <logger name="org.springframework.web" level="INFO"/>
        <logger name="com.pdai.springboot" level="INFO"/>
        <root level="INFO">
        	<appender-ref ref="FILE" />
        </root>
    </springProfile>
  	 
</configuration>
```

### [#](#在配置前可以参考如下文章) 在配置前可以参考如下文章

https://www.cnblogs.com/warking/p/5710303.html

## [#](#參考文档) 參考文档

- Logback官网

https://logback.qos.ch/manual/layouts.html#conversionWord

- Logback官网 文档

https://logback.qos.ch/manual/index.html

- Logback中Encoder Pattern

```xml
<encoder>
	<pattern>%d{HH:mm:ss} [%thread][%X{traceId}] %-5level %logger{36} - %msg%n</pattern>
</encoder>
```

https://logback.qos.ch/manual/layouts.html#conversionWord



作为一名多年开发经验的老鸟，平时抽空收集了各种优质的技术教程，涉及前后端和移动端。包含各种编程语言，有兴趣Q的可以抽空学习起来：[全栈工程师必读技术教程](https://nav.vpssw.com/favorites/technical-information)   毕竟在这个竞争激烈的时代，多学一点，多一份技能傍身总是有好处的。