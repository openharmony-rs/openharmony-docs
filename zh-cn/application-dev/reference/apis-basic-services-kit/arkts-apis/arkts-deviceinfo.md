# @ohos.deviceInfo

本模块提供终端设备信息查询能力，支持获取设备类型、品牌、型号、系统版本、安全补丁级别、设备唯一标识等多种设备信息，适用于设备适配、版本兼容性检查、设备识别、统计分析等场景，帮助开发者快速获取设备信息进行应用适配和优化。开发者不可配置这些信息。 > **说明：** > > 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > hardwareProfile、incrementalVersion、buildType、buildUser、buildHost、buildTime、buildRootHash等参数返回值为default，这些参数会在设备正式商用版本中配置具体值。 > 本模块接口返回设备常量信息，建议应用只调用一次，不需要频繁调用。未特殊说明的字段，数据长度最大值为96字节。 > 相关错误码请参考[deviceInfo错误码](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/errorcode-device-info)

**起始版本：** 6

<!--Device-unnamed-declare namespace deviceInfo--><!--Device-unnamed-declare namespace deviceInfo-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## 导入模块

```TypeScript
import { deviceInfo } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [apiAvailable](arkts-basicservices-deviceinfo-apiavailable-f.md) | 检查指定的API版本在当前设备上是否可用。 此方法提供跨不同OpenHarmony/分布式操作系统版本的兼容性检查。该方法会根据输入格式和API版本范围自动选择合适的版本检查方法。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DeviceTypes](arkts-basicservices-deviceinfo-devicetypes-e.md) | 设备类型枚举值，可用于校验deviceType的返回值。 |
| [PerformanceClassLevel](arkts-basicservices-deviceinfo-performanceclasslevel-e.md) | 表示设备能力定级的枚举。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [ODID](arkts-basicservices-deviceinfo-con.md#odid) | ODID（Open Developer Identifier，开发者匿名设备标识符）。 **ODID值会在以下场景重新生成：** 手机恢复出厂设置。 同一设备上同一个开发者(developerId相同)的应用全部卸载后重新安装时。 **ODID生成规则：** 根据签名信息里developerId解析出的groupId生成，developerId规则为groupId.developerId，若无groupId则取整个developerId作为groupId。 同一设备上运行的同一个开发者(developerId相同)的应用，ODID相同。 同一个设备上不同开发者(developerId不同)的应用，ODID不同。 不同设备上同一个开发者(developerId相同)的应用，ODID不同。 不同设备上不同开发者(developerId不同)的应用，ODID不同。 |
| [abiList](arkts-basicservices-deviceinfo-con.md#abilist) | 应用二进制接口（Abi）。 示例：arm64-v8a |
| [bootCount](arkts-basicservices-deviceinfo-con.md#bootcount) | 当前设备重启次数，获取失败时返回-1。 示例：100 |
| [bootloaderVersion](arkts-basicservices-deviceinfo-con.md#bootloaderversion) | Bootloader版本号，用于标识设备启动引导程序的版本信息。 示例：bootloader |
| [brand](arkts-basicservices-deviceinfo-con.md#brand) | 设备品牌名称。 |
| [buildHost](arkts-basicservices-deviceinfo-con.md#buildhost) | 构建主机。 示例：default |
| [buildRootHash](arkts-basicservices-deviceinfo-con.md#buildroothash) | 构建版本Hash。 示例：default |
| [buildTime](arkts-basicservices-deviceinfo-con.md#buildtime) | 构建时间。 示例：default |
| [buildType](arkts-basicservices-deviceinfo-con.md#buildtype) | 构建类型。 示例：default |
| [buildUser](arkts-basicservices-deviceinfo-con.md#builduser) | 构建用户。 示例：default |
| [buildVersion](arkts-basicservices-deviceinfo-con.md#buildversion) | Build版本号，标识编译构建的版本号，值为osFullName中的第四位数值，建议直接使用deviceInfo.buildVersion获取，可提升效率，不建议开发者自主解析osFullName获取。 示例：1 |
| [chipType](arkts-basicservices-deviceinfo-con.md#chiptype) | 当前设备CPU芯片型号。 **使用场景**：用于根据芯片型号进行性能适配、设备特性识别、兼容性检查等场景，不同芯片型号可能具有不同的GPU性能、AI加速能力等特性。 示例：xxxxx |
| [deviceColor](arkts-basicservices-deviceinfo-con.md#devicecolor) | 当前设备颜色。如果无法获取，则返回空字符串 示例：gold |
| [deviceType](arkts-basicservices-deviceinfo-con.md#devicetype) | 设备类型。详细请参考[deviceTypes标签](../../../quick-start/module-configuration-file.md#devicetypes标签)。 示例：<!--RP1-->wearable<!--RP1End--> |
| [diskSN](arkts-basicservices-deviceinfo-con.md#disksn) | 硬盘序列号，该接口在执行期间会拉起临时进程，当系统负载较高时，可能引发阻塞风险。为确保应用主线程的响应性能，建议避免在主线程中调用。设备信息因设备而异且固定不变，可在首次获取后缓存在本地，避免每次使用时重复获取，以提升性能。 |
| [displayVersion](arkts-basicservices-deviceinfo-con.md#displayversion) | 产品版本。 示例：<!--RP8-->XXX X.X.X.X<!--RP8End--> |
| [distributionOSApiName](arkts-basicservices-deviceinfo-con.md#distributionosapiname) | 发行版系统API版本名称<!--Del-->，由发行方定义<!--DelEnd-->。 <!--RP16-- |
| [distributionOSApiVersion](arkts-basicservices-deviceinfo-con.md#distributionosapiversion) | 发行版系统API版本<!--Del-->，由发行方定义<!--DelEnd-->。<!--RP15--><!--RP15End--> 示例：50001 |
| [distributionOSName](arkts-basicservices-deviceinfo-con.md#distributionosname) | 发行版系统名称<!--Del-->，由发行方定义<!--DelEnd-->。 示例：OpenHarmony |
| [distributionOSReleaseType](arkts-basicservices-deviceinfo-con.md#distributionosreleasetype) | 发行版系统类型<!--Del-->，由发行方定义<!--DelEnd-->。 示例：Release |
| [distributionOSVersion](arkts-basicservices-deviceinfo-con.md#distributionosversion) | 发行版系统版本号<!--Del-->，由发行方定义<!--DelEnd-->。<!--RP11--><!--RP11End--> 示例：5.0.0 |
| [featureVersion](arkts-basicservices-deviceinfo-con.md#featureversion) | Feature版本号，标识规划的新特性版本，值为osFullName中的第三位数值，建议直接使用deviceInfo.featureVersion获取，可提升效率，不建议开发者自主解析osFullName获取。 示例：0 |
| [firstApiVersion](arkts-basicservices-deviceinfo-con.md#firstapiversion) | 首个版本系统软件API版本。 示例：3 |
| [hardwareModel](arkts-basicservices-deviceinfo-con.md#hardwaremodel) | 硬件版本号。 示例：<!--RP6-->TASA00CVN1<!--RP6End--> |
| [hardwareProfile](arkts-basicservices-deviceinfo-con.md#hardwareprofile) | 硬件Profile。 |
| [incrementalVersion](arkts-basicservices-deviceinfo-con.md#incrementalversion) | 差异版本号，是编译时生成的ohos的版本号。 示例：6.1.1.120 |
| [majorVersion](arkts-basicservices-deviceinfo-con.md#majorversion) | Major版本号，随主版本更新增加，值为osFullName中的第一位数值，建议直接使用deviceInfo.majorVersion获取，可提升效率，不建议开发者自主解析osFullName获取。 示例：5 |
| [manufacture](arkts-basicservices-deviceinfo-con.md#manufacture) | 设备厂家名称。 |
| [marketName](arkts-basicservices-deviceinfo-con.md#marketname) | 外部产品系列。 示例：<!--RP2-->Mate XX<!--RP2End--> |
| [osFullName](arkts-basicservices-deviceinfo-con.md#osfullname) | 系统版本，版本格式<!--RP12-->OpenHarmony-x.x.x.x，其中x表示数字占位符。<!--RP12End-->如需获取版本号各段数值，建议直接使用majorVersion、seniorVersion、featureVersion、buildVersion字段，可提升效率，不建议解析osFullName获取。 示例：<!--RP10-->OpenHarmony-5.0.0.1<!--RP10End--> |
| [osReleaseType](arkts-basicservices-deviceinfo-con.md#osreleasetype) | 系统的发布类型，取值为： - Canary：面向特定开发者发布的早期预览版本，不承诺API稳定性。 - Beta：面向开发者公开发布的Beta版本，不承诺API稳定性。 - Release：面向开发者公开发布的正式版本，承诺API稳定性。 示例：<!--RP9-->Canary/Beta/Release<!--RP9End--> |
| [performanceClass](arkts-basicservices-deviceinfo-con.md#performanceclass) | 描述设备能力等级，基于CPU、内存、存储读写性能和屏幕分辨率等因素综合评估。 **使用场景**：用于根据设备能力进行性能适配，如调整动画复杂度、选择不同质量的资源、动态控制功能特性等。 示例：0 |
| [productModel](arkts-basicservices-deviceinfo-con.md#productmodel) | 认证型号。 示例：<!--RP4-->TAS-AL00<!--RP4End--> |
| [productModelAlias](arkts-basicservices-deviceinfo-con.md#productmodelalias) | 认证型号别名。 示例：TAS-AL00 |
| [productSeries](arkts-basicservices-deviceinfo-con.md#productseries) | 产品系列。 示例：<!--RP3-->TAS<!--RP3End--> |
| [sdkApiVersion](arkts-basicservices-deviceinfo-con.md#sdkapiversion) | 系统软件API版本。 示例：12 |
| [sdkMinorApiVersion](arkts-basicservices-deviceinfo-con.md#sdkminorapiversion) | 系统软件Minor API版本。从API 26.0.0 版本开始，系统API版本格式：sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion。 26.0.0 示例：0 |
| [sdkPatchApiVersion](arkts-basicservices-deviceinfo-con.md#sdkpatchapiversion) | 系统软件Patch API版本。从API 26.0.0 版本开始，系统API版本格式：sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion。 26.0.0 示例：0 |
| [securityPatchTag](arkts-basicservices-deviceinfo-con.md#securitypatchtag) | 安全补丁级别。 示例：<!--RP7-->2021/01/01<!--RP7End--> |
| [seniorVersion](arkts-basicservices-deviceinfo-con.md#seniorversion) | Senior版本号，随局部架构、重大特性增加，值为osFullName中的第二位数值，建议直接使用deviceInfo.seniorVersion获取，可提升效率，不建议开发者自主解析osFullName获取。 示例：0 |
| [serial](arkts-basicservices-deviceinfo-con.md#serial) | 设备序列号SN(Serial Number)，该接口在执行期间会拉起临时进程，当系统负载较高时，可能引发阻塞风险。为确保应用主线程的响应性能，建议避免在主线程中调用。设备信息因设备而异且固定不变，可在首次获取后缓存在本地，避免每次使用时重复获取，以提升性能。 |
| [softwareModel](arkts-basicservices-deviceinfo-con.md#softwaremodel) | 内部软件子型号。 示例：<!--RP5-->TAS-AL00<!--RP5End--> |
| [udid](arkts-basicservices-deviceinfo-con.md#udid) | 设备UDID，该接口在执行期间会拉起临时进程，当系统负载较高时，可能引发阻塞风险。为确保应用主线程的响应性能，建议避免在主线程中调用。设备信息因设备而异且固定不变，可在首次获取后缓存在本地，避免每次使用时重复获取，以提升性能。 |
| [versionId](arkts-basicservices-deviceinfo-con.md#versionid) | 版本ID。由deviceType、manufacture、brand、productSeries、osFullName、productModel、softwareModel、sdkApiVersion、 incrementalVersion、buildType拼接组成。如果需要获取其中的某个字段值，建议直接使用对应的字段（如deviceType、manufacture等），可提升效率，不建议解析versionId获取。 |

