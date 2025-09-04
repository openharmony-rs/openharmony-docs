# 打包工具
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @lixueqing513-->
<!--Adviser: @Brilliantry_Rui-->

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
| targetAPIVersion         | -                        | targetAPIVersion           | targetSdkVersion/compileSdkVersion  <br/>说明：targetSdkVersion存在时，targetAPIVersion由targetSdkVersion决定；<br/>否则，targetAPIVersion由compileSdkVersion决定。               |

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
| --compress-level | 否         | number        | lib库下文件压缩等级，默认值1，可选等级1-9。在应用配置compressNativeLibs参数为true的情况下生效，数值越大压缩率越高、压缩速度越慢。 |
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
| debug                            | 从API version 20开始，要求所有HAP的debug字段值均保持一致，如果HAP的debug字段值为false，HSP的debug字段值也必须为false。如果HAP的debug字段值为true，对HSP的debug字段值无要求。<br/>对于API version 19及之前版本，要求所有HAP/HSP的debug字段值均保持一致。    |
| minAPIVersion                    | 从API version 20开始，要求所有HAP的minAPIVersion字段值均保持一致，且均不低于所有HSP对应字段的最大值。<br/>对于API version 19及之前版本，要求所有HAP/HSP的minAPIVersion字段值均保持一致。    |
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
java -jar app_packing_tool.jar --mode app [--hap-path <path>] [--hsp-path <path>] --out-path <path> [--signature-path <path>] [--certificate-path <path>] --pack-info-path <path> [--pack-res-path <path>] [--force true] [--encrypt-path <path>] [--pac-json-path <path>] [--atomic-service-entry-size-limit <size>] [--atomic-service-non-entry-size-limit <size>]
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
| --pac-json-path     | 否     | NA          | pac.json文件路径，文件名必须为pac.json。<br/>从API Version 20开始支持该参数。|
| --atomic-service-entry-size-limit      | 否         | NA            | 设置元服务entry包大小（包含其依赖包的大小）限制，仅Stage模型应用且bundleType为atomicService时生效。取值范围为[0,4194304]的整数，取值为0表示不限制大小，单位KB。不设置该参数时默认值为2048KB。                       |
| --atomic-service-non-entry-size-limit  | 否         | NA            | 设置元服务非entry包大小（包含其依赖包的大小）限制，仅Stage模型应用且bundleType为atomicService时生效。取值范围为[0,4194304]的整数，取值为0表示不限制大小，单位KB。不设置该参数时默认值为2048KB。                     |



## 多工程打包指令

多工程打包适用于多个团队开发同一个应用，但不方便共享代码的情况。开发者通过传入已经打好的HAP、HSP和App包，将多个包打成一个最终的App包，并上架应用市场。

**表6** 多工程打包合法性校验规则

| HAP/HSP的module.json中的被校验字段  | 校验规则                           |
| --------------------------------- | --------------------------------- |
| module下的name字段                | 要求所有HAP/HSP的name字段值均不相同。      |
| bundleName                       | 要求所有HAP/HSP的bundleName字段值均保持一致。  |
| bundleType                       | 要求所有HAP/HSP的bundleType字段值均保持一致。  |
| versionCode                      | 要求所有HAP/HSP的versionCode字段值均保持一致。 |
| debug                            | 从API version 20开始，要求所有HAP的debug字段值均保持一致，如果HAP的debug字段值为false，HSP的debug字段值也必须为false。如果HAP的debug字段值为true，对HSP的debug字段值无要求。<br/>对于API version 19及之前版本，要求所有HAP/HSP的debug字段值均保持一致。    |
| minAPIVersion                    | 从API version 20开始，要求所有HAP的minAPIVersion字段值均保持一致，且均不低于所有HSP对应字段的最大值。<br/>对于API version 19及之前版本，要求所有HAP/HSP的minAPIVersion字段值均保持一致。    |
| minCompatibleVersionCode         | 从API version 16开始，要求所有HAP的minCompatibleVersionCode字段值均保持一致，且均不低于所有HSP对应字段的最大值。<br/>对于API version 15及之前版本，要求所有HAP/HSP的minCompatibleVersionCode字段值均保持一致。    |
| targetAPIVersion                 | 从API version 16开始，要求所有HAP的targetAPIVersion字段值均保持一致，且均不低于所有HSP对应字段的最大值。<br/>对于API version 15及之前版本，要求所有HAP/HSP的targetAPIVersion字段值均保持一致。    |
| versionName                | 从API version 12开始，不再对versionName校验。      |

