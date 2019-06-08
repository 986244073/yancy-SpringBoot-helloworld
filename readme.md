# SpringBoot HelloWorld

## 新建一个项目

在POM中加入

```xml
  <!-- web依赖-->
<dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
<!--启动依赖-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    <!--热更新依赖-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <version>2.1.5.RELEASE</version>
            <optional>true</optional>
        </dependency>
    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <!--设置热更新-->
                <configuration>
                    <fork>true</fork>
                </configuration>
            </plugin>
        </plugins>
    </build>

```

在目录 src\main\java\com\yancy\helloworld\web 下创建 HelloController： 

```java
//Json 输出
@RestController
public class HelloWorldController {
// 匹配路径
    @RequestMapping("/")
    public String sayHello(String name) {
        return "Hello,world!"+name;
    }
}
```

在设置里面开启热更新 

> 选择 File | Settings | Compiler 命令，然后勾选 Build project automatically 复选框 
>
> 

> 使⽤用快捷键 Ctrl + Shift + A，在输⼊入框中输⼊入 Registry，勾选 compile.automake.allow.when.app.running 复
> 选框 

debug 启动 ,可以访问`http://localhost:8080/?name=张三`