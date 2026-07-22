# 常量

## ODID

```TypeScript
const ODID: string
```

开发者匿名设备标识符。

**ODID值会在以下场景重新生成：**

手机恢复出厂设置。

同一设备上同一个开发者(developerId相同)的应用全部卸载后重新安装时。

**ODID生成规则：**

根据签名信息里developerId解析出的groupId生成，developerId规则为groupId.developerId，若无groupId则取整个developerId作为groupId。

同一设备上运行的同一个开发者(developerId相同)的应用，ODID相同。

同一个设备上不同开发者(developerId不同)的应用，ODID不同。

不同设备上同一个开发者(developerId相同)的应用，ODID不同。

不同设备上不同开发者(developerId不同)的应用，ODID不同。

**说明：**数据长度为37字节(包含结束符)。

示例：1234a567-XXXX-XXXX-XXXX-XXXXXXXXXXXX

**起始版本：** 12

<!--Device-deviceInfo-const ODID: string--><!--Device-deviceInfo-const ODID: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## abiList

```TypeScript
const abiList: string
```

应用二进制接口（Abi）。

示例：arm64-v8a

**起始版本：** 6

<!--Device-deviceInfo-const abiList: string--><!--Device-deviceInfo-const abiList: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## bootCount

```TypeScript
const bootCount: number
```

当前设备重启次数，获取失败时返回-1

示例：100

**起始版本：** 21

<!--Device-deviceInfo-const bootCount: number--><!--Device-deviceInfo-const bootCount: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## bootloaderVersion

```TypeScript
const bootloaderVersion: string
```

Bootloader版本号，用于标识设备启动引导程序的版本信息。

示例：bootloader

**起始版本：** 6

<!--Device-deviceInfo-const bootloaderVersion: string--><!--Device-deviceInfo-const bootloaderVersion: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## brand

```TypeScript
const brand: string
```

设备品牌名称。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-deviceInfo-const brand: string--><!--Device-deviceInfo-const brand: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## buildHost

```TypeScript
const buildHost: string
```

构建主机。

示例：default

**起始版本：** 6

<!--Device-deviceInfo-const buildHost: string--><!--Device-deviceInfo-const buildHost: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## buildRootHash

```TypeScript
const buildRootHash: string
```

构建版本Hash。

示例：default

**起始版本：** 6

<!--Device-deviceInfo-const buildRootHash: string--><!--Device-deviceInfo-const buildRootHash: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## buildTime

```TypeScript
const buildTime: string
```

构建时间。

示例：default

**起始版本：** 6

<!--Device-deviceInfo-const buildTime: string--><!--Device-deviceInfo-const buildTime: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## buildType

```TypeScript
const buildType: string
```

构建类型。

示例：default

**起始版本：** 6

<!--Device-deviceInfo-const buildType: string--><!--Device-deviceInfo-const buildType: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## buildUser

```TypeScript
const buildUser: string
```

构建用户。

示例：default

**起始版本：** 6

<!--Device-deviceInfo-const buildUser: string--><!--Device-deviceInfo-const buildUser: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## buildVersion

```TypeScript
const buildVersion: number
```

Build版本号，标识编译构建的版本号，值为osFullName中的第四位数值，建议直接使用deviceInfo.buildVersion获取，可提升效率，不建议开发者自主解析osFullName获取。

示例：1

**起始版本：** 6

<!--Device-deviceInfo-const buildVersion: number--><!--Device-deviceInfo-const buildVersion: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## chipType

```TypeScript
const chipType: string
```

当前设备CPU芯片型号

示例：xxxxx

**起始版本：** 21

<!--Device-deviceInfo-const chipType: string--><!--Device-deviceInfo-const chipType: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## deviceColor

```TypeScript
const deviceColor: string
```

当前设备颜色。如果无法获取，则返回空字符串

示例：gold

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-deviceInfo-const deviceColor: string--><!--Device-deviceInfo-const deviceColor: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## deviceType

```TypeScript
const deviceType: string
```

