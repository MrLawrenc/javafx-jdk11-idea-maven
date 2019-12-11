### 将jar包打为exe可执行文件（仅限于没有fmxl等资源情况）

- 使用exe4j打包，可以官网下载，也可以使用exe4j文件下的安装程序，安装激活之后打开程序

- 选择open，选择附带的jfx11.exe4j文件，即可导入配置

- 选择第五步Java invocation更改jar包位置为自己的jar包路径(有边有编辑按钮)
- 更新下面的mainClass为自己的辅助Launcher类

- 之后将jre放在桌面，随后点击finish即可在桌面生成exe文件

- jre和exe文件只要在同一目录，就可以在任何没有java环境的电脑运行

### 如果包含资源文件(仅限本机，jre11打进去加载资源文件会报错，暂时还未解决，java8可以打入jre可以正常使用)
- 请不要将jre和生成的exe文件放在中文目录或者是不规范的目录下，否则将会在启动的时候读取资源文件失败
- 在桌面报错的原因，先检查用户目录是否包含空格
- 建议目录最好全为英文，无空格，无中文相关符号
- 比如读取resource文件夹下的资源文件，如fxml,可以采用如下方式:
```java
FXMLLoader fxmlLoader = new FXMLLoader(getClass().getResource("/Mars.fxml"));
Parent root = fxmlLoader.load();
```
### exe4j自定义配置
- 以上只是简化初学者的配置，如果想自定义生成的exe文件(比如文件名，图标等)，那么可以自己跟着exe4j的配置走即可


### 使用java的模块化jlink打包，大致步骤如下(还未实践，周末空了做)
- 新建module-info.java将项目模块化
- 添加所需要的模块
- 可以使用jlink的maven插件，也可以手动制作jmod，之后使用jlink打包

### 如果打包之后启动exe文件失败报错
- 先使用java -jar 名字.jar  启动看看是否报错
- 如果不报错请仔细检查exe4j配置和文件目录等信息
- 根据生成的exe文件日志查看错误原因，根据报错代码行进一步查找原因
- 在exe4j生成exe文件的时候可以配置日志，具体在 Executable->Redirectionp里面，可以配置error.log和output.log生成方式
- 查看是否因为exe4j版本造成的，我自己试了6.0版本会报错，打印日志发现资源文件都是从c盘的用户目录寻找，但是5.0版本可以正常使用
- scenebuilder和jcpicker是jfx开发相关工具，后者是一款取色器，配合使用比较方便
