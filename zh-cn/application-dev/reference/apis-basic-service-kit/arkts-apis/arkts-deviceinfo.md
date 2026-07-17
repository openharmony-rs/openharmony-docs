# @ohos.deviceInfo

本模块提供终端设备信息查询，开发者不可配置。

> **说明：**  
>  
> 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  
> hardwareProfile、incrementalVersion、buildType、buildUser、buildHost、buildTime、buildRootHash等参数返回值为default，这些参数会在设备正式商用版本中配置具体值。  
> 本模块接口返回设备常量信息，建议应用只调用一次，不需要频繁调用。

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
| [apiAvailable](arkts-basicservices-deviceinfo-apiavailable-f.md#apiavailable-1) | 检查指定的API版本在当前设备上是否可用。此方法提供跨不同OpenHarmony/分布式操作系统版本的兼容性检查。它会根据输入格式和API版本范围自动选择合适的版本检查方法。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DeviceTypes](arkts-basicservices-deviceinfo-devicetypes-e.md) | 设备类型枚举值，可用于校验deviceType的返回值。 |
| [PerformanceClassLevel](arkts-basicservices-deviceinfo-performanceclasslevel-e.md) | 表示设备能力定级的枚举。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [ODID](arkts-basicservices-deviceinfo-con.md#odid) | 开发者匿名设备标识符。**ODID值会在以下场景重新生成：**手机恢复出厂设置。同一设备上同一个开发者(developerId相同)的应用全部卸载后重新安装时。**ODID生成规则：**根据签名信息里developerId解析出的groupId生成，developerId规则为groupId.developerId，若无groupId则取整个developerId作为groupId。同一设备上运行的同一个开发者(developerId相同)的应用，ODID相同。同一个设备上不同开发者(developerId不同)的应用，ODID不同。不同设备上同一个开发者(developerId相同)的应用，ODID不同。不同设备上不同开发者(developerId不同)的应用，ODID不同。 |
| [abiList](arkts-basicservices-deviceinfo-con.md#abilist) | 应用二进制接口（Abi）。示例：arm64-v8a |
| [bootCount](arkts-basicservices-deviceinfo-con.md#bootcount) | 当前设备重启次数，获取失败时返回-1示例：100 |
| [bootloaderVersion](arkts-basicservices-deviceinfo-con.md#bootloaderversion) | Bootloader版本号。示例：bootloader |
| [brand](arkts-basicservices-deviceinfo-con.md#brand) | 设备品牌名称。示例：HUAWEI |
| [buildHost](arkts-basicservices-deviceinfo-con.md#buildhost) | 构建主机。示例：default |
| [buildRootHash](arkts-basicservices-deviceinfo-con.md#buildroothash) | 构建版本Hash。示例：default |
| [buildTime](arkts-basicservices-deviceinfo-con.md#buildtime) | 构建时间。示例：default |
| [buildType](arkts-basicservices-deviceinfo-con.md#buildtype) | 构建类型。示例：default |
| [buildUser](arkts-basicservices-deviceinfo-con.md#builduser) | 构建用户。示例：default |
| [buildVersion](arkts-basicservices-deviceinfo-con.md#buildversion) | Build版本号，标识编译构建的版本号，值为osFullName中的第四位数值，建议直接使用deviceInfo.buildVersion获取，可提升效率，不建议开发者自主解析osFullName获取。示例：1 |
| [chipType](arkts-basicservices-deviceinfo-con.md#chiptype) | 当前设备CPU芯片型号示例：xxxxx |
| [deviceColor](arkts-basicservices-deviceinfo-con.md#devicecolor) | 当前设备颜色。如果无法获取，则返回空字符串示例：gold |
| [deviceType](arkts-basicservices-deviceinfo-con.md#devicetype) | 设备类型。详细请参考[deviceTypes标签](../../../../quick-start/module-configuration-file.md#devicetypes标签)。示例：&lt;!--RP1--&gt;wearable&lt;!--RP1End--&gt; |
| [diskSN](arkts-basicservices-deviceinfo-con.md#disksn) | 硬盘序列号。**说明** ：该字段只能在2in1设备进行查询，其他设备查询结果为空。ohos.permission.ACCESS_DISK_PHY_INFO示例：2502EM400567 |
| [displayVersion](arkts-basicservices-deviceinfo-con.md#displayversion) | 产品版本。示例：&lt;!--RP8--&gt;XXX X.X.X.X&lt;!--RP8End--&gt; |
| [distributionOSApiName](arkts-basicservices-deviceinfo-con.md#distributionosapiname) | 发行版系统api版本名称&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。 |
| [distributionOSApiVersion](arkts-basicservices-deviceinfo-con.md#distributionosapiversion) | 发行版系统api版本&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。示例：50001 |
| [distributionOSName](arkts-basicservices-deviceinfo-con.md#distributionosname) | 发行版系统名称&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。示例：OpenHarmony |
| [distributionOSReleaseType](arkts-basicservices-deviceinfo-con.md#distributionosreleasetype) | 发行版系统类型&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。示例：Release |
| [distributionOSVersion](arkts-basicservices-deviceinfo-con.md#distributionosversion) | 发行版系统版本号&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。&lt;!--RP11--&gt;&lt;!--RP11End--&gt;示例：5.0.0 |
| [featureVersion](arkts-basicservices-deviceinfo-con.md#featureversion) | Feature版本号，标识规划的新特性版本，值为osFullName中的第三位数值，建议直接使用deviceInfo.featureVersion获取，可提升效率，不建议开发者自主解析osFullName获取。示例：0 |
| [firstApiVersion](arkts-basicservices-deviceinfo-con.md#firstapiversion) | 首个版本系统软件API版本。示例：3 |
| [hardwareModel](arkts-basicservices-deviceinfo-con.md#hardwaremodel) | 硬件版本号。示例：&lt;!--RP6--&gt;TASA00CVN1&lt;!--RP6End--&gt; |
| [hardwareProfile](arkts-basicservices-deviceinfo-con.md#hardwareprofile) | 硬件Profile。 |
| [incrementalVersion](arkts-basicservices-deviceinfo-con.md#incrementalversion) | 差异版本号。示例：default |
| [majorVersion](arkts-basicservices-deviceinfo-con.md#majorversion) | Major版本号，随主版本更新增加，值为osFullName中的第一位数值，建议直接使用deviceInfo.majorVersion获取，可提升效率，不建议开发者自主解析osFullName获取。示例：5 |
| [manufacture](arkts-basicservices-deviceinfo-con.md#manufacture) | 设备厂家名称。示例：HUAWEI |
| [marketName](arkts-basicservices-deviceinfo-con.md#marketname) | 外部产品系列。示例：&lt;!--RP2--&gt;Mate XX&lt;!--RP2End--&gt; |
| [osFullName](arkts-basicservices-deviceinfo-con.md#osfullname) | 系统版本，版本格式&lt;!--RP12--&gt;OpenHarmony-x.x.x.x,x为数值。&lt;!--RP12End--&gt;示例：&lt;!--RP10--&gt;OpenHarmony-x.x.x.x，其中x表示数字占位符。&lt;!--RP10End--&gt;如需获取版本号各段数值，建议直接使用majorVersion、seniorVersion、featureVersion、buildVersion字段，可提升效率，不建议解析osFullName获取。 |
| [osReleaseType](arkts-basicservices-deviceinfo-con.md#osreleasetype) | 系统的发布类型，取值为：- Canary：面向特定开发者发布的早期预览版本，不承诺API稳定性。- Beta：面向开发者公开发布的Beta版本，不承诺API稳定性。- Release：面向开发者公开发布的正式版本，承诺API稳定性。示例：&lt;!--RP9--&gt;Canary/Beta/Release&lt;!--RP9End--&gt; |
| [performanceClass](arkts-basicservices-deviceinfo-con.md#performanceclass) | 描述设备能力等级，基于CPU、内存、存储读写性能和屏幕分辨率等因素综合评估。 |
| [productModel](arkts-basicservices-deviceinfo-con.md#productmodel) | 认证型号。示例：&lt;!--RP4--&gt;TAS-AL00&lt;!--RP4End--&gt; |
| [productModelAlias](arkts-basicservices-deviceinfo-con.md#productmodelalias) | 认证型号别名。示例：TAS-AL00 |
| [productSeries](arkts-basicservices-deviceinfo-con.md#productseries) | 产品系列。示例：&lt;!--RP3--&gt;TAS&lt;!--RP3End--&gt; |
| [sdkApiVersion](arkts-basicservices-deviceinfo-con.md#sdkapiversion) | 系统软件API版本。示例：12 |
| [sdkMinorApiVersion](arkts-basicservices-deviceinfo-con.md#sdkminorapiversion) | 系统软件Minor API版本。**从** API 26 版本开始，系统API版本格式：sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion。26.0.0示例：0 |
| [sdkPatchApiVersion](arkts-basicservices-deviceinfo-con.md#sdkpatchapiversion) | 系统软件Patch API版本。**从** API 26 版本开始，系统API版本格式：sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion。26.0.0示例：0 |
| [securityPatchTag](arkts-basicservices-deviceinfo-con.md#securitypatchtag) | 安全补丁级别。示例：&lt;!--RP7--&gt;2021/01/01&lt;!--RP7End--&gt; |
| [seniorVersion](arkts-basicservices-deviceinfo-con.md#seniorversion) | Senior版本号，随局部架构、重大特性增加，值为osFullName中的第二位数值，建议直接使用deviceInfo.seniorVersion获取，可提升效率，不建议开发者自主解析osFullName获取。示例：0 |
| [serial](arkts-basicservices-deviceinfo-con.md#serial) | 设备序列号SN(Serial Number)。 |
| [softwareModel](arkts-basicservices-deviceinfo-con.md#softwaremodel) | 内部软件子型号。示例：&lt;!--RP5--&gt;TAS-AL00&lt;!--RP5End--&gt; |
| [udid](arkts-basicservices-deviceinfo-con.md#udid) | 设备UDID。 |
| [versionId](arkts-basicservices-deviceinfo-con.md#versionid) | 版本ID。由deviceType、manufacture、brand、productSeries、osFullName、productModel、softwareModel、sdkApiVersion、incrementalVersion、buildType拼接组成。如果需要获取其中的某个字段值，建议直接使用对应的字段（如deviceType、manufacture等），可提升效率，不建议解析versionId获取。示例：wearable/HUAWEI/HUAWEI/TAS/OpenHarmony-5.0.0.1/TAS-AL00/TAS-AL00/12/default/release:nolog |

