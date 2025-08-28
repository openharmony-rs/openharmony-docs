# 打包工具
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @lixueqing513-->

打包工具用于在程序编译完成后，对编译出的文件等进行打包，以供安装发布。开发者可以使用DevEco Studio进行打包，也可使用打包工具的JAR包进行打包，JAR包通常存放在SDK路径下的toolchains目录中。

打包工具支持生成：Ability类型的模块包（HAP）、动态共享包（HSP）、应用程序包（App）、快速修复模块包（HQF）、快速修复包（APPQF）。

打包指令中的文件来源于[DevEco Studio编译构建产物](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-compile-build)，文件路径查看操作如下。<br/>
1. 在DevEco Studio工程根目录下的/hvigor/hvigor-config.json5文件中，修改"logging"下的"level"字段为"debug"。<br/>
2. 在DevEco Studio菜单栏，依次选择"构建 -> 清理项目"。<br/>
3. 在DevEco Studio菜单栏，依次选择"构建 -> 构建APP(s)"。<br/>
4. 在DevEco Studio底部"构建"窗口，搜索"app_packing_tool.jar"，确认打包参数中文件的路径。<br/>

打包工具会对module.json文件属性进行合法性校验。module.json文件是编译构建产物，其属性值在编译构建时自动生成，与配置文件中配置项对应关系如下。

**表1** module.json与配置文件属性的对照表