设备类型。详细请参考[deviceTypes标签](../../../quick-start/module-configuration-file.md#devicetypes标签)。

示例：<!--RP1-->wearable<!--RP1End-->

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-deviceInfo-const deviceType: string--><!--Device-deviceInfo-const deviceType: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## diskSN

```TypeScript
const diskSN: string
```

硬盘序列号。

**说明** ：该字段只能在2in1设备进行查询，其他设备查询结果为空。

ohos.permission.ACCESS_DISK_PHY_INFO

示例：2502EM400567

**起始版本：** 15

**需要权限：** ohos.permission.ACCESS_DISK_PHY_INFO

<!--Device-deviceInfo-const diskSN: string--><!--Device-deviceInfo-const diskSN: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## displayVersion

```TypeScript
const displayVersion: string
```

产品版本。

示例：<!--RP8-->XXX X.X.X.X<!--RP8End-->

**起始版本：** 6

<!--Device-deviceInfo-const displayVersion: string--><!--Device-deviceInfo-const displayVersion: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## distributionOSApiName

```TypeScript
const distributionOSApiName: string
```

发行版系统api版本名称<!--Del-->，由发行方定义<!--DelEnd-->。

**起始版本：** 13

<!--Device-deviceInfo-const distributionOSApiName: string--><!--Device-deviceInfo-const distributionOSApiName: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## distributionOSApiVersion

```TypeScript
const distributionOSApiVersion: number
```

发行版系统api版本<!--Del-->，由发行方定义<!--DelEnd-->。

示例：50001

**起始版本：** 10

<!--Device-deviceInfo-const distributionOSApiVersion: number--><!--Device-deviceInfo-const distributionOSApiVersion: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## distributionOSName

```TypeScript
const distributionOSName: string
```

发行版系统名称<!--Del-->，由发行方定义<!--DelEnd-->。

示例：OpenHarmony

**起始版本：** 10

<!--Device-deviceInfo-const distributionOSName: string--><!--Device-deviceInfo-const distributionOSName: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## distributionOSReleaseType

```TypeScript
const distributionOSReleaseType: string
```

发行版系统类型<!--Del-->，由发行方定义<!--DelEnd-->。

示例：Release

**起始版本：** 10

<!--Device-deviceInfo-const distributionOSReleaseType: string--><!--Device-deviceInfo-const distributionOSReleaseType: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## distributionOSVersion

```TypeScript
const distributionOSVersion: string
```

发行版系统版本号<!--Del-->，由发行方定义<!--DelEnd-->。<!--RP11--><!--RP11End-->

示例：5.0.0

**起始版本：** 10

<!--Device-deviceInfo-const distributionOSVersion: string--><!--Device-deviceInfo-const distributionOSVersion: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## featureVersion

```TypeScript
const featureVersion: number
```

Feature版本号，标识规划的新特性版本，值为osFullName中的第三位数值，建议直接使用deviceInfo.featureVersion获取，可提升效率，不建议开发者自主解析osFullName获取。

示例：0

**起始版本：** 6

<!--Device-deviceInfo-const featureVersion: number--><!--Device-deviceInfo-const featureVersion: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## firstApiVersion

```TypeScript
const firstApiVersion: number
```

首个版本系统软件API版本。

示例：3

**起始版本：** 6

<!--Device-deviceInfo-const firstApiVersion: number--><!--Device-deviceInfo-const firstApiVersion: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## hardwareModel

```TypeScript
const hardwareModel: string
```

硬件版本号。

示例：<!--RP6-->TASA00CVN1<!--RP6End-->

**起始版本：** 6

<!--Device-deviceInfo-const hardwareModel: string--><!--Device-deviceInfo-const hardwareModel: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## hardwareProfile

```TypeScript
const hardwareProfile: string
```

硬件Profile。

**说明：**

从API version 6 开始支持，从API version 9 开始废弃，建议使用[系统能力SystemCapability](../../../reference/syscap.md)替代。

示例：default

**起始版本：** 6

**废弃版本：** 9

<!--Device-deviceInfo-const hardwareProfile: string--><!--Device-deviceInfo-const hardwareProfile: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## incrementalVersion

```TypeScript
const incrementalVersion: string
```

差异版本号，是编译时生成的ohos的版本号。

示例：default

**起始版本：** 6

<!--Device-deviceInfo-const incrementalVersion: string--><!--Device-deviceInfo-const incrementalVersion: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## majorVersion

```TypeScript
const majorVersion: number
```

Major版本号，随主版本更新增加，值为osFullName中的第一位数值，建议直接使用deviceInfo.majorVersion获取，可提升效率，不建议开发者自主解析osFullName获取。

示例：5

**起始版本：** 6

<!--Device-deviceInfo-const majorVersion: number--><!--Device-deviceInfo-const majorVersion: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## manufacture

```TypeScript
const manufacture: string
```

设备厂家名称。

**起始版本：** 6

<!--Device-deviceInfo-const manufacture: string--><!--Device-deviceInfo-const manufacture: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## marketName

```TypeScript
const marketName: string
```

外部产品系列。

示例：<!--RP2-->Mate XX<!--RP2End-->

**起始版本：** 6

<!--Device-deviceInfo-const marketName: string--><!--Device-deviceInfo-const marketName: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## osFullName

```TypeScript
const osFullName: string
```

系统版本，版本格式<!--RP12-->OpenHarmony-x.x.x.x,x为数值。<!--RP12End-->

示例：<!--RP10-->OpenHarmony-x.x.x.x，其中x表示数字占位符。<!--RP10End-->

如需获取版本号各段数值，建议直接使用majorVersion、seniorVersion、featureVersion、buildVersion字段，可提升效率，不建议解析osFullName获取。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-deviceInfo-const osFullName: string--><!--Device-deviceInfo-const osFullName: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## osReleaseType

```TypeScript
const osReleaseType: string
```

系统的发布类型，取值为：

- Canary：面向特定开发者发布的早期预览版本，不承诺API稳定性。

- Beta：面向开发者公开发布的Beta版本，不承诺API稳定性。

- Release：面向开发者公开发布的正式版本，承诺API稳定性。

示例：<!--RP9-->Canary/Beta/Release<!--RP9End-->

**起始版本：** 6

<!--Device-deviceInfo-const osReleaseType: string--><!--Device-deviceInfo-const osReleaseType: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## performanceClass

```TypeScript
const performanceClass: PerformanceClassLevel
```

描述设备能力等级，基于CPU、内存、存储读写性能和屏幕分辨率等因素综合评估。

**起始版本：** 19

<!--Device-deviceInfo-const performanceClass: PerformanceClassLevel--><!--Device-deviceInfo-const performanceClass: PerformanceClassLevel-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## productModel

```TypeScript
const productModel: string
```

认证型号。

示例：<!--RP4-->TAS-AL00<!--RP4End-->

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-deviceInfo-const productModel: string--><!--Device-deviceInfo-const productModel: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## productModelAlias

```TypeScript
const productModelAlias: string
```

认证型号别名。

示例：TAS-AL00

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-deviceInfo-const productModelAlias: string--><!--Device-deviceInfo-const productModelAlias: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## productSeries

```TypeScript
const productSeries: string
```

产品系列。

示例：<!--RP3-->TAS<!--RP3End-->

**起始版本：** 6

<!--Device-deviceInfo-const productSeries: string--><!--Device-deviceInfo-const productSeries: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## sdkApiVersion

```TypeScript
const sdkApiVersion: number
```

系统软件API版本。

示例：12

**起始版本：** 6

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-deviceInfo-const sdkApiVersion: number--><!--Device-deviceInfo-const sdkApiVersion: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## sdkMinorApiVersion

```TypeScript
const sdkMinorApiVersion: number
```

系统软件Minor API版本。从API 26 版本开始，系统API版本格式：sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion。

26.0.0

示例：0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-deviceInfo-const sdkMinorApiVersion: number--><!--Device-deviceInfo-const sdkMinorApiVersion: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## sdkPatchApiVersion

```TypeScript
const sdkPatchApiVersion: number
```

系统软件Patch API版本。从API 26 版本开始，系统API版本格式：sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion。

26.0.0

示例：0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-deviceInfo-const sdkPatchApiVersion: number--><!--Device-deviceInfo-const sdkPatchApiVersion: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## securityPatchTag

```TypeScript
const securityPatchTag: string
```

安全补丁级别。

示例：<!--RP7-->2021/01/01<!--RP7End-->

**起始版本：** 6

<!--Device-deviceInfo-const securityPatchTag: string--><!--Device-deviceInfo-const securityPatchTag: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## seniorVersion

```TypeScript
const seniorVersion: number
```

Senior版本号，随局部架构、重大特性增加，值为osFullName中的第二位数值，建议直接使用deviceInfo.seniorVersion获取，可提升效率，不建议开发者自主解析osFullName获取。

示例：0

**起始版本：** 6

<!--Device-deviceInfo-const seniorVersion: number--><!--Device-deviceInfo-const seniorVersion: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## serial

```TypeScript
const serial: string
```

设备序列号SN(Serial Number)。

**说明：**可作为设备唯一识别码。

ohos.permission.sec.ACCESS_UDID(该权限只允许系统应用及企业定制应用申请)

示例：序列号随设备差异

**起始版本：** 6

**需要权限：** ohos.permission.sec.ACCESS_UDID

<!--Device-deviceInfo-const serial: string--><!--Device-deviceInfo-const serial: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## softwareModel

```TypeScript
const softwareModel: string
```

内部软件子型号。

示例：<!--RP5-->TAS-AL00<!--RP5End-->

**起始版本：** 6

<!--Device-deviceInfo-const softwareModel: string--><!--Device-deviceInfo-const softwareModel: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## udid

```TypeScript
const udid: string
```

设备UDID。

**说明：**数据长度为65字节。可作为设备唯一识别码。

ohos.permission.sec.ACCESS_UDID(该权限只允许系统应用及企业类应用申请)

示例：9D6AABD147XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXE5536412

**起始版本：** 7

**需要权限：** ohos.permission.sec.ACCESS_UDID

<!--Device-deviceInfo-const udid: string--><!--Device-deviceInfo-const udid: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## versionId

```TypeScript
const versionId: string
```

版本ID。由deviceType、manufacture、brand、productSeries、osFullName、productModel、softwareModel、sdkApiVersion、incrementalVersion、buildType拼接组成。如果需要获取其中的某个字段值，建议直接使用对应的字段（如deviceType、manufacture等），可提升效率，不建议解析versionId获取。

**起始版本：** 6

<!--Device-deviceInfo-const versionId: string--><!--Device-deviceInfo-const versionId: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

