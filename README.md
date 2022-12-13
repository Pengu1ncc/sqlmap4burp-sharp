# sqlmap4burp#
## 0x01 插件简介
sqlmap4burp#是在[sqlmap4burp++](https://github.com/c0ny1/sqlmap4burp-plus-plus)的基础上进行优化，拥有原项目可以实现跨平台联动Burpsuite与sqlmap的优点，新增加了在macOS上对于iTerm2的支持。

![优化ui](https://github.com/Pengu1ncc/sqlmap4burp-sharp/blob/main/img/sqlmap4burp%23ui.png)

## 0x02 插件编译

```
mvn package
```

## 0x03 插件优化

在sqlmap4burp++作者的开发思路上，增加了以下代码，以实现插件支持ITerm2

```java
cmds.add("osascript");
cmds.add("-e");
String cmd = "tell application \"iTerm\" \n" +
"create window with default profile\n" +
"tell current session of current window to write text \"%s\"\n" +
"end tell";
cmds.add(String.format(cmd, command));
```

在开发过程中，原目的是想实现对macOS上多种终端工具的支持，但在测试中发现大多数的终端工具都不支持`AppleScript`语法，如果大家有更好的实现方法，欢迎提交建议，我会更新插件。

## 0x04 插件使用

在Burpsuite的Extender模块中导入jar即可，详细使用方法可以参考[sqlmap4burp++](https://github.com/c0ny1/sqlmap4burp-plus-plus)的说明文档。

## 0x05 参考项目
* https://github.com/c0ny1/sqlmap4burp-plus-plus