> **说明：** 
>
> - module.json文件为DevEco Studio编译构建产物，其中的字段与配置文件的对应关系，请参考[表1 module.json与配置文件属性的对照表](packing-tool.md)。

示例：

```
java -jar app_packing_tool.jar --mode multiApp [--hap-list <path>] [--hsp-list <path>] [--app-list <path>] --out-path <option> [--force true] [--encrypt-path <path>] [--pac-json-path <path>] [--atomic-service-entry-size-limit <size>] [--atomic-service-non-entry-size-limit <size>]
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
| --pac-json-path | 否     | NA          | pac.json文件路径，文件名必须为pac.json。<br/>最终app产物中pac.json文件只来源于该参数，不配置的话，最终app产物不包含该文件。<br/>--app-list参数指定的app包中的pac.json不会打包进最终app。<br/>从API Version 20开始支持该参数。|
| --atomic-service-entry-size-limit      | 否         | NA            | 设置元服务entry包大小（包含其依赖包的大小）限制，仅Stage模型应用且bundleType为atomicService时生效。取值范围为[0,4194304]的整数，取值为0表示不限制大小，单位KB。不设置该参数时默认值为2048KB。                       |
| --atomic-service-non-entry-size-limit  | 否         | NA            | 设置元服务非entry包大小（包含其依赖包的大小）限制，仅Stage模型应用且bundleType为atomicService时生效。取值范围为[0,4194304]的整数，取值为0表示不限制大小，单位KB。不设置该参数时默认值为2048KB。                     |



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

## 通用归一指令（generalNormalize）

此命令可以修改传入的HAP/HSP的 deviceType/bundleName/versionName/versionCode/minCompatibleVersionCode/minAPIVersion/targetAPIVersion/<br/>
apiReleaseType/bundleTypes/installationFree/deliveryWithInstall参数，并在指定目录生成修改后的同名HAP/HSP，以及一个general_record.json文件，用于记录所有HAP、HSP原有的参数名称和moduleName。上述设置的参数应符合正确打包规范，否则会在指定目录生成HAP/HSP失败，指定目录不会有文件生成。

> **说明：** 
>
> - 从API version 20开始支持通用归一化指令。

示例：

```
java -jar app_packing_tool.jar --mode generalNormalize --input-list 1.hsp,2.hsp --bundle-name com.example.myapplication --version-code 1000001 --version-name 1.0.1 --min-compatible-version-code 14 --min-api-version 14 --target-api-version 14 --api-release-type Release1 --bundle-type app --installation-free false --delivery-with-install true --device-types default,tablet --out-path out
```

**表12**  参数含义及规范

| 指令                          | 是否必选项 | 选项                                               | 描述                                                         |
| ----------------------------- | ---------- | -------------------------------------------------- | ------------------------------------------------------------ |
| --mode                        | 是         | generalNormalize                                   | 指令类型，表示通用归一化指令。                               |
| --input-list                  | 是         | HAP或HSP的路径                                     | 1. HAP或HSP包文件路径，文件名必须以.hap或.hsp为后缀。多个HAP或HSP包文件路径之间使用“,”分隔。<br/>2. 传入目录时，会读取目录下所有的HAP和HSP文件。 |
| --bundle-name                 | 否         | 包名                                               | 指定的Bundle名称，传入的包的Bundle名称会被修改为该Bundle名称。指定的值不能为空，该字段的详细定义和规格请参考[app.json5](../quick-start/app-configuration-file.md#配置文件标签)中的bundleName字段。 |
| --version-code                | 否         | 版本号                                             | 指定的版本号，传入的包的版本号会被修改为该版本号。取值范围为0~2147483647的整数，指定的值不能为空值，该字段的详细定义和规格请参考[app.json5](../quick-start/app-configuration-file.md#配置文件标签)中的versionCode字段。 |
| --version-name                | 否         | 版本名称                                           | 指定的版本名称，传入的包的版本名称会被修改为该版本名称。指定的值不能为空，该字段的详细定义和规格请参考[app.json5](../quick-start/app-configuration-file.md#配置文件标签)中的versionName字段。 |
| --min-compatible-version-code | 否         | 能够兼容的最低历史版本号                           | 指定的最低历史版本号，传入的包的最低历史版本号会被修改为该版本号。取值范围为0~2147483647的整数，指定的值不能为空值，该字段的详细定义和规格请参考[app.json5](../quick-start/app-configuration-file.md#配置文件标签)中的minCompatibleVersionCode字段。 |
| --min-api-version             | 否         | SDK的API最小版本                                   | 指定的SDK的API最小版本，传入的包的SDK的API最小版本会被修改为该版本。取值范围为0~2147483647的整数，指定的值不能为空值，该字段的详细定义和规格请参考[app.json5](../quick-start/app-configuration-file.md#配置文件标签)中的minAPIVersion字段。 |
| --target-api-version          | 否         | API目标版本                                        | 指定的API目标版本，传入的包的API目标版本会被修改为该版本。取值范围为0~2147483647的整数，指定的值不能为空值，该字段的详细定义和规格请参考[app.json5](../quick-start/app-configuration-file.md#配置文件标签)中的targetAPIVersion字段。 |
| --api-release-type            | 否         | API目标版本的类型                                  | 指定的API目标版本的类型，传入的包的API目标版本的类型会被修改为该类型。指定的值不能为空，该字段的详细定义和规格请参考[app.json5](../quick-start/app-configuration-file.md#配置文件标签)中的apiReleaseType字段。 |
| --bundle-type                 | 否         | Bundle类型                                         | 指定的Bundle类型，传入的包的Bundle类型会被修改为该类型。指定的值不能为空，该字段的详细定义和规格请参考[app.json5](../quick-start/app-configuration-file.md#配置文件标签)中的bundleType字段。 |
| --installation-free           | 否         | 是否支持免安装特性                                 | 指定的免安装特性，传入的包的免安装特性会被修改为该类型。指定的值不能为空，该字段的详细定义和规格请参考Stage模型[module.json5](../quick-start/module-configuration-file.md#配置文件标签)/FA模型[config.json](../quick-start/application-configuration-file-overview-fa.md)中的installationFree字段。 |
| --delivery-with-install       | 否         | 当前HAP是否在用户主动安装HAP所在应用的时候一起安装 | 指定的HAP是否需要一起安装，传入的包的deliveryWithInstall会被修改为该类型。指定的值不能为空，该字段的详细定义和规格参考Stage模型[module.json5](../quick-start/module-configuration-file.md#配置文件标签)/FA模型[config.json](../quick-start/application-configuration-file-overview-fa.md)中的deliveryWithInstall字段。 |
| --device-types                | 否         | 允许Ability运行的设备类型                          | 指定的设备类型，传入的包的设备类型会被修改为该类型。指定的值不能为空，该字段的详细定义和规格请参考Stage模型[module.json5](../quick-start/module-configuration-file.md#配置文件标签)/FA模型[config.json](../quick-start/application-configuration-file-overview-fa.md)中的deviceTypes字段，传入值的形式为字符串格式，多个设备类型之间使用“,”分隔。 |
| --out-path                    | 是         | NA                                                 | 目标文件路径，需要为一个有读写权限的目录。                   |

## res模式打包指令

此命令用于打包元服务快照资源。

示例：

```
java -jar app_packing_tool.jar --mode res --entrycard-path <path> --pack-info-path <path> --out-path <path> [--force true]
```

**表13** 参数含义及规范

| 指令               | 是否必选项 | 选项            | 描述                                 |
|------------------|-------|---------------|------------------------------------|
| --mode           | 是     | res           | 命令类型。                              |
| --entrycard-path | 是     | NA            | 快照目录的路径。                           |
| --pack-info-path | 是     | NA            | pack.info文件路径。              |
| --out-path       | 是     | NA            | 目标文件路径，文件名必须以.res为后缀。              |
| --force          | 否     | true或者false   | 默认值为false。如果为true，表示当目标文件存在时，强制删除。 |

## fastApp模式打包指令

开发者可以使用打包工具的jar包对应用进行打包，通过传入打包选项、HAP、HSP包文件目录路径，生成所需的App包。App包用于上架应用市场。

**表14** fastApp打包合法性校验规则

| HAP/HSP的module.json中的被校验字段  | 校验规则                           |
| --------------------------------- | --------------------------------- |
| module下的name字段                | 要求所有HAP/HSP的name字段值均不相同。      |
| bundleName                       | 要求所有HAP/HSP的bundleName字段值均保持一致。  |
| bundleType                       | 要求所有HAP/HSP的bundleType字段值均保持一致。  |
| versionCode                      | 要求所有HAP/HSP的versionCode字段值均保持一致。 |
| debug                            | 从API version 20开始，要求所有HAP的debug字段值均保持一致，如果HAP的debug字段值为false，HSP的debug字段值也必须为false。如果HAP的debug字段值为true，对HSP的debug字段值无要求。<br/>对于API version 19及之前版本，要求所有HAP/HSP的debug字段值均保持一致。    |
| minAPIVersion                    | 从API version 20开始，要求所有HAP的minAPIVersion字段值均保持一致，且均不低于所有HSP对应字段的最大值。<br/>对于API version 19及之前版本，要求所有HAP/HSP的minAPIVersion字段值均保持一致。    |
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
java -jar app_packing_tool.jar --mode fastApp [--hap-path <path>] [--hsp-path <path>] --out-path <path> [--signature-path <path>] [--certificate-path <path>] --pack-info-path <path> [--pack-res-path <path>] [--force true] [--encrypt-path <path>] [--pac-json-path <path>] [--atomic-service-entry-size-limit <size>] [--atomic-service-non-entry-size-limit <size>]
```

