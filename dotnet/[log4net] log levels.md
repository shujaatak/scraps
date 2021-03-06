# Setting log level in log4net

That's the log levels matrix. You should read it by columns - each column represents a log level and messages included there. For example, `ERROR` log level has only `ERROR` and `FATAL` messages.

|  ALL  | DEBUG |  INFO |  WARN | ERROR | FATAL |
|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
|  ALL  |       |       |       |       |       |
| DEBUG | DEBUG |       |       |       |       |
|  INFO |  INFO |  INFO |       |       |       |
|  WARN |  WARN |  WARN |  WARN |       |       |
| ERROR | ERROR | ERROR | ERROR | ERROR |       |
| FATAL | FATAL | FATAL | FATAL | FATAL | FATAL |

For example, if we want to log only messages with level `WARN` and below (skipping `DEBUG` and `INFO`), then we should do like this:

``` html
<param name="LevelMin" value="WARN"/>
```

Here's the full config:

``` html
<?xml version="1.0" encoding="utf-8" ?>
<log4net>
  <appender name="RollingFile" type="log4net.Appender.FileAppender">
    <file value="some.log" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%-5p [%d{yyyy-MM-dd HH:mm:ss}] %message%newline" />
    </layout>
    <filter type="log4net.Filter.LevelRangeFilter">
        <param name="LevelMin" value="WARN"/>
    </filter>
  </appender>
   <root>
    <level value="ALL" />
    <appender-ref ref="RollingFile" />
  </root>
</log4net>
```
