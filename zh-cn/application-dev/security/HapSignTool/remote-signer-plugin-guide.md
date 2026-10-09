# HAP签名工具远程签名插件开发指南

<!--Kit: Common-->
<!--Subsystem: Security-->
<!--Owner: @scuteehuangjun-->
<!--Designer: @scuteehuangjun; @liuchibin-->
<!--Tester: @wwrongs-->
<!--Adviser: @zengyawen-->

## 远程签名插件简介

HAP签名工具支持本地签名和远程签名两种模式。

**本地签名模式**：签名密钥存储在本地KeyStore文件中，开发者可以直接使用。但在企业级应用开发中，通常需要更严格的密钥管理策略，例如：企业希望统一管理所有应用的签名密钥，避免密钥分散在各个开发者的计算机上，造成安全风险。

**远程签名模式**：通过实现`ISigner`接口的Java插件，将签名请求发送到远程签名服务。私钥存储在远程服务的HSM（硬件安全模块）中，由远程服务完成实际签名操作。这样既保持了HAP签名工具的使用习惯，又实现了密钥的集中管理和安全保护。

## 基本概念

在使用远程签名插件前，开发者应了解以下基本概念：

- **[ISigner接口](#签名接口)**
  
  所有远程签名插件必须实现的接口，定义了签名操作的核心方法。插件通过实现这个接口，将自定义的签名逻辑集成到HAP签名工具中。

- **插件JAR**
  
  打包好的插件文件，包含插件实现类和配置文件。HAP签名工具通过类加载器动态加载JAR文件中的类。

- **signer.properties**
  
  插件的配置文件，必须位于JAR文件的根目录。配置文件中定义了接口与实现类的映射关系。

## 实现原理

**远程签名插件工作流程**

当HAP签名工具检测到`mode`参数值为`remoteSign`，且指定了`signerPlugin`参数时，会触发插件加载流程。

1. **类加载器创建**：使用`URLClassLoader`创建插件JAR的类加载器，父类加载器为HAP签名工具的类加载器。
2. **读取配置文件**：从类加载器读取`signer.properties`配置文件，获取接口与实现类的映射关系。
3. **类加载与实例化**：通过反射加载插件实现类，并调用接收`Map<String, Object>`参数的构造函数创建实例。
4. **接口验证**：验证创建的对象是否实现了`ISigner`接口，确保插件的有效性。
5. **签名调用**：调用插件的签名方法执行签名操作。

## 约束与限制

- 远程签名插件仅支持`remoteSign`模式，不支持`localSign`模式。
- 插件必须实现`ISigner`接口的所有方法，实现类必须有`public`修饰符。
- 插件JAR必须包含`signer.properties`配置文件。

## 接口说明

### 签名接口

```java
package com.ohos.hapsigntool.signer;

import java.security.cert.X509CRL;
import java.security.cert.X509Certificate;
import java.security.spec.AlgorithmParameterSpec;
import java.util.List;

/**
 * 签名器接口
 * 所有远程签名插件必须实现此接口
 */
public interface ISigner {
    /**
     * 执行签名操作
     *
     * @param data          待签名的数据
     * @param signAlg       签名算法（如 "SHA256withECDSA"）
     * @param parameterSpec 算法参数（通常为null）
     * @return 签名后的字节数组
     */
    byte[] getSignature(byte[] data, String signAlg, AlgorithmParameterSpec parameterSpec);

    /**
     * 获取证书吊销列表
     *
     * @return CRL列表
     */
    List<X509CRL> getCrls();

    /**
     * 获取证书链
     *
     * @return 证书链
     */
    List<X509Certificate> getCertificates();
}
```

## 环境准备

| 组件        | 版本要求    | 用途             |
| ----------- | ----------- | ---------------- |
| JDK         | 1.8+       | Java开发环境     |
| Maven       | 3.6+        | 项目构建工具     |
| HAP签名工具  | 4.0.0+      | 插件加载和签名测试 |

**获取HAP签名工具**

- [签名工具仓库下载](https://gitcode.com/openharmony/developtools_hapsigner/blob/master/dist/hap-sign-tool.jar)。
- 通过SDK获取，签名工具路径：`${SDK安装目录}/toolchains/lib/hap-sign-tool.jar`。

## 开发步骤

1. 创建插件项目。

    创建Maven项目，包含以下目录结构：

    ```log
    my-remote-signer-plugin/
    ├── pom.xml
    ├── lib
    |   └── hap-sign-tool.jar
    └── src/
        └── main/
            ├── java/
            │   └── com/
            │       └── example/
            │           └── MyRemoteSigner.java
            └── resources/
                └── signer.properties
    ```

2. 配置pom.xml。

    在pom.xml中添加HAP签名工具库依赖和相关依赖：

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0"
             xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    
        <modelVersion>4.0.0</modelVersion>
        
        <groupId>com.example</groupId>
        <artifactId>my-remote-signer-plugin</artifactId>
        <version>1.0.0</version>
        <packaging>jar</packaging>
        
        <properties>
            <maven.compiler.source>1.8</maven.compiler.source>
            <maven.compiler.target>1.8</maven.compiler.target>
            <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        </properties>
        
        <dependencies>
            <dependency>
                <groupId>com.ohos</groupId>
                <artifactId>hap-sign-tool</artifactId>
                <version>4.0</version>
                <scope>system</scope>
                <systemPath>${project.basedir}/lib/hap-sign-tool.jar</systemPath>
            </dependency>
        </dependencies>
    </project>
    ```

3. 创建signer.properties配置文件。

    在`src/main/resources/`目录下创建`signer.properties`文件：

    ```properties
    com.ohos.hapsigntool.signer.ISigner=com.example.MyRemoteSigner
    ```

4. 实现ISigner接口。

    创建`MyRemoteSigner.java`类，实现`ISigner`接口：

    ```java
    package com.example;

    import com.ohos.hapsigntool.error.CustomException;
    import com.ohos.hapsigntool.error.ERROR;
    import com.ohos.hapsigntool.signer.ISigner;

    import java.security.cert.X509CRL;
    import java.security.cert.X509Certificate;
    import java.security.spec.AlgorithmParameterSpec;
    import java.util.Collections;
    import java.util.List;
    import java.util.Map;

    public class MyRemoteSigner implements ISigner {
        private final Map<String, Object> params;

        public MyRemoteSigner(Map<String, Object> params) {
            this.params = params;
        }

        @Override
        public byte[] getSignature(byte[] data, String signAlg, AlgorithmParameterSpec parameterSpec) {
            try {
                // 获取命令行参数keyAlias
                String keyAlias = String.valueOf(params.get("keyAlias"));
                // 此处可以将待签名数据和签名算法等发送给服务器，在签名服务器使用证书对应的私钥进行签名，并返回签名结果。
                byte[] signature = new byte[0];
                return signature;
            } catch (Exception e) {
                // 签名失败，抛出异常，HAP签名工具会捕获此异常，中断签名流程。
                CustomException.throwException(ERROR.SIGN_ERROR, "remote sign failed, msg: " + e.getMessage());
                return null;
            }
        }

        @Override
        public List<X509CRL> getCrls() {
            return Collections.emptyList();
        }

        @Override
        public List<X509Certificate> getCertificates() {
            return Collections.emptyList();
        }
    }
    ```

5. 打包插件JAR。

    使用Maven打包插件：

    ```bash
    mvn clean package
    ```

    打包成功后，在`target/`目录下生成插件JAR文件。

## 插件用法

1. 使用插件。

    ```shell
    java -jar hap-sign-tool.jar sign-app \
        -mode remoteSign \
        -keyAlias remoteKeyAlias \
        -signerPlugin my-remote-signer-plugin-1.0.0.jar \
        -inFile input.hap \
        -outFile output.hap \
        -appCertFile app-cert-chain.cer \
        -profileFile provision-profile.p7b \
        -signAlg SHA256withECDSA
    ```

2. 参数说明。

    | 参数名 | 参数说明 |
    | --- | --- |
    | -mode | 签名模式，可选以下值：<br>localSign为本地签名模式。<br>remoteSign为远程签名模式。 |
    | -keyAlias | 签名使用的密钥别名。 |
    | -profileFile | 签名证书对应的profile文件路径，支持绝对路径和相对路径。 |
    | -appCertFile | 签名证书文件路径，支持绝对路径和相对路径。 |
    | -inFile | 待签名的HAP包文件路径，支持绝对路径和相对路径。 |
    | -outFile | 签名后的HAP包文件路径，支持绝对路径和相对路径。 |
    | -signAlg | 签名算法，支持的签名算法：SHA256withECDSA、SHA384withECDSA。 |
    | -signerPlugin | remoteSign插件路径，支持绝对路径和相对路径。 |

## 常见问题

### 插件无法加载

**问题现象**

```text
[WARN] lost parameter signerPlugin
[WARN] can not find signerPlugin or not a file by param signerPlugin = xxx.jar
```

**可能原因**

1. 未指定`-signerPlugin`参数。
2. 插件JAR文件不存在。

**解决措施**

1. 确保传入正确的`-signerPlugin`参数。
2. 确认JAR文件存在。

### 找不到signer.properties

**问题现象**

```text
[WARN] can not find entry signer.properties in xxx.jar
```

**可能原因**

`signer.properties`不在JAR根目录。

**解决措施**

确认`signer.properties`在JAR根目录，验证方法：`jar tf plugin.jar`，查看JAR文件条目，确保条目中包含`signer.properties`。

### 类加载失败

**问题现象**

```text
[WARN] load remote signer from xxx.jar failed, msg: ClassNotFoundException
```

**可能原因**

1. `signer.properties`中的类名错误。
2. 类缺少`public`修饰符。
3. 构造函数签名不匹配。

**解决措施**

1. 检查`signer.properties`中的类名是否正确。
2. 确认类有`public`修饰符。
3. 确认类有接收`Map<String, Object>`的构造函数。