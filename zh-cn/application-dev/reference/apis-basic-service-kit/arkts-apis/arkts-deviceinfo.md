# @ohos.deviceInfo

/*
 Copyright (c) 2026 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** -1

<!--Device-unnamed-declare namespace deviceInfo--><!--Device-unnamed-declare namespace deviceInfo-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [apiAvailable](arkts-basicservices-deviceinfo-apiavailable-f.md#apiAvailable) | 检查指定的API版本在当前设备上是否可用。 此方法提供跨不同OpenHarmony/分布式操作系统版本的兼容性检查。它会根据输入格式和API版本范围自动选择合适的版本检查方法。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DeviceTypes](arkts-basicservices-deviceinfo-devicetypes-e.md) | 设备类型枚举值，可用于校验deviceType的返回值。 |
| [PerformanceClassLevel](arkts-basicservices-deviceinfo-performanceclasslevel-e.md) | 表示设备能力定级的枚举。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [ODID](arkts-basicservices-deviceinfo-con.md#ODID) | 开发者匿名设备标识符。 **ODID值会在以下场景重新生成：** 手机恢复出厂设置。 同一设备上同一个开发者(developerId相同)的应用全部卸载后重新安装时。 **ODID生成规则：** 根据签名信息里developerId解析出的groupId生成，developerId规则为groupId.developerId，若无groupId则取整个developerId作为groupId。 同一设备上运行的同一个开发者(developerId相同)的应用，ODID相同。 同一个设备上不同开发者(developerId不同)的应用，ODID不同。 不同设备上同一个开发者(developerId相同)的应用，ODID不同。 不同设备上不同开发者(developerId不同)的应用，ODID不同。 |
| [abiList](arkts-basicservices-deviceinfo-con.md#abiList) | 应用二进制接口（Abi）。 示例：arm64-v8a |
| [bootCount](arkts-basicservices-deviceinfo-con.md#bootCount) | 当前设备重启次数，获取失败时返回-1。 示例：100 |
| [bootloaderVersion](arkts-basicservices-deviceinfo-con.md#bootloaderVersion) | Bootloader版本号，用于标识设备启动引导程序的版本信息。 示例：bootloader |
| [brand](arkts-basicservices-deviceinfo-con.md#brand) | 设备品牌名称。 |
| [buildHost](arkts-basicservices-deviceinfo-con.md#buildHost) | 构建主机。 示例：default |
| [buildRootHash](arkts-basicservices-deviceinfo-con.md#buildRootHash) | 构建版本Hash。 示例：default |
| [buildTime](arkts-basicservices-deviceinfo-con.md#buildTime) | 构建时间。 示例：default |
| [buildType](arkts-basicservices-deviceinfo-con.md#buildType) | 构建类型。 示例：default |
| [buildUser](arkts-basicservices-deviceinfo-con.md#buildUser) | 构建用户。 示例：default |
| [buildVersion](arkts-basicservices-deviceinfo-con.md#buildVersion) | Build版本号，标识编译构建的版本号，值为osFullName中的第四位数值，建议直接使用deviceInfo.buildVersion获取，可提升效率，不建议开发者自主解析osFullName获取。 示例：1 |
| [chipType](arkts-basicservices-deviceinfo-con.md#chipType) | 当前设备CPU芯片型号。 **使用场景**：用于根据芯片型号进行性能适配、设备特性识别、兼容性检查等场景，不同芯片型号可能具有不同的GPU性能、AI加速能力等特性。 示例：xxxxx |
| [deviceColor](arkts-basicservices-deviceinfo-con.md#deviceColor) | 当前设备颜色。如果无法获取，则返回空字符串 示例：gold |
| [deviceType](arkts-basicservices-deviceinfo-con.md#deviceType) | 设备类型。详细请参考[deviceTypes标签](../../../quick-start/module-configuration-file.md#devicetypes标签)。 示例：&lt;!--RP1--&gt;wearable&lt;!--RP1End--&gt; |
| [diskSN](arkts-basicservices-deviceinfo-con.md#diskSN) | 硬盘序列号，该接口在执行期间会拉起临时进程，当系统负载较高时，可能引发阻塞风险。为确保应用主线程的响应性能，建议避免在主线程中调用。设备信息因设备而异且固定不变，可在首次获取后缓存在本地，避免每次使用时重复获取，以提升性能。 |
| [displayVersion](arkts-basicservices-deviceinfo-con.md#displayVersion) | 产品版本。 示例：&lt;!--RP8--&gt;XXX X.X.X.X&lt;!--RP8End--&gt; |
| [distributionOSApiName](arkts-basicservices-deviceinfo-con.md#distributionOSApiName) | 发行版系统api版本名称&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。 &lt;!--RP16-- |
| [distributionOSApiVersion](arkts-basicservices-deviceinfo-con.md#distributionOSApiVersion) | 发行版系统API版本&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。&lt;!--RP15--&gt;&lt;!--RP15End--&gt; 示例：50001 |
| [distributionOSName](arkts-basicservices-deviceinfo-con.md#distributionOSName) | 发行版系统名称&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。 示例：OpenHarmony |
| [distributionOSReleaseType](arkts-basicservices-deviceinfo-con.md#distributionOSReleaseType) | 发行版系统类型&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。 示例：Release |
| [distributionOSVersion](arkts-basicservices-deviceinfo-con.md#distributionOSVersion) | 发行版系统版本号&lt;!--Del--&gt;，由发行方定义&lt;!--DelEnd--&gt;。&lt;!--RP11--&gt;&lt;!--RP11End--&gt; 示例：5.0.0 |
| [featureVersion](arkts-basicservices-deviceinfo-con.md#featureVersion) | Feature版本号，标识规划的新特性版本，值为osFullName中的第三位数值，建议直接使用deviceInfo.featureVersion获取，可提升效率，不建议开发者自主解析osFullName获取。 示例：0 |
| [firstApiVersion](arkts-basicservices-deviceinfo-con.md#firstApiVersion) | 首个版本系统软件API版本。 示例：3 |
| [hardwareModel](arkts-basicservices-deviceinfo-con.md#hardwareModel) | 硬件版本号。 示例：&lt;!--RP6--&gt;TASA00CVN1&lt;!--RP6End--&gt; |
| [hardwareProfile](arkts-basicservices-deviceinfo-con.md#hardwareProfile) | 硬件Profile。 |
| [incrementalVersion](arkts-basicservices-deviceinfo-con.md#incrementalVersion) | 差异版本号，是编译时生成的ohos的版本号。 示例：6.1.1.120 |
| [majorVersion](arkts-basicservices-deviceinfo-con.md#majorVersion) | Major版本号，随主版本更新增加，值为osFullName中的第一位数值，建议直接使用deviceInfo.majorVersion获取，可提升效率，不建议开发者自主解析osFullName获取。 示例：5 |
| [manufacture](arkts-basicservices-deviceinfo-con.md#manufacture) | 设备厂家名称。 |
| [marketName](arkts-basicservices-deviceinfo-con.md#marketName) | 外部产品系列。 示例：&lt;!--RP2--&gt;Mate XX&lt;!--RP2End--&gt; |
| [osFullName](arkts-basicservices-deviceinfo-con.md#osFullName) | 系统版本，版本格式&lt;!--RP12--&gt;OpenHarmony-x.x.x.x，其中x表示数字占位符。&lt;!--RP12End--&gt;如需获取版本号各段数值，建议直接使用majorVersion、seniorVersion、featureVersion、buildVersion字段，可提升效率，不建议解析osFullName获取。 示例：&lt;!--RP10--&gt;OpenHarmony-5.0.0.1&lt;!--RP10End--&gt; |
| [osReleaseType](arkts-basicservices-deviceinfo-con.md#osReleaseType) | 系统的发布类型，取值为： - Canary：面向特定开发者发布的早期预览版本，不承诺API稳定性。 - Beta：面向开发者公开发布的Beta版本，不承诺API稳定性。 - Release：面向开发者公开发布的正式版本，承诺API稳定性。 示例：&lt;!--RP9--&gt;Canary/Beta/Release&lt;!--RP9End--&gt; |
| [performanceClass](arkts-basicservices-deviceinfo-con.md#performanceClass) | 描述设备能力等级，基于CPU、内存、存储读写性能和屏幕分辨率等因素综合评估。 **使用场景**：用于根据设备能力进行性能适配，如调整动画复杂度、选择不同质量的资源、动态控制功能特性等。 示例：0 |
| [productModel](arkts-basicservices-deviceinfo-con.md#productModel) | 认证型号。 示例：&lt;!--RP4--&gt;TAS-AL00&lt;!--RP4End--&gt; |
| [productModelAlias](arkts-basicservices-deviceinfo-con.md#productModelAlias) | 认证型号别名。 示例：TAS-AL00 |
| [productSeries](arkts-basicservices-deviceinfo-con.md#productSeries) | 产品系列。 示例：&lt;!--RP3--&gt;TAS&lt;!--RP3End--&gt; |
| [sdkApiVersion](arkts-basicservices-deviceinfo-con.md#sdkApiVersion) | 系统软件API版本。 示例：12 |
| [sdkMinorApiVersion](arkts-basicservices-deviceinfo-con.md#sdkMinorApiVersion) | 系统软件Minor API版本。从API 26.0.0 版本开始，系统API版本格式：sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion。 26.0.0 示例：0 |
| [sdkPatchApiVersion](arkts-basicservices-deviceinfo-con.md#sdkPatchApiVersion) | 系统软件Patch API版本。从API 26 版本开始，系统API版本格式：sdkApiVersion.sdkMinorApiVersion.sdkPatchApiVersion。 26.0.0 示例：0 |
| [securityPatchTag](arkts-basicservices-deviceinfo-con.md#securityPatchTag) | 安全补丁级别。 示例：&lt;!--RP7--&gt;2021/01/01&lt;!--RP7End--&gt; |
| [seniorVersion](arkts-basicservices-deviceinfo-con.md#seniorVersion) | Senior版本号，随局部架构、重大特性增加，值为osFullName中的第二位数值，建议直接使用deviceInfo.seniorVersion获取，可提升效率，不建议开发者自主解析osFullName获取。 示例：0 |
| [serial](arkts-basicservices-deviceinfo-con.md#serial) | 设备序列号SN(Serial Number)，该接口在执行期间会拉起临时进程，当系统负载较高时，可能引发阻塞风险。为确保应用主线程的响应性能，建议避免在主线程中调用。设备信息因设备而异且固定不变，可在首次获取后缓存在本地，避免每次使用时重复获取，以提升性能。 |
| [softwareModel](arkts-basicservices-deviceinfo-con.md#softwareModel) | 内部软件子型号。 示例：&lt;!--RP5--&gt;TAS-AL00&lt;!--RP5End--&gt; |
| [udid](arkts-basicservices-deviceinfo-con.md#udid) | 设备UDID，该接口在执行期间会拉起临时进程，当系统负载较高时，可能引发阻塞风险。为确保应用主线程的响应性能，建议避免在主线程中调用。设备信息因设备而异且固定不变，可在首次获取后缓存在本地，避免每次使用时重复获取，以提升性能。 |
| [versionId](arkts-basicservices-deviceinfo-con.md#versionId) | 版本ID。由deviceType、manufacture、brand、productSeries、osFullName、productModel、softwareModel、sdkApiVersion、 incrementalVersion、buildType拼接组成。如果需要获取其中的某个字段值，建议直接使用对应的字段（如deviceType、manufacture等），可提升效率，不建议解析versionId获取。 |