| module.json属性          | [module.json5](../quick-start/module-configuration-file.md#配置文件标签)配置项         | [app.json5](../quick-start/app-configuration-file.md#配置文件标签)配置项            | [工程级build-profile.json5](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-build-profile-app)配置项  |
| ------------------------ | ------------------------ | -------------------------- | --------------------------       |
| bundleName               | -                        | bundleName                 | -                                |
| bundleType               | -                        | bundleType                 | -                                |
| versionCode              | -                        | versionCode                | -                                |
| debug                    | -                        | debug                      | -                                |
| module/name              | module/name              | -                          | -                                |
| minCompatibleVersionCode | -                        | minCompatibleVersionCode   | -                                |
| minAPIVersion            | -                        | minAPIVersion              | compatibleSdkVersion             |
| targetAPIVersion         | -                        | targetAPIVersion           | targetSdkVersion或compileSdkVersion  <br/>说明：targetSdkVersion存在时，targetAPIVersion由targetSdkVersion决定；<br/>否则，targetAPIVersion由compileSdkVersion决定。               |

## 约束与限制

- 打包工具需要运行在Java8及其以上环境。
- 打包指令中参数和参数值需成对出现。例如，HAP打包指令中--resources-path \<path>，其中--resources-path为指令参数，path为参数值，两者需要同时出现。

## HAP打包指令

开发者可以使用打包工具的JAR包对模块进行打包，通过传入打包选项、文件路径，生成所需的HAP包。

**打包HAP时的压缩规则：**
- 应用配置compressNativeLibs为true时，会按照--compress-level设置的压缩等级对--lib-path指定目录下的文件进行压缩。
- 出于运行时性能等考量，--lib-path指定目录外的文件不会进行压缩。

示例：
- [Stage模型](../../application-dev/application-models/application-models.md#应用模型概况)示例：


    ```
    java -jar app_packing_tool.jar --mode hap --json-path <path> [--resources-path <path>] [--ets-path <path>] [--index-path <path>] [--pack-info-path <path>] [--lib-path <path>] --out-path <path> [--force true] [--compress-level 5] [--pkg-context-path <path>] [--hnp-path <path>]
    ```

- [FA模型](../../application-dev/application-models/application-models.md#应用模型概况)示例：


    ```
    java -jar app_packing_tool.jar --mode hap --json-path <path> [--maple-so-path <path>] [--profile-path <path>] [--maple-so-dir <path>] [--dex-path <path>] [--lib-path <path>] [--resources-path <path>] [--index-path <path>] --out-path <path> [--force true] [--compress-level 5]
    ```

**表2** HAP打包指令参数说明

| 指令             | 是否必选项 | 选项          | 描述                                                         | 备注            |
| ---------------- | ---------- | ------------- | ------------------------------------------------------------ | --------------- |
| --mode           | 是         | hap           | 打包类型。                                                   | NA              |
| --json-path      | 是         | NA            | .json文件路径。FA模型文件名必须为config.json；Stage模型文件名必须为module.json。 | NA              |
| --profile-path   | 否         | NA            | CAPABILITY.profile文件路径。                                 | NA              |
| --maple-so-path  | 否         | NA            | maple so文件输入路径，so文件路径，文件名必须以.so为后缀。如果是多个so需要用“，”分隔。 | NA              |
| --maple-so-dir   | 否         | NA            | maple so目录输入路径。                                       | NA              |
| --dex-path       | 否         | NA            | dex文件路径，文件名必须以.dex为后缀。如果是多个dex需要用“，”分隔。 <br/>dex文件路径也可以为目录。 | NA              |
| --lib-path       | 否         | NA            | lib库文件路径。                                              | NA              |
| --resources-path | 否         | NA            | resources资源包路径。                                        | NA              |
| --index-path     | 否         | NA            | .index文件路径，文件名必须为resources.index。                | NA              |
| --pack-info-path | 否         | NA            | pack.info文件路径，文件名必须为pack.info。                   | NA              |
| --rpcid-path     | 否         | NA            | rpcid.sc文件路径，文件名必须为rpcid.sc。                     | NA              |
| --js-path        | 否         | NA            | 存放js文件目录路径。                                         | 仅Stage模型生效。 |
| --ets-path       | 否         | NA            | 存放ets文件目录路径。                                        | 仅Stage模型生效。 |
| --out-path       | 是         | NA            | 目标文件路径，文件名必须以.hap为后缀。                       | NA              |
| --force          | 否         | true或者false | 默认值为false。如果为true，表示当目标文件存在时，强制删除。  | NA              |
| --an-path        | 否         | NA            | 存放[an文件](https://developer.huawei.com/consumer/cn/doc/harmonyos-faqs-V5/faqs-arkts-52-V5)的路径。| 仅stage模型生效。 |
| --ap-path        | 否         | NA            | 存放[ap文件](https://developer.huawei.com/consumer/cn/doc/harmonyos-faqs-V5/faqs-arkts-52-V5)的路径。| 仅stage模型生效。 |
| --dir-list       | 否         | NA            | 可指定目标文件夹列表，将其打入HAP包内。                      | NA              |
| --compress-level | 否         | number        | lib库下文件压缩等级，默认值1。可选等级1-9。在应用配置compressNativeLibs参数为true的情况下生效，数值越大压缩率越高、压缩速度越慢。 | NA  |
| --pkg-context-path      | 否         | NA            | 可指定语境信息表文件路径，文件名必须为pkgContextInfo.json。 | 仅Stage模型生效。              |
| --hnp-path | 否 | NA | 指定native软件包文件路径，将native软件包打入HAP包内。 | NA |

## HSP打包指令

HSP包实现了多个HAP对文件的共享，开发者可以使用打包工具的jar包对应用进行打包，通过传入打包选项、文件路径，生成所需的HSP包。

**打包HSP时的压缩规则：**
- 应用配置compressNativeLibs为true时，会按照--compress-level设置的压缩等级对--lib-path指定目录下的文件进行压缩。
- 出于运行时性能等考量，--lib-path指定目录外的文件不会进行压缩。

示例：
```
java -jar app_packing_tool.jar --mode hsp --json-path <path> [--resources-path <path>] [--ets-path <path>] [--index-path <path>] [--pack-info-path <path>] [--lib-path <path>] --out-path <path> [--force true] [--compress-level 5] [--pkg-context-path <path>]
```

**表3** HSP打包指令参数说明

| 指令             | 是否必选项 | 选项          | 描述                                                         |
| ---------------- | ---------- | ------------- | ------------------------------------------------------------ |
| --mode           | 是         | hsp           | 打包类型。                                                   |
| --json-path      | 是         | NA            | .json文件路径，文件名必须为module.json。                     |
| --profile-path   | 否         | NA            | CAPABILITY.profile文件路径。                                 |
| --dex-path       | 否         | NA            | 1. dex文件路径，文件名必须以.dex为后缀。如果是多个dex需要用“，”分隔。<br/>2. dex文件路径也可以为目录。 |
| --lib-path       | 否         | NA            | lib库文件路径。                                              |
| --resources-path | 否         | NA            | resources资源包路径。                                        |
| --index-path     | 否         | NA            | .index文件路径，文件名必须为resources.index。                |
| --pack-info-path | 否         | NA            | pack.info文件路径，文件名必须为pack.info。                   |
| --js-path        | 否         | NA            | 存放js文件目录路径。                                         |
| --ets-path       | 否         | NA            | 存放ets文件目录路径。                                        |
| --out-path       | 是         | NA            | 目标文件路径，文件名必须以.hsp为后缀。                       |
| --force          | 否         | true或者false | 默认值为false。如果为true，表示当目标文件存在时，强制删除。  |
| --compress-level | 否         | number        | lib库下文件压缩等级，默认值1。可选等级1-9。在应用配置compressNativeLibs参数为true的情况下生效，数值越大压缩率越高、压缩速度越慢。 |
| --pkg-context-path      | 否         | NA            | 可指定语境信息表文件路径，文件名必须为pkgContextInfo.json。 |

## App打包指令

开发者可以使用打包工具的jar包对应用进行打包，通过传入打包选项、文件路径，生成所需的App包。App包用于上架应用市场。

**表4** App打包合法性校验规则

| HAP/HSP的module.json中的被校验字段  | 校验规则                           |
| --------------------------------- | --------------------------------- |
| module下的name字段                | 要求所有HAP/HSP的name字段值均不相同。      |
| bundleName                       | 要求所有HAP/HSP的bundleName字段值均保持一致。  |
| bundleType                       | 要求所有HAP/HSP的bundleType字段值均保持一致。  |
| versionCode                      | 要求所有HAP/HSP的versionCode字段值均保持一致。 |
| debug                            | 要求所有HAP/HSP的debug字段值均保持一致。    |
| minAPIVersion                    | 要求所有HAP/HSP的minAPIVersion字段值均保持一致。    |
| minCompatibleVersionCode         | 从API version 16开始，要求所有HAP的minCompatibleVersionCode字段值均保持一致，且均不低于所有HSP对应字段的最大值。<br/>对于API version 15及之前版本，要求所有HAP/HSP的minCompatibleVersionCode字段值均保持一致。    |
| targetAPIVersion                 | 从API version 16开始，要求所有HAP的targetAPIVersion字段值均保持一致，且均不低于所有HSP对应字段的最大值。<br/>对于API version 15及之前版本，要求所有HAP/HSP的targetAPIVersion字段值均保持一致。    |
| versionName                | 从API version 12开始，不再对versionName校验。      |

> **说明：** 
>
> - module.json文件为DevEco Studio编译构建产物，其中的字段与配置文件的对应关系，请参考[表1 module.json与配置文件属性的对照表](packing-tool.md)。

**打包App时的压缩规则：** 打包App时，对release模式的HAP、HSP包会进行压缩，对debug模式的HAP、HSP包不会压缩。

> **说明：** 
> 
> 若HAP/HSP中已压缩的so文件，在打包APP时再次压缩，将不会有明显体积缩减。

示例：

```
java -jar app_packing_tool.jar --mode app [--hap-path <path>] [--hsp-path <path>] --out-path <path> [--signature-path <path>] [--certificate-path <path>] --pack-info-path <path> [--pack-res-path <path>] [--force true] [--encrypt-path <path>]
```

**表5** App打包指令参数说明

| 指令                 | 是否必选项 | 选项          | 描述                                                           |
|--------------------|-------|-------------|--------------------------------------------------------------|
| --mode             | 是     | app         | 多个HAP需满足HAP的合法性校验。                                           |
| --hap-path         | 否     | NA          | HAP包文件路径，文件名必须以.hap为后缀。如果是多个HAP包需要用“,”分隔。<br/>HAP包文件路径也可以是目录。 |
| --hsp-path         | 否     | NA          | HSP包文件路径，文件名必须以.hsp为后缀。如果是多个HSP包需要用“,”分隔。<br/>HSP包文件路径也可以是目录。 |
| --pack-info-path   | 是     | NA          | 文件名必须为pack.info。                                             |
| --out-path         | 是     | NA          | 目标文件路径，文件名必须以.app为后缀。                                        |
| --signature-path   | 否     | NA          | 签名路径。                                                        |
| --certificate-path | 否     | NA          | 证书路径。                                                        |
| --pack-res-path    | 否     | NA          | pack.res快照文件路径。                                 |
| --force            | 否     | true或者false | 默认值为false。如果为true，表示当目标文件存在时，强制删除。                           |
| --encrypt-path     | 否     | NA          | 文件名必须为encrypt.json 。                           |



## 多工程打包指令

多工程打包适用于多个团队开发同一个应用，但不方便共享代码的情况。开发者通过传入已经打好的HAP、HSP和App包，将多个包打成一个最终的App包，并上架应用市场。

**表6** 多工程打包合法性校验规则

| HAP/HSP的module.json中的被校验字段  | 校验规则                           |
| --------------------------------- | --------------------------------- |
| module下的name字段                | 要求所有HAP/HSP的name字段值均不相同。      |
| bundleName                       | 要求所有HAP/HSP的bundleName字段值均保持一致。  |
| bundleType                       | 要求所有HAP/HSP的bundleType字段值均保持一致。  |
| versionCode                      | 要求所有HAP/HSP的versionCode字段值均保持一致。 |
| debug                            | 要求所有HAP/HSP的debug字段值均保持一致。    |
| minAPIVersion                    | 要求所有HAP/HSP的minAPIVersion字段值均保持一致。    |
| minCompatibleVersionCode         | 从API version 16开始，要求所有HAP的minCompatibleVersionCode字段值均保持一致，且均不低于所有HSP对应字段的最大值。<br/>对于API version 15及之前版本，要求所有HAP/HSP的minCompatibleVersionCode字段值均保持一致。    |
| targetAPIVersion                 | 从API version 16开始，要求所有HAP的targetAPIVersion字段值均保持一致，且均不低于所有HSP对应字段的最大值。<br/>对于API version 15及之前版本，要求所有HAP/HSP的targetAPIVersion字段值均保持一致。    |
| versionName                | 从API version 12开始，不再对versionName校验。      |

> **说明：** 
>
> - module.json文件为DevEco Studio编译构建产物，其中的字段与配置文件的对应关系，请参考[表1 module.json与配置文件属性的对照表](packing-tool.md)。

示例：

```
java -jar app_packing_tool.jar --mode multiApp [--hap-list <path>] [--hsp-list <path>] [--app-list <path>] --out-path <option> [--force true] [--encrypt-path <path>]
```

**表7** 多工程打包指令参数说明

| 指令         | 是否必选项 | 选项        | 描述                                                        |
|------------|-------|-----------|----------------------------------------------------------------|
| --mode     | 是     | multiApp  | 打包类型，在将多个HAP打入同一个App时，需保证每个HAP满足合法性校验规则。                                                            |
| --hap-list | 否     | HAP的路径    | HAP包文件路径，文件名必须以.hap为后缀。如果是多个HAP包需要“,”分隔。<br/>HAP文件路径也可以是目录。                                          |
| --hsp-list | 否     | HSP的路径    | HSP包文件路径，文件名必须以.hsp为后缀。如果是多个HSP包需要“,”分隔。<br/>HSP文件路径也可以是目录。                                          |
| --app-list | 否     | App的路径    | App文件路径，文件名必须以.app为后缀。如果是多个App包需要用“,”分隔。<br/>App文件路径也可以是目录。<br/>--hap-list，--hsp-list，--app-list不可以都不传。 |
| --out-path | 是     | NA | 目标文件路径，文件名必须以.app为后缀。 |
| --force    | 否     | true或者false | 默认值为false。如果为true，表示当目标文件存在时，强制删除。                                                                  |
| --encrypt-path | 否     | encrypt.json的路径 | 文件名必须为encrypt.json。                                                                  |



## HQF打包指令

HQF包适用于应用存在一些问题，需要紧急修复的场景。开发者可以使用打包工具的jar包对应用进行打包，通过传入打包选项、文件路径，生成所需的HQF包。

示例:

```
java -jar app_packing_tool.jar --mode hqf --json-path <path> [--lib-path <path>] [--ets-path <path>] [--resources-path <path>] --out-path <path> [--force true]
```

**表8** HQF打包指令参数说明

| 指令          | 是否必选项 | 选项          | 描述                                 |
|-------------|-------|-------------|------------------------------------|
| --mode      | 是     | hqf         | 打包类型。                              |
| --json-path | 是     | NA          | .json文件路径，文件名必须为[patch.json](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-incremental-debugging#section28031446182019)。        |
| --lib-path  | 否     | NA          | lib库文件的路径。                         |
| --ets-path  | 否     | NA          | 存放ets文件目录路径。                       |
| --resources-path  | 否     | NA          | resources资源包路径。                       |
| --out-path  | 是     | NA          | 目标文件路径，文件名必须以.hqf为后缀。              |
| --force     | 否     | true或者false | 默认值为false。如果为true，表示当目标文件存在时，强制删除。 |

## APPQF打包指令

APPQF包由一个或多个HQF文件组成。这些HQF包在应用市场会从APPQF包中拆分出来，再被分发到具体的设备上。开发者可以使用打包工具的jar包对应用进行打包，通过传入打包选项、文件路径，生成所需的APPQF包。

**APPQF打包合法性校验**
- 在打包生成APPQF包时，确保每个HQF的[patch.json文件](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-incremental-debugging#section28031446182019)中的versionName、versionCode、patchVersionName、patchVersionCode保持一致。
- 所有HQF不得重复。HQF重复是指同时满足以下两个条件：
	1. 两个HQF的patch.json文件中module下的name字段相同。
	2. 两个HQF的patch.json文件中module下的deviceTypes属性相交（至少存在一个相同的设备类型）。

示例:

```
java -jar app_packing_tool.jar --mode appqf --hqf-list <path> --out-path <path> [--force true]
```

**表9** APPQF打包指令参数说明

| 指令         | 是否必选项 | 选项          | 描述                                 |
|------------|-------|-------------|------------------------------------|
| --mode     | 是     | appqf       | 打包类型。                              |
| --hqf-list | 是     | NA          | [HQF文件](packing-tool.md#hqf打包指令)路径，多个HQF以英文逗号隔开。              |
| --out-path | 是     | NA          | 目标文件路径，文件名必须以.appqf为后缀。            |
| --force    | 否     | true或者false | 默认值为false。如果为true，表示当目标文件存在时，强制删除。 |

## 版本归一指令（versionNormalize）

同一个App中，所有HAP、HSP包的versionName和versionCode需要保持一致。当只有一个HAP或HSP需要修改升级时，可以调用此命令，将多个HAP、HSP的版本统一。本命令会修改所传入的HAP、HSP的版本号和版本名称，并在指定目录生成修改后的同名HAP、HSP，以及一个version_record.json文件，用于记录所有HAP、HSP原有的版本号、版本名称。

示例：
```
java -jar app_packing_tool.jar --mode versionNormalize --input-list 1.hap,2.hsp --version-code 1000001 --version-name 1.0.1 --out-path out
```

**表10** versionNormalize指令参数说明

| 指令             | 是否必选项 | 选项               | 描述                                                                |
|----------------|-------|------------------|-------------------------------------------------------------------|
| --mode         | 是     | versionNormalize | 命令类型。                                                             |
| --input-list   | 是     | HAP或HSP的路径       | 1. HAP或HSP包文件路径，文件名必须以.HAP或.HSP为后缀。如果是多个HAP或HSP包需要“,”分隔。<br/>2. 传入目录时，会读取目录下所有的HAP和HSP文件。 |
| --version-code | 是     | 版本号              | 指定的版本号，HAP、HSP的版本号会被修改为该版本。需要为整数，且不小于所有传入的HAP、HSP的版本号。            |
| --version-name | 是     | 版本名称             | 指定的版本名称，HAP、HSP的版本名称会被修改为该版本名称。                                    |
| --out-path     | 是     | NA               | 目标文件路径，需要为一个目录。                                                   |

## 包名归一指令（packageNormalize）

此命令可以修改传入的HSP的包名和版本号，并在指定目录生成修改后的同名HSP。

示例：
```
java -jar app_packing_tool.jar --mode packageNormalize --hsp-list 1.hsp,2.hsp --bundle-name com.example.myapplication --version-code 1000001 --out-path out
```

**表11**  参数含义及规范

| 指令             | 是否必选项 | 选项            | 描述                                                  |
|----------------|-------|---------------|-----------------------------------------------------|
| --mode         | 是     | packageNormalize | 命令类型。                                               |
| --hsp-list     | 是     | HSP的路径      | 1. HSP包文件路径，文件名必须以.hsp为后缀。如果是多个HSP包需要“,”分隔。<br/>2. HSP包目录。仅处理目录内以.hsp为后缀的文件。|
| --bundle-name  | 是     | 包名            | 指定的包名，HSP的包名会被修改为指定的包名。                             |
| --version-code | 是     | 版本号           | 指定的版本号，HSP的版本号会被修改为该版本号。需要为整数，且大于0。                 |
| --out-path     | 是     | NA            | 目标文件路径，需要为一个目录。                                     |

## res模式打包指令

此命令用于打包元服务快照资源。

示例：

```
java -jar app_packing_tool.jar --mode res --entrycard-path <path> --pack-info-path <path> --out-path <path> [--force true]
```

**表12** 参数含义及规范

| 指令               | 是否必选项 | 选项            | 描述                                 |
|------------------|-------|---------------|------------------------------------|
| --mode           | 是     | res           | 命令类型。                              |
| --entrycard-path | 是     | NA            | 快照目录的路径。                           |
| --pack-info-path | 是     | NA            | pack.info文件路径。              |
| --out-path       | 是     | NA            | 目标文件路径，文件名必须以.res为后缀。              |
| --force          | 否     | true或者false   | 默认值为false。如果为true，表示当目标文件存在时，强制删除。 |

## fastApp模式打包指令

开发者可以使用打包工具的jar包对应用进行打包，通过传入打包选项、HAP、HSP包文件目录路径，生成所需的App包。App包用于上架应用市场。

**表13** fastApp打包合法性校验规则

| HAP/HSP的module.json中的被校验字段  | 校验规则                           |
| --------------------------------- | --------------------------------- |
| module下的name字段                | 要求所有HAP/HSP的name字段值均不相同。      |
| bundleName                       | 要求所有HAP/HSP的bundleName字段值均保持一致。  |
| bundleType                       | 要求所有HAP/HSP的bundleType字段值均保持一致。  |
| versionCode                      | 要求所有HAP/HSP的versionCode字段值均保持一致。 |
| debug                            | 要求所有HAP/HSP的debug字段值均保持一致。    |
| minAPIVersion                    | 要求所有HAP/HSP的minAPIVersion字段值均保持一致。    |
| minCompatibleVersionCode         | 从API version 16开始，要求所有HAP的minCompatibleVersionCode字段值均保持一致，且均不低于所有HSP对应字段的最大值。<br/>对于API version 15及之前版本，要求所有HAP/HSP的minCompatibleVersionCode字段值均保持一致。    |
| targetAPIVersion                 | 从API version 16开始，要求所有HAP的targetAPIVersion字段值均保持一致，且均不低于所有HSP对应字段的最大值。<br/>对于API version 15及之前版本，要求所有HAP/HSP的targetAPIVersion字段值均保持一致。    |

> **说明：** 
>
> - module.json文件为DevEco Studio编译构建产物，其中的字段与配置文件的对应关系，请参考[表1 module.json与配置文件属性的对照表](packing-tool.md)。

**打包App时的压缩规则：** 打包App时，对release模式的HAP、HSP包会进行压缩，对debug模式的HAP、HSP包不会压缩。

> **说明：** 
> 
> 若HAP/HSP中已压缩的so文件，在打包APP时再次压缩，将不会有明显体积缩减。

示例：

```
java -jar app_packing_tool.jar --mode fastApp [--hap-path <path>] [--hsp-path <path>] --out-path <path> [--signature-path <path>] [--certificate-path <path>] --pack-info-path <path> [--pack-res-path <path>] [--force true] [--encrypt-path <path>]
```

**表14** 参数含义及规范

| 指令                 | 是否必选项 | 选项         | 描述                                                     |
|--------------------|-------|------------|----------------------------------------------------|
| --mode             | 是     | fastApp    | 多个HAP需满足HAP的合法性校验。                   |
| --hap-path         | 否     | NA         | HAP包文件目录路径，目录内要包含一个完整的HAP包的所有文件。允许传入多个路径，多个路径需要用英文“,”分隔。                                              |
| --hsp-path         | 否     | NA         | 1. HSP包文件路径，文件名必须以.hsp为后缀。如果是多个HSP包需要用英文“,”分隔。<br/>2. HSP包文件目录路径，目录内要包含一个完整的HSP包的所有文件。允许传入多个路径，多个路径需要用英文“,”分隔。 |
| --pack-info-path   | 是     | NA         | 文件名必须为pack.info。                                                        |
| --out-path         | 是     | NA         | 目标文件路径，文件名必须以.app为后缀。                                          |
| --signature-path   | 否     | NA         | 签名路径。                                                     |
| --certificate-path | 否     | NA         | 证书路径。                                                               |
| --pack-res-path    | 否     | NA         | pack.res快照文件路径。                                            |
| --force            | 否     | true或者false | 默认值为false。如果为true，表示当目标文件存在时，强制删除。            |
| --encrypt-path     | 否     | NA         | 文件名必须为encrypt.json。                                     |
