# @ohos.deviceInfo

本模块提供终端设备信息查询，开发者不可配置。

> **说明：**
>
> 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 部分参数返回值为default的，会在正式发布的版本中配置。
> 本模块接口返回设备常量信息，建议应用只调用一次，不需要频繁调用。

**起始版本：** 6

**系统能力：** SystemCapability.Startup.SystemInfo

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [apiAvailable](arkts-basicservices-deviceinfo-apiavailable-f.md#apiAvailable-1) | &lt;!--RP13--&gt;<br/><br/>检查指定的API版本在当前设备上是否可用。<br/><br/>此方法提供跨不同OpenHarmony/分布式操作系统版本的兼容性检查。它会根据输入格式和API版本范围自动选择合适的版本检查方法。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DeviceTypes](arkts-basicservices-deviceinfo-devicetypes-e.md) | 设备类型枚举值，可用于校验deviceType的返回值。<br/> |
| [PerformanceClassLevel](arkts-basicservices-deviceinfo-performanceclasslevel-e.md) | 表示设备能力定级的枚举。<br/> |

### 常量

| 名称 | 说明 |
| --- | --- |
| [ODID](arkts-basicservices-deviceinfo-con.md#ODID) | 开发者匿名设备标识符。<br/><br/>**ODID值会在以下场景重新生成**：<br/><br/>手机恢复出厂设置。<br/><br/>同一设备上同一个开发者(developerId相同)的应用全部卸载后重新安装时。<br/><br/>**ODID生成规则**：<br/><br/>根据签名信息里developerId解析出的groupId生成，developerId规则为groupId.developerId，若无groupId则取整个developerId作为groupId。<br/><br/>同一设备上运行的同一个开发者(developerId相同)的应用，ODID相同。<br/><br/>同一个设备上不同开发者(developerId不同)的应用，ODID不同。<br/><br/>不同设备上同一个开发者(developerId相同)的应用，ODID不同。<br/><br/>不同设备上不同开发者(developerId不同)的应用，ODID不同。<br/><br/>**说明**：数据长度为37字节(包含结束符)。<br/><br/>示例：1234a567-XXXX-XXXX-XXXX-XXXXXXXXXXXX<br/> |
| [abiList](arkts-basicservices-deviceinfo-con.md#abiList) | 应用二进制接口（Abi）。<br/><br/>示例：arm64-v8a<br/> |
| [bootCount](arkts-basicservices-deviceinfo-con.md#bootCount) | 当前设备重启次数，获取失败时返回-1<br/><br/>示例：100<br/> |
| [bootloaderVersion](arkts-basicservices-deviceinfo-con.md#bootloaderVersion) | Bootloader版本号。<br/><br/>示例：bootloader<br/> |
| [brand](arkts-basicservices-deviceinfo-con.md#brand) | 设备品牌名称。<br/><br/>示例：HUAWEI<br/> |
| [buildHost](arkts-basicservices-deviceinfo-con.md#buildHost) | 构建主机。<br/><br/>示例：default<br/> |
| [buildRootHash](arkts-basicservices-deviceinfo-con.md#buildRootHash) | 构建版本Hash。<br/><br/>示例：default<br/> |
| [buildTime](arkts-basicservices-deviceinfo-con.md#buildTime) | 构建时间。<br/><br/>示例：default<br/> |
| [buildType](arkts-basicservices-deviceinfo-con.md#buildType) | 构建类型。<br/><br/>示例：default<br/> |
| [buildUser](arkts-basicservices-deviceinfo-con.md#buildUser) | 构建用户。<br/><br/>示例：default<br/> |
| [buildVersion](arkts-basicservices-deviceinfo-con.md#buildVersion) | Build版本号，标识编译构建的版本号，值为osFullName中的第四位数值，建议直接使用deviceInfo.buildVersion获取，可提升效率，不建议开发者自主解析osFullName获取。<br/><br/>示例：1<br/> |
| [chipType](arkts-basicservices-deviceinfo-con.md#chipType) | 当前设备CPU芯片型号<br/><br/>示例：xxxxx<br/> |
| [deviceColor](arkts-basicservices-deviceinfo-con.md#deviceColor) | 当前设备颜色<br/><br/>示例：gold<br/> |
| [deviceType](arkts-basicservices-deviceinfo-con.md#deviceType) | 设备类型。详细请参考[deviceTypes标签](../../../../quick-start/module-configuration-file.md#devicetypes标签)。<br/><br/>示例：&lt;!--RP1--&gt;wearable&lt;!--RP1End--&gt;<br/> |
| [diskSN](arkts-basicservices-deviceinfo-con.md#diskSN) | 硬盘序列号。<br/><br/>**说明** ：该字段只能在2in1设备进行查询，其他设备查询结果为空。<br/><br/>ohos.permission.ACCESS_DISK_PHY_INFO <br/><br/>示例：2502EM400567<br/> |
| [displayVersion](arkts-basicservices-deviceinfo-con.md#displayVersion) | 产品版本。<br/><br/>示例：&lt;!--RP8--&gt;XXX X.X.X.X&lt;!--RP8End--&gt;<br/> |
| [distributionOSApiName](arkts-basicservices-deviceinfo-con.md#distributionOSApiName) | 发行版系统api版本名称&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。<br/> |
| [distributionOSApiVersion](arkts-basicservices-deviceinfo-con.md#distributionOSApiVersion) | 发行版系统api版本&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。<br/><br/>示例：50001<br/> |
| [distributionOSName](arkts-basicservices-deviceinfo-con.md#distributionOSName) | 发行版系统名称&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。<br/><br/>示例：OpenHarmony<br/> |
| [distributionOSReleaseType](arkts-basicservices-deviceinfo-con.md#distributionOSReleaseType) | 发行版系统类型&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。<br/><br/>示例：Release<br/> |
| [distributionOSVersion](arkts-basicservices-deviceinfo-con.md#distributionOSVersion) | 发行版系统版本号&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。&lt;!--RP11--&gt;&lt;!--RP11End--&gt;<br/><br/>示例：5.0.0<br/> |
| [featureVersion](arkts-basicservices-deviceinfo-con.md#featureVersion) | Feature版本号，标识规划的新特性版本，值为osFullName中的第三位数值，建议直接使用deviceInfo.featureVersion获取，可提升效率，不建议开发者自主解析osFullName获取。<br/><br/>示例：0<br/> |
| [firstApiVersion](arkts-basicservices-deviceinfo-con.md#firstApiVersion) | 首个版本系统软件API版本。<br/><br/>示例：3<br/> |
| [hardwareModel](arkts-basicservices-deviceinfo-con.md#hardwareModel) | 硬件版本号。<br/><br/>示例：&lt;!--RP6--&gt;TASA00CVN1&lt;!--RP6End--&gt;<br/> |
| [hardwareProfile](arkts-basicservices-deviceinfo-con.md#hardwareProfile) | 硬件Profile。<br/><br/>**说明**：<br/><br/>从API version 6 开始支持，从API version 9 开始废弃，建议使用[系统能力SystemCapability](../../../../reference/syscap.md)替代。<br/><br/>示例：default<br/> |
| [incrementalVersion](arkts-basicservices-deviceinfo-con.md#incrementalVersion) | 差异版本号。<br/><br/>示例：default<br/> |
| [majorVersion](arkts-basicservices-deviceinfo-con.md#majorVersion) | Major版本号，随主版本更新增加，值为osFullName中的第一位数值，建议直接使用deviceInfo.majorVersion获取，可提升效率，不建议开发者解析osFullName获取。<br/><br/>示例：5<br/> |
| [manufacture](arkts-basicservices-deviceinfo-con.md#manufacture) | 设备厂家名称。<br/><br/>示例：HUAWEI<br/> |
| [marketName](arkts-basicservices-deviceinfo-con.md#marketName) | 外部产品系列。<br/><br/>示例：&lt;!--RP2--&gt;Mate XX&lt;!--RP2End--&gt;<br/> |
| [osFullName](arkts-basicservices-deviceinfo-con.md#osFullName) | 系统版本，版本格式&lt;!--RP12--&gt;OpenHarmony-x.x.x.x,x为数值。&lt;!--RP12End--&gt;<br/><br/>示例：&lt;!--RP10--&gt;Openharmony-5.0.0.1&lt;!--RP10End--&gt;<br/> |
| [osReleaseType](arkts-basicservices-deviceinfo-con.md#osReleaseType) | 系统的发布类型，取值为：<br/><br/>- Canary：面向特定开发者发布的早期预览版本，不承诺API稳定性。<br/><br/>- Beta：面向开发者公开发布的Beta版本，不承诺API稳定性。<br/><br/>- Release：面向开发者公开发布的正式版本，承诺API稳定性。<br/><br/>示例：&lt;!--RP9--&gt;Canary/Beta/Release&lt;!--RP9End--&gt;<br/> |
| [performanceClass](arkts-basicservices-deviceinfo-con.md#performanceClass) | 描述设备能力等级，基于CPU、内存、存储读写性能和屏幕分辨率等因素综合评估。<br/> |
| [productModel](arkts-basicservices-deviceinfo-con.md#productModel) | 认证型号。<br/><br/>示例：&lt;!--RP4--&gt;TAS-AL00&lt;!--RP4End--&gt;<br/> |
| [productModelAlias](arkts-basicservices-deviceinfo-con.md#productModelAlias) | 认证型号别名。<br/><br/>示例：TAS-AL00<br/> |
| [productSeries](arkts-basicservices-deviceinfo-con.md#productSeries) | 产品系列。<br/><br/>示例：&lt;!--RP3--&gt;TAS&lt;!--RP3End--&gt;<br/> |
| [sdkApiVersion](arkts-basicservices-deviceinfo-con.md#sdkApiVersion) | 系统软件API版本。<br/><br/>示例：12<br/> |
| [sdkMinorApiVersion](arkts-basicservices-deviceinfo-con.md#sdkMinorApiVersion) | 系统软件Minor API版本。**从** API 26 版本开始，系统API版本格式：sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion。<br/><br/>26.0.0<br/><br/>示例：0<br/> |
| [sdkPatchApiVersion](arkts-basicservices-deviceinfo-con.md#sdkPatchApiVersion) | 系统软件Patch API版本。**从** API 26 版本开始，系统API版本格式：sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion。<br/><br/>26.0.0<br/><br/>示例：0<br/> |
| [securityPatchTag](arkts-basicservices-deviceinfo-con.md#securityPatchTag) | 安全补丁级别。<br/><br/>示例：&lt;!--RP7--&gt;2021/01/01&lt;!--RP7End--&gt;<br/> |
| [seniorVersion](arkts-basicservices-deviceinfo-con.md#seniorVersion) | Senior版本号，随局部架构、重大特性增加，值为osFullName中的第二位数值，建议直接使用deviceInfo.seniorVersion获取，可提升效率，不建议开发者自主解析osFullName获取。<br/><br/>示例：0<br/> |
| [serial](arkts-basicservices-deviceinfo-con.md#serial) | 设备序列号SN(Serial Number)。<br/><br/>**说明**：可作为设备唯一识别码。<br/><br/>ohos.permission.sec.ACCESS_UDID(该权限只允许系统应用及企业定制应用申请) <br/><br/>示例：序列号随设备差异<br/> |
| [softwareModel](arkts-basicservices-deviceinfo-con.md#softwareModel) | 内部软件子型号。<br/><br/>示例：&lt;!--RP5--&gt;TAS-AL00&lt;!--RP5End--&gt;<br/> |
| [udid](arkts-basicservices-deviceinfo-con.md#udid) | 设备Udid。<br/><br/>**说明**：数据长度为65字节。可作为设备唯一识别码。<br/><br/>ohos.permission.sec.ACCESS_UDID(该权限只允许系统应用及企业类应用申请)<br/><br/>示例：9D6AABD147XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXE5536412<br/> |
| [versionId](arkts-basicservices-deviceinfo-con.md#versionId) | 版本ID。由deviceType、manufacture、brand、productSeries、osFullName、productModel、softwareModel、sdkApiVersion、<br/>incrementalVersion、buildType拼接组成。<br/><br/>示例：wearable/HUAWEI/HUAWEI/TAS/OpenHarmony-5.0.0.1/TAS-AL00/TAS-AL00/12/default/release:nolog<br/> |

