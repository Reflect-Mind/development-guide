# 基于JavaFX Maven Plugin插件JavaFx程序打包

--- 
JavaFx Maven Plugin为JavaFx应用程序提供了一个集成的打包方式。

此插件本质上是原生JavaFx提供的打包方式的一种封装，以简化使用。更多的有关于此插件的更多的使用方法请参考[Whttps://github.com/javafx-maven-plugin/javafx-maven-plugin](https://github.com/javafx-maven-plugin/javafx-maven-plugin)。本教程将简单介绍使用该插件来把我们的ReflectMind打包成exe程序

## 软件需求

* Maven 3.5+
* JDK1.8.40+

## 应具备的知识

在继续学习该教程前，请确保Java和Maven运行环境正确配置，同时需要对Maven知识有基本的了解，如果尚未掌握Maven基础知识，请访问[Maven教程](https://www.yiibai.com/maven/)进行学习

## 基本配置

在ReflectMind程序的pom.xml文件中，已添加以下配置

```
<plugin>
    <groupId>com.zenjava</groupId>
    <artifactId>javafx-maven-plugin</artifactId>
    <version>8.8.3</version>
    <configuration>
        <mainClass>cn.lingnan.edu.Main</mainClass>
    </configuration>
</plugin>
```
其中mainClass标签体指定ReflectMind程序的入口

## 运行方式

* 命令行
> 在命令行中，进入该工程的根目录，编写命令**mvn jfx:native**并回车即可。

运行完成后，exe程序在文件夹**target/jfx/native**中，由于本项目中的数据库文件并未在打包后的程序中，如果使用64位版的JDK进行打包，为确保程序正常运行，我们将本项目根目录的数据库文件**psychovocab.db**复制粘贴到exe文件所在文件夹中，如使用32位版的JDK进行打包，则将该数据库文件放置于exe文件夹下的的app文件夹中

## 可能遇到的问题

* 测试用例编译不通过导致插件运行失败
> 解决方法：在该命令后添加 **-Dmaven.test.skip=true**运行，跳过测试用例的编译和执行。
