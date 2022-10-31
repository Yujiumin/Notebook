logback-spring.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<configuration xmlns="http://ch.qos.logback/xml/ns/logback"
               xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
               xsi:schemaLocation="http://ch.qos.logback/xml/ns/logback
                https://raw.githubusercontent.com/enricopulatzo/logback-XSD/master/src/main/xsd/logback.xsd">

    <property name="LOG_HOMEDIR" value="/var/log"/>
    <property name="LOG_PATTERN" value="%d{yyyy-MM-dd HH:mm:ss.SSS} %-5level [%15thread] %logger{40} : %msg%n"/>

    <!--  控制台输出  -->
    <appender name="Console" class="ch.qos.logback.core.ConsoleAppender">
        <encoder>
            <charset>UTF-8</charset>
            <pattern>${LOG_PATTERN}</pattern>
        </encoder>
    </appender>

    <!--  INFO级日志输出文件  -->
    <appender name="InfoLogFile" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <filter class="ch.qos.logback.classic.filter.LevelFilter">
            <level>INFO</level>
            <onMatch>ACCEPT</onMatch>
            <onMismatch>DENY</onMismatch>
        </filter>
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <fileNamePattern>${LOG_HOMEDIR}/info/%d.log</fileNamePattern>
            <maxHistory>180</maxHistory>
        </rollingPolicy>
        <encoder>
            <charset>UTF-8</charset>
            <pattern>${LOG_PATTERN}</pattern>
        </encoder>
    </appender>

    <!--  ERROR级日志输出文件  -->
    <appender name="ErrorLogFile" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <filter class="ch.qos.logback.classic.filter.LevelFilter">
            <level>ERROR</level>
            <onMatch>ACCEPT</onMatch>
            <onMismatch>DENY</onMismatch>
        </filter>
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <fileNamePattern>${LOG_HOMEDIR}/error/%d.log</fileNamePattern>
            <maxHistory>30</maxHistory>
        </rollingPolicy>
        <encoder>
            <charset>UTF-8</charset>
            <pattern>${LOG_PATTERN}</pattern>
        </encoder>
    </appender>

    <root level="INFO">
        <appender-ref ref="Console"/>
        <appender-ref ref="InfoLogFile"/>
        <appender-ref ref="ErrorLogFile"/>
    </root>
</configuration>
```

