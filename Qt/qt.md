## Qt

- [Set environment variable](#set-environment-variable)
- [Gather diagnostic information](#gather-diagnostic-information)
- [Snippets](#snippets)
  + [Sleep](#sleep)

### Set environment variable

``` bash
qputenv("QT_QPA_EGLFS_PHYSICAL_WIDTH", "1920");
```

### Gather diagnostic information

General information about your platfom:

``` bash
/path/to/qt/5.11.1/clang_64/bin/qtdiag
```

For graphics related stuff set `QSG_INFO=1` environment variable and watch the application output:

``` bash
qputenv("QSG_INFO", "1”);
```

You can also visualize your scene graph by setting:

``` bash
qputenv("QSG_VISUALIZE", "overdraw");
```

### Snippets

#### Sleep

``` cpp
QTime dieTime = QTime::currentTime().addSecs(5); // sleep for 5 seconds
while (QTime::currentTime() < dieTime)
{ QCoreApplication::processEvents(QEventLoop::AllEvents, 100);}
```
