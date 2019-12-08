### 如果不需要打包,只需要使用辅助类启动即可,也可以使用mvn javafx：run启动
```java
public class FXLauncher {

    public static void main(String[] args) {
        MainFX.main(args);
    }
}
```

### 如果需要打包，在pom引入打包插件，执行mvn clean install即可
```xml
<!--注意辅助启动类Launcher和FX application配置的位置-->
<!--必须引入第二个插件maven-shade-plugin，否则打包之后的jar是会报错找不到主清单的-->
<!--可以不引入maven的打包插件是因为在openjfx的插件里面就包含了maven插件，但是需要指定版本，详见pom文件-->
  <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <release>${maven.compiler.release}</release>
                </configuration>
            </plugin>

             <plugin>
                 <groupId>org.openjfx</groupId>
                 <artifactId>javafx-maven-plugin</artifactId>
                 <version>0.0.3</version>
                 <configuration>
                     <mainClass>com.swust.MainFX</mainClass>
                 </configuration>
             </plugin>
             <plugin>
                 <groupId>org.apache.maven.plugins</groupId>
                 <artifactId>maven-shade-plugin</artifactId>
                 <version>2.4.1</version>
                 <executions>
                     <execution>
                         <phase>package</phase>
                         <goals>
                             <goal>shade</goal>
                         </goals>
                         <configuration>
                             <transformers>
                                 <transformer
                                         implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
                                     <mainClass>com.swust.FXLauncher</mainClass>
                                 </transformer>
                             </transformers>
                         </configuration>
                     </execution>
                 </executions>
             </plugin>
         </plugins>
```