**表15** 参数含义及规范

| 指令                 | 是否必选项 | 选项         | 描述                                                     |
|--------------------|-------|------------|----------------------------------------------------|
| --mode             | 是     | fastApp    | 多个HAP需满足HAP的合法性校验。                                      |
| --hap-path         | 否     | NA         | HAP包文件目录路径，目录内要包含一个完整的HAP包的所有文件。允许传入多个路径，多个路径需要用英文“,”分隔。                                              |
| --hsp-path         | 否     | NA         | 1. HSP包文件路径，文件名必须以.hsp为后缀。如果是多个HSP包需要用英文“,”分隔。<br/>2. HSP包文件目录路径，目录内要包含一个完整的HSP包的所有文件。允许传入多个路径，多个路径需要用英文“,”分隔。 |
| --pack-info-path   | 是     | NA         | 文件名必须为pack.info。                                               |
| --out-path         | 是     | NA         | 目标文件路径，文件名必须以.app为后缀。                                             |
| --signature-path   | 否     | NA         | 签名路径。                                                            |
| --certificate-path | 否     | NA         | 证书路径。                                                |
| --pack-res-path    | 否     | NA         | pack.res快照文件路径。                   |
| --force            | 否     | true或者false | 默认值为false。如果为true，表示当目标文件存在时，强制删除。           |
| --encrypt-path     | 否     | NA         | 文件名必须为encrypt.json。           |
| --pac-json-path     | 否     | NA          | pac.json文件路径，文件名必须为pac.json。<br/>从API Version 20开始支持该参数。|
| --atomic-service-entry-size-limit      | 否         | NA            | 设置元服务entry包大小（包含其依赖包的大小）限制，仅Stage模型应用且bundleType为atomicService时生效。取值范围为[0,4194304]的整数，取值为0表示不限制大小，单位KB。不设置该参数时默认值为2048KB。                      |
| --atomic-service-non-entry-size-limit  | 否         | NA            | 设置元服务非entry包大小（包含其依赖包的大小）限制，仅Stage模型应用且bundleType为atomicService时生效。取值范围为[0,4194304]的整数，取值为0表示不限制大小，单位KB。不设置该参数时默认值为2048KB。                     |

