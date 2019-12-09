### idea+jdk11+jfx
clone之后可以直接在idea运行
- 不需要打包
执行辅助类Launcher即可

- 需要打包
加入打包插件，执行maven的打包命令即可

### 打包为exe文件
- exe目录下包含所需要的打包软件及配置
- exe下还包含jfx相关开发工具
### 附
- 使用jlink获取jdk11的jre
```cmd
Step1:用管理员身份打开cmp 

Step2:进入jdk/bin，（我的路径是：C:\Program Files\Java\jdk-11.0.2\bin）

Step3:输入jlink.exe --module-path jmods --add-modules java.desktop --output jre
```
- jfx的官网地址https://openjfx.io/  （国内可能略慢，上面有jfx的sdk和doc）