This is a simple [Logback](http://logback.qos.ch/) appender which pushes logs to [MsTeams](https://products.office.com/en-us/microsoft-teams/group-chat-software) channel.

# How to setup

Add MsTeamsAppender configuration to logback.xml file

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<configuration>
  ...

  <appender name="MSTEAMS" class="de.smartthingssimple.basar.logback.MsTeamsAppender">
    <appName>AppName</appName>
    <webhookUri>your web hook from ms teams</webhookUri>
  </appender>
  
  <appender name="ASYNC_MSTEAMS" class="ch.qos.logback.classic.AsyncAppender">
    <appender-ref ref="MSTEAMS" />
    <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
      <level>WARN</level>
    </filter>
  </appender>

  <root level="INFO">
    <appender-ref ref="ASYNC_MSTEAMS" />
  </root>

</configuration>
```
