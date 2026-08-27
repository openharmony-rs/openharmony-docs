# @ohos.telephony.esim(eSIM卡管理)

eSIM卡管理模块提供了eSIM卡管理的基础能力，包括获取指定卡槽是否支持eSIM功能，如果支持则允许用户添加单个配置文件。

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addProfile(eSIM卡管理)](arkts-telephony-esim-addprofile-f.md) | 通过该接口拉起下载界面，允许用户添加单个配置文件。使用Promise异步回调。 |
| [isSupported(eSIM卡管理)](arkts-telephony-esim-issupported-f.md) | 获取指定卡槽是否支持eSIM功能。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [cancelSession(eSIM卡管理)](arkts-telephony-esim-cancelsession-f-sys.md) | 取消会话。使用Promise异步回调。 |
| [deleteProfile(eSIM卡管理)](arkts-telephony-esim-deleteprofile-f-sys.md) | 删除配置文件。使用Promise异步回调。 |
| [downloadProfile(eSIM卡管理)](arkts-telephony-esim-downloadprofile-f-sys.md) | 下载配置文件。使用Promise异步回调。 |
| [getContractInfo(eSIM卡管理)](arkts-telephony-esim-getcontractinfo-f-sys.md) | 获取开通eSIM需要的，加密的esim id等信息。 |
| [getDefaultSmdpAddress(eSIM卡管理)](arkts-telephony-esim-getdefaultsmdpaddress-f-sys.md) | 获取存储在eUICC中的默认SM-DP+地址。使用Promise异步回调。 |
| [getDownloadableProfileMetadata(eSIM卡管理)](arkts-telephony-esim-getdownloadableprofilemetadata-f-sys.md) | 填充可下载配置文件的元数据。使用Promise异步回调。 |
| [getDownloadableProfiles(eSIM卡管理)](arkts-telephony-esim-getdownloadableprofiles-f-sys.md) | 获取可用的可下载配置文件列表。使用Promise异步回调。 |
| [getEid(eSIM卡管理)](arkts-telephony-esim-geteid-f-sys.md) | 获取指定卡槽标识eUICC硬件的EID(Equipment Identifier，Embedded SIM识别码)。 |
| [getEsimFreeStorage(eSIM卡管理)](arkts-telephony-esim-getesimfreestorage-f-sys.md) | 通过该接口获取eUICC硬件的剩余存储空间。使用Promise异步回调。 |
| [getEuiccInfo(eSIM卡管理)](arkts-telephony-esim-geteuiccinfo-f-sys.md) | 获取eUICC信息。使用Promise异步回调。 |
| [getEuiccProfileInfoList(eSIM卡管理)](arkts-telephony-esim-geteuiccprofileinfolist-f-sys.md) | 获取配置文件信息列表。使用Promise异步回调。 |
| [getOsuStatus(eSIM卡管理)](arkts-telephony-esim-getosustatus-f-sys.md) | 获取指定卡槽操作系统升级的状态。使用Promise异步回调。 |
| [getSupportedPkids(eSIM卡管理)](arkts-telephony-esim-getsupportedpkids-f-sys.md) | 获取手机支持的公钥ID信息。 |
| [reserveProfilesForFactoryRestore(eSIM卡管理)](arkts-telephony-esim-reserveprofilesforfactoryrestore-f-sys.md) | 恢复出厂设置，并保留profiles。使用Promise异步回调。 |
| [resetMemory(eSIM卡管理)](arkts-telephony-esim-resetmemory-f-sys.md) | 清除所有特定配置文件并重置eUICC。使用Promise异步回调。 |
| [setDefaultSmdpAddress(eSIM卡管理)](arkts-telephony-esim-setdefaultsmdpaddress-f-sys.md) | 设置或更新eUICC中存储的默认SM-DP+地址。使用Promise异步回调。 |
| [setProfileNickname(eSIM卡管理)](arkts-telephony-esim-setprofilenickname-f-sys.md) | 设置给定配置文件的昵称。使用Promise异步回调。 |
| [startOsu(eSIM卡管理)](arkts-telephony-esim-startosu-f-sys.md) | 如果指定卡槽的操作系统不是最新的，则执行操作系统升级。使用Promise异步回调。 |
| [switchToProfile(eSIM卡管理)](arkts-telephony-esim-switchtoprofile-f-sys.md) | 切换到(启用)给定的配置文件。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [DownloadableProfile(eSIM卡管理)](arkts-telephony-esim-downloadableprofile-i.md) | 可下载的配置文件。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessRule(eSIM卡管理)](arkts-telephony-esim-accessrule-i-sys.md) | 访问规则。@interface AccessRule |
| [ContractRequestData(eSIM卡管理)](arkts-telephony-esim-contractrequestdata-i-sys.md) | 加密需要的信息。 |
| [DownloadConfiguration(eSIM卡管理)](arkts-telephony-esim-downloadconfiguration-i-sys.md) | 下载过程中的属性配置。 |
| [DownloadProfileResult(eSIM卡管理)](arkts-telephony-esim-downloadprofileresult-i-sys.md) | 下载配置文件的结果。 |
| [EuiccInfo(eSIM卡管理)](arkts-telephony-esim-euiccinfo-i-sys.md) | euicc信息。 |
| [EuiccProfile(eSIM卡管理)](arkts-telephony-esim-euiccprofile-i-sys.md) | 配置文件信息。 |
| [GetDownloadableProfileMetadataResult(eSIM卡管理)](arkts-telephony-esim-getdownloadableprofilemetadataresult-i-sys.md) | 获取可下载配置文件的元数据。 |
| [GetDownloadableProfilesResult(eSIM卡管理)](arkts-telephony-esim-getdownloadableprofilesresult-i-sys.md) | 获取默认可下载配置文件的列表。 |
| [GetEuiccProfileInfoListResult(eSIM卡管理)](arkts-telephony-esim-geteuiccprofileinfolistresult-i-sys.md) | 获取配置文件信息列表。 |
| [OperatorId(eSIM卡管理)](arkts-telephony-esim-operatorid-i-sys.md) | 获取eUICC芯片/设备的相关信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CancelReason(eSIM卡管理)](arkts-telephony-esim-cancelreason-e-sys.md) | 取消会话的原因。 |
| [OsuStatus(eSIM卡管理)](arkts-telephony-esim-osustatus-e-sys.md) | 操作系统升级状态。 |
| [PolicyRules(eSIM卡管理)](arkts-telephony-esim-policyrules-e-sys.md) | 配置文件的策略规则。 |
| [ProfileClass(eSIM卡管理)](arkts-telephony-esim-profileclass-e-sys.md) | 配置文件类。 |
| [ProfileState(eSIM卡管理)](arkts-telephony-esim-profilestate-e-sys.md) | 配置文件状态。 |
| [ResetOption(eSIM卡管理)](arkts-telephony-esim-resetoption-e-sys.md) | 重置状态。 |
| [ResultCode(eSIM卡管理)](arkts-telephony-esim-resultcode-e-sys.md) | 结果码。 |
| [SolvableErrors(eSIM卡管理)](arkts-telephony-esim-solvableerrors-e-sys.md) | 可解决错误码。 |
<!--DelEnd-->