## 打包工具错误码

### 10010001 执行打包工具失败
**错误信息**

Execute packing tool failed.

**错误描述**

执行打包工具失败。

**可能原因**

1. 打包文件合法性校验失败。
2. 需要打包的文件正在被其他程序使用，例如压缩软件或文件管理器。

**处理步骤**

1. 根据报错信息检查[app.json5](../quick-start/app-configuration-file.md)和[module.json5](../quick-start/module-configuration-file.md)中的配置项是否准确。当有多条报错信息时，优先根据第一条报错信息进行排查。
2. 检查是否有程序（如压缩软件、文件管理器）占用打包文件，关闭相关进程后重试。

### 10012001 执行压缩操作失败
**错误信息**

Execute compress process failed.

**错误描述**

执行打包操作时，例如打包HAP或App，执行压缩操作失败，导致打包中断。

**可能原因**

1. 打包文件合法性校验失败。
2. 需要打包的文件正在被其他程序使用，例如压缩软件或文件管理器。

**处理步骤**

1. 根据报错信息检查[app.json5](../quick-start/app-configuration-file.md)和[module.json5](../quick-start/module-configuration-file.md)中的配置项是否准确。当有多条报错信息时，优先根据第一条报错信息进行排查。
2. 检查是否有程序（如压缩软件、文件管理器）占用打包文件，关闭相关进程后重试。

