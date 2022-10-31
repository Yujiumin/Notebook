logback-spring.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<configuration debug="false" xmlns="http://ch.qos.logback/xml/ns/logback"
               xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
               xsi:schemaLocation="http://ch.qos.logback/xml/ns/logback
               https://raw.githubusercontent.com/enricopulatzo/logback-XSD/master/src/main/xsd/logback.xsd">
    
    <property name="log.dir" value="/var/log"/>
    <property name="log.pattern" value="%d{yyyy-MM-dd HH:mm:ss.SSS} %-5level --- [%thread] %logger{40} : %msg%n"/>

    <appender name="CONSOLE_LOG" class="ch.qos.logback.core.ConsoleAppender">
        <encoder>
            <charset>UTF-8</charset>
            <pattern>${log.pattern}</pattern>
        </encoder>
    </appender>

    <appender name="INFO_LOG_FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <filter class="ch.qos.logback.classic.filter.LevelFilter">
            <level>INFO</level>
            <onMatch>ACCEPT</onMatch>
            <onMismatch>DENY</onMismatch>
        </filter>
        <encoder>
            <charset>UTF-8</charset>
            <pattern>${log.pattern}</pattern>
        </encoder>
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <fileNamePattern>${log.dir}/info/%d{yyyy-MM-dd}.log</fileNamePattern>
            <maxHistory>180</maxHistory>
        </rollingPolicy>
    </appender>

    <appender name="ERROR_LOG_FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
            <level>ERROR</level>
        </filter>
        <encoder>
            <charset>UTF-8</charset>
            <pattern>${log.pattern}</pattern>
        </encoder>
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <fileNamePattern>${log.dir}/error/%d{yyyy-MM-dd}.log</fileNamePattern>
            <maxHistory>30</maxHistory>
        </rollingPolicy>
    </appender>

    <root level="INFO">
        <appender-ref ref="CONSOLE_LOG"/>
        <appender-ref ref="INFO_LOG_FILE"/>
        <appender-ref ref="ERROR_LOG_FILE"/>
    </root>
</configuration>
```