### 10012002 HAP包压缩失败
**错误信息**

Compress Stage Hap failed.

**错误描述**

打包HAP时，执行压缩Stage模型的HAP包操作失败。

**可能原因**

1. Stage模型HAP包打包文件合法性校验失败。
2. 需要打包的文件正在被其他程序使用，例如压缩软件或文件管理器。

**处理步骤**

1. 根据报错信息检查[app.json5](../quick-start/app-configuration-file.md)和[module.json5](../quick-start/module-configuration-file.md)中的配置项是否准确。当有多条报错信息时，优先根据第一条报错信息进行排查。
2. 检查是否有程序（如压缩软件、文件管理器）占用打包文件，关闭相关进程后重试。

### 10012003 校验HAP信息失败
**错误信息**

Verify stage hap info failed.

**错误描述**

打包Stage模型HAP包时，配置信息校验失败。

**可能原因**

`module.json5`中`atomicService`或`continueBundleName`存在配置错误，或`app.json5`中`asanEnabled`或`hwasanEnabled`存在配置错误。

**处理步骤**

参考[asanEnabled配置错误码](#10012004-检查参数asanenabled失败)、[hwasanEnabled配置错误码](#10012005-检查参数hwasanenabled失败)、[atomicService配置错误码](#10012006-检查atomicservice失败)、[continueBundleName配置错误码](#10012007-检查continuebundlename无效)，更改配置项。

### 10012004 检查参数asanEnabled失败
**错误信息**

Check asanEnabled failed.

**错误描述**

打包HAP/HSP时，`app.json5`中`asanEnabled`配置错误。

**可能原因**

`asanEnabled`和`tsanEnabled`被同时设置为true。

**处理步骤**

检查[app.json5](../quick-start/app-configuration-file.md)，修改`asanEnabled`和`tsanEnabled`，确保二者不会同时为true。

### 10012005 检查参数hwasanEnabled失败
**错误信息**

Check hwasanEnabled failed.

**错误描述**

打包HAP/HSP时，`app.json5`中`hwasanEnabled`配置错误。

**可能原因**

1. `hwasanEnabled`和`asanEnabled`被同时配置为true。
2. `hwasanEnabled`和`tsanEnabled`被同时配置为true。
3. `hwasanEnabled`和`GWPAsanEnabled`被同时配置为true。

**处理步骤**

检查[app.json5](../quick-start/app-configuration-file.md)，确保`asanEnabled`、`tsanEnabled`、`GWPAsanEnabled`三项的中任一项与`hwasanEnabled`，不会同时配置为true。

### 10012006 检查atomicService失败
**错误信息**

Check atomicService failed.

**错误描述**

打包HAP/HSP时，`atomicService`配置检查失败。

**可能原因**

1. `module.json5`中`entry`模块未配置ability，导致`atomicService`配置检查失败。
2. 当`app.json5`中`bundleType`配置为`atomicService`时，但`module.json5`中`installationFree`为false。

**处理步骤**

1. 检查[module.json5](../quick-start/module-configuration-file.md)，确保`module.json5`文件中正确配置了`abilities`标签，并且至少包含一个ability，详细请参见[abilities标签](../quick-start/module-configuration-file.md#abilities标签)。
2. 检查`module.json5`和[app.json5](../quick-start/app-configuration-file.md)，当`bundleType`为`atomicService`时，确保`installationFree`配置为true，反之，需要配置为false。

### 10012007 检查continueBundleName无效
**错误信息**

Check continueBundleName invalid.

**错误描述**

打包HAP/HSP时，`continueBundleName`配置检查失败。

**可能原因**

`module.json5`中的`continueBundleName`与`app.json5`中`bundleName`相同。

**处理步骤**

修改`continueBundleName`，确保其与[app.json5](../quick-start/app-configuration-file.md)中的`bundleName`不同。

### 10012008 检查overlay失败
**错误信息**

Check whether is an overlay hsp failed.

**错误描述**

检查是否是overlay特性HSP包失败。

**可能原因**

1. 在`module.json5`中同时配置了`targetModuleName`与`requestPermissions`。

2. `module.json5`中的`targetModuleName`和`module.json5`中的`name`相同。

3. 在`module.json5`中配置了`targetPriority`时，未配置`targetModuleName`。

4. 在`app.json5`中配置了`targetBundleName`时，`module.json5`中未配置`targetModuleName`。

5. 在`app.json5`中的`targetBundleName`与`bundleName`配置相同。

**处理步骤**

1. 检查[module.json5](../quick-start/module-configuration-file.md)，确保`targetModuleName`和`requestPermissions`不会同时出现。
2. 检查`module.json5`，确保`targetModuleName`和`name`不同。
3. 检查`module.json5`，确保配置`targetPriority`时，同时配置了`targetModuleName`。
4. 检查[app.json5](../quick-start/app-configuration-file.md)和`module.json5`，确保配置`targetBundleName`时，同时配置了`targetModuleName`。
5. 检查`app.json5`，确保`targetBundleName`与`bundleName`不同。

### 10012009 执行压缩操作时异常
**错误信息**

Process compress exception.

**错误描述**

执行压缩HAP/HSP/App操作时存在异常。

**可能原因**

1. 打包文件合法性校验失败。
2. 需要打包的文件正在被其他程序使用，例如压缩软件或文件管理器。

**处理步骤**

1. 根据报错信息检查[app.json5](../quick-start/app-configuration-file.md)和[module.json5](../quick-start/module-configuration-file.md)中的配置项是否准确。当有多条报错信息时，优先根据第一条报错信息进行排查。
2. 检查是否有程序（如压缩软件、文件管理器）占用打包文件，关闭相关进程后重试。

### 10012015 构建App包失败
**错误信息**

Compress app file failed.

**错误描述**

构建App包失败。

**可能原因**

1. App打包文件合法性校验失败。
2. 需要打包的文件正在被其他程序使用，例如压缩软件或文件管理器。

**处理步骤**

1. 根据报错信息检查[app.json5](../quick-start/app-configuration-file.md)和[module.json5](../quick-start/module-configuration-file.md)中的配置项是否准确。当有多条报错信息时，优先根据第一条报错信息进行排查。
2. 检查是否有程序（如压缩软件、文件管理器）占用打包文件，关闭相关进程后重试。

### 10012017 检查SharedAPP无效
**错误信息**

Check shared App mode invalid.

**错误描述**

构建[bundleType](../quick-start/app-configuration-file.md#配置文件标签)为shared的App包时，检查HSP包无效。

**可能原因**

1. 存在两个以上的[HSP包](../quick-start/in-app-hsp.md)。例如下图使用DevEco Studio构建App时，工程中包含了两个HSP包library和library1，此时打包APP包失败。

![alt text](figures/zh_cn_packing_tool_image_10012017_01.png)

2. HSP包在`module.json5`中配置了`dependencies`。

**处理步骤**

1. 检查打包文件，确保`bundleType`为shared的App包中，HSP包不超过一个。
2. 检查打包文件，删除HSP包中[module.json5](../quick-start/module-configuration-file.md)配置的`dependencies`。

### 10012022 校验Stage HSP失败
**错误信息**

Verify stage hsp info failed.

**错误描述**

打包HSP时，校验Stage模型HSP包失败。

**可能原因**

1. `module.json5`中的`atomicService`、`continueBundleName`存在配置错误，或`app.json5`中的`asanEnabled`、`hwasanEnabled`存在配置错误。
2. overlay配置出错。

**处理步骤**

1. 参考[asanEnabled配置错误码](#10012004-检查参数asanenabled失败)、[hwasanEnabled配置错误码](#10012005-检查参数hwasanenabled失败)、[atomicService配置错误码](#10012006-检查atomicservice失败)、[continueBundleName配置错误码](#10012007-检查continuebundlename无效)，更改配置项。
1. 参考[检查overlay失败](#10012008-检查overlay失败)，更改配置项。

### 10012024 校验元服务大小失败
**错误信息**

Check atomicService size failed.

**错误描述**

打包App时，检查元服务包的大小超出了2MB。

**可能原因**

元服务包及依赖的共享库或资源文件大小超出了2MB的限制。

**处理步骤**

优化并减少包的大小，例如删除不必要的资源、精简代码或减少依赖。

### 10013005 检查模块bundleType失败
**错误信息**

Failed to parse module.json and bundleType.

**错误描述**

检查模块bundleType失败。

**可能原因**

不符合配置要求，例如：
1. 模块的[app.json5](../quick-start/app-configuration-file.md)配置文件中`bundleType`为app，但[module.json5](../quick-start/module-configuration-file.md)中的`installationFree`属性值为true。
2. 模块的app.json5配置文件中`bundleType`为atomicService，但module.json5中的`installationFree`属性值为false。
3. 模块的app.json5配置文件中`bundleType`为shared，但module.json5中的`type`属性值不是shared。

**处理步骤**

1. 确保app.json5配置文件中`bundleType`为app时，module.json5中的`installationFree`属性值为false。
2. 确保app.json5配置文件中`bundleType`为atomicService时，module.json5中的`installationFree`属性值为true。
3. 确保app.json5配置文件中`bundleType`为shared时，module.json5中的`type`属性值也是shared。
4. 当有多条报错信息时，优先根据第一条报错信息进行排查。

### 10013006 检查entry模块中的ability失败
**错误信息**

check entry module at least one ability failed.

**错误描述**

Entry类型包中没有ability。

**可能原因**

Entry类型包中不存在ability，该错误可能是由于`module.json5`未配置`abilities`或者`abilities`配置为空引起。

**处理步骤**

检查[module.json5](../quick-start/module-configuration-file.md)，确保Entry类型包`abilities`正确配置了ability。

### 10013007 检查installationFree错误
**错误信息**

Check module atomicService installationFree invalid.

**错误描述**

打包HAP/HSP时，检查`atomicService`和`installationFree`配置出错。

**可能原因**

1. `app.json5`中的`bundleType`配置了无效值。
2. 当`bundleType`为shared时，`module.json5`中`installationFree`未设置为false。
3. 当`installationFree`为true时，`bundleType`未设置为atomicService。

**处理步骤**

1. 检查[app.json5](../quick-start/app-configuration-file.md)，确保`bundleType`设置为app，atomicService，shared<!--Del-->，appService<!--DelEnd-->之一。
2. 如果`bundleType`为shared，确保[module.json5](../quick-start/module-configuration-file.md)中的`installationFree`设置为false。
3. 如果`installationFree`为true，确保`bundleType`设置为atomicService。

### 10014001 未找到可用文件
**错误信息**

File available not found exception.

**错误描述**

使用打包工具打包时，需要打包的文件不可使用。

**可能原因**

1. 指定的文件路径错误或文件不存在。
2. 文件正在被其他程序使用，例如压缩软件或文件管理器。
3. 当前用户没有访问该文件的权限。

**处理步骤**

1. 确认提供的文件路径正确，并检查该文件是否存在。
2. 检查是否有程序（如压缩软件、文件管理器）占用文件，关闭相关进程后重试。
3. 检查并调整文件的访问权限，例如当前用户可以读取、修改、删除文件。

### 10016003 分发策略相交校验失败
**错误信息**

Check two distroFilter policy disjoint invalid.

**错误描述**

[HAP唯一性校验](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-verification-rule)需要判断分发策略是否相交，由于分发策略配置错误，导致无法判断分发策略是否相交。

**可能原因**

分发策略`policy`、`value`标签为空或为无效值。

**处理步骤**

检查分发策略相关配置，确保`policy`的值为`include`或`exclude`，`value`取值参见[distributionFilter标签](../quick-start/module-configuration-file.md#distributionfilter标签)。

### 10016006 检查HAP包无效
**错误信息**

Verify hap info is invalid.

**错误描述**

构建App包时，校验用于打包的HAP/HSP失败。

**可能原因**

多个HAP/HSP包配置之间存在冲突。

**处理步骤**

根据报错信息检查[app.json5](../quick-start/app-configuration-file.md)和[module.json5](../quick-start/module-configuration-file.md)中的配置项是否准确。当有多条报错信息时，优先根据第一条报错信息进行排查。

### 10016007 检查entry模块无效
**错误信息**

Check entry module invalid.

**错误描述**

构建App包时，当工程中存在多个Entry类型HAP包时，检查配置信息失败。

**可能原因**

不符合HAP唯一性校验规则。

**处理步骤**

参考[HAP唯一性校验](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-verification-rule)，调整工程中的Entry类型HAP配置。

### 10016009 检查依赖错误
**错误信息**

Check dependency list is invalid.

**错误描述**

构建App包时，模块依赖关系检查失败。

**可能原因**

1. 模块间存在循环依赖，例如：模块library1的`module.json5`中`dependencies`配置了library2，同时模块library2中的`dependencies`配置了library1，则这两个模块之间构成循环依赖。
2. `module.json5`配置中依赖的模块对应的`module.json5`中的`type`为entry或feature。

**处理步骤**

1. 检查[module.json5](../quick-start/module-configuration-file.md)中的`dependencies`，删除循环依赖，确保App中不存在循环依赖。
2. 检查`module.json5`中的`dependencies`的配置，删除对entry或feature类型模块的依赖。

### 10016010 检查元服务无效
**错误信息**

Check atomicservice is invalid.

**错误描述**

构建App包时，检查元服务无效。

**可能原因**

`module.json5`中`preloads`配置的`moduleName`错误。

**处理步骤**

检查[module.json5](../quick-start/module-configuration-file.md)中的[preloads属性](../quick-start/module-configuration-file.md#atomicservice标签)下的`moduleName`，不能配置为自身模块`module.json5`中的`name`，且`moduleName`对应的模块必须存在。

### 10016011 检查元服务预加载无效
**错误信息**

Atomicservice preloads is invalid.

**错误描述**

构建bundleType为atomicService类型的App包时，检查元服务包预加载的模块无效。

**可能原因**

1. 元服务包`module.json5`中的`preloads`配置了重复的`moduleName`。
2. 元服务包`preloads`配置的`moduleName`，和其他元服务包中`module.json5`中的`name`不匹配。
3. 元服务包`preloads`配置的`moduleName`，和自身`module.json5`中的`name`相同。

**处理步骤**

检查[module.json5](../quick-start/module-configuration-file.md)中元服务[preloads属性](../quick-start/module-configuration-file.md#atomicservice标签)，确保没有配置重复的模块，配置所有的模块都存在且不能配置自身的模块名。

### 10016012 目标模块不存在
**错误信息**

TargetModuleName is not exist.

**错误描述**

构建App时，模块中配置了目标模块，但未找到该模块。

**可能原因**

`module.json5`中配置了`targetModuleName`，但和其他模块对应`module.json5`中的`name`均不同。

**处理步骤**

检查`targetModuleName`配置项，确保其正确配置（详细请参见[module.json5配置文件标签](../quick-start/module-configuration-file.md#配置文件标签)及targetModuleName属性），必要时创建目标模块。

### 10016014 代理数据不唯一
**错误信息**

Proxy data uri is not unique.

**错误描述**

数据代理uri不唯一，存在重复项。

**可能原因**

`module.json5`中的`proxyData`配置的uri存在重复。

**处理步骤**

检查[module.json5](../quick-start/module-configuration-file.md)，删除`proxyData`中重复的uri，确保每个uri都是唯一的（详细请参见[proxyData标签](../quick-start/module-configuration-file.md#proxydata标签)）。

### 10016015 ContinueType配置无效
**错误信息**

Check continueType is invalid.

**错误描述**

构建App时，检查continueType配置错误。

**可能原因**

1. `module.json5`不同的ability存在重复的`continueType`配置项。
2. 不同的`module.json5`中同时存在重复的`deviceType`配置项和`continueType`配置项。

**处理步骤**

检查[module.json5](../quick-start/module-configuration-file.md)，删除`continueType`或`deviceType`重复的配置项。

### 10016016 文件大小检查错误
**错误信息**

Check file size failed.

**错误描述**

构建元服务类型App时，检查单个包大小超过2MB。

**可能原因**

单个包大小超过2MB，超出限制。

**处理步骤**

优化并减少对应单个包文件的大小，例如删除不必要的资源、精简代码或压缩文件。

### 10016018 元服务模块大小检查错误
**错误信息**

Check the atomicService module size failed.

**错误描述**

构建元服务类型App时，检查单个包和其依赖的共享库大小超过2MB。

**可能原因**

单个包和其依赖的共享库总大小超过2MB，超出限制。

**处理步骤**

优化并减少相应包的大小，例如删除不必要的资源、精简代码或减少依赖项。

### 10016019 检查分发策略无效
**错误信息**

Check the entry module distributionFilter is invalid.

**错误描述**

检查Entry类型模块分发策略错误。

**可能原因**

Entry类型模块分发策略配置存在错误。

**处理步骤**

检查Entry模块分发策略是否正确配置，例如`policy`的值应为`exclude`或`include`，详细请参考[distributionFilter标签](../quick-start/module-configuration-file.md#distributionfilter标签)。

### 10011021 通用归一化命令失败

**错误信息**

Parse and check args invalid in generalNormalize mode.

**错误描述**

通用归一化命令失败。

**可能原因**

1. 传入的参数类型错误。
2. 传入参数范围错误。
3. 传入HAP/HSP包不完整，缺少json文件（json文件配置请参考Stage模型[module.json5](../quick-start/module-configuration-file.md#配置文件标签)/FA模型[config.json](../quick-start/application-configuration-file-overview-fa.md)）。

**处理步骤**

检查并传入正确的命令参数和有效的包文件。