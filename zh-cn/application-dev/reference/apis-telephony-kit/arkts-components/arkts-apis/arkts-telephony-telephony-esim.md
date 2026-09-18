# @ohos.telephony.esim(eSIM卡管理)

eSIM卡管理模块提供了eSIM卡管理的基础能力，包括获取指定卡槽是否支持eSIM功能，如果支持则允许用户添加单个配置文件。

**起始版本：** 18

**系统能力：** SystemCapability.Telephony.CoreService.Esim

## 导入模块

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addProfile](arkts-telephony-esim-addprofile-f.md) | 通过该接口拉起下载界面，允许用户添加单个配置文件。使用Promise异步回调。 |
| [isSupported](arkts-telephony-esim-issupported-f.md) | 获取指定卡槽是否支持eSIM功能。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [cancelSession](arkts-telephony-esim-cancelsession-f-sys.md) | 取消会话。使用Promise异步回调。 |
| [deleteProfile](arkts-telephony-esim-deleteprofile-f-sys.md) | 删除配置文件。使用Promise异步回调。 |
| [downloadProfile](arkts-telephony-esim-downloadprofile-f-sys.md) | 下载配置文件。使用Promise异步回调。 |
| [getContractInfo](arkts-telephony-esim-getcontractinfo-f-sys.md) | 获取开通eSIM需要的，加密的esim id等信息。 |
| [getDefaultSmdpAddress](arkts-telephony-esim-getdefaultsmdpaddress-f-sys.md) | 获取存储在eUICC中的默认SM-DP+地址。使用Promise异步回调。 |
| [getDownloadableProfileMetadata](arkts-telephony-esim-getdownloadableprofilemetadata-f-sys.md) | 填充可下载配置文件的元数据。使用Promise异步回调。 |
| [getDownloadableProfiles](arkts-telephony-esim-getdownloadableprofiles-f-sys.md) | 获取可用的可下载配置文件列表。使用Promise异步回调。 |
| [getEid](arkts-telephony-esim-geteid-f-sys.md) | 获取指定卡槽标识eUICC硬件的EID(Equipment Identifier，Embedded SIM识别码)。 |
| [getEsimFreeStorage](arkts-telephony-esim-getesimfreestorage-f-sys.md) | 通过该接口获取eUICC硬件的剩余存储空间。使用Promise异步回调。 |
| [getEuiccInfo](arkts-telephony-esim-geteuiccinfo-f-sys.md) | 获取eUICC信息。使用Promise异步回调。 |
| [getEuiccProfileInfoList](arkts-telephony-esim-geteuiccprofileinfolist-f-sys.md) | 获取配置文件信息列表。使用Promise异步回调。 |
| [getOsuStatus](arkts-telephony-esim-getosustatus-f-sys.md) | 获取指定卡槽操作系统升级的状态。使用Promise异步回调。 |
| [getSupportedPkids](arkts-telephony-esim-getsupportedpkids-f-sys.md) | 获取手机支持的公钥ID信息。 |
| [reserveProfilesForFactoryRestore](arkts-telephony-esim-reserveprofilesforfactoryrestore-f-sys.md) | 恢复出厂设置，并保留profiles。使用Promise异步回调。 |
| [resetMemory](arkts-telephony-esim-resetmemory-f-sys.md) | 清除所有特定配置文件并重置eUICC。使用Promise异步回调。 |
| [setDefaultSmdpAddress](arkts-telephony-esim-setdefaultsmdpaddress-f-sys.md) | 设置或更新eUICC中存储的默认SM-DP+地址。使用Promise异步回调。 |
| [setProfileNickname](arkts-telephony-esim-setprofilenickname-f-sys.md) | 设置给定配置文件的昵称。使用Promise异步回调。 |
| [startOsu](arkts-telephony-esim-startosu-f-sys.md) | 如果指定卡槽的操作系统不是最新的，则执行操作系统升级。使用Promise异步回调。 |
| [switchToProfile](arkts-telephony-esim-switchtoprofile-f-sys.md) | 切换到(启用)给定的配置文件。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [DownloadableProfile](arkts-telephony-esim-downloadableprofile-i.md) | 可下载的配置文件。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessRule](arkts-telephony-esim-accessrule-i-sys.md) | 访问规则。 |
| [ContractRequestData](arkts-telephony-esim-contractrequestdata-i-sys.md) | 加密需要的信息。 |
| [DownloadConfiguration](arkts-telephony-esim-downloadconfiguration-i-sys.md) | 下载过程中的属性配置。 |
| [DownloadProfileResult](arkts-telephony-esim-downloadprofileresult-i-sys.md) | 下载配置文件的结果。 |
| [EuiccInfo](arkts-telephony-esim-euiccinfo-i-sys.md) | euicc信息。 |
| [EuiccProfile](arkts-telephony-esim-euiccprofile-i-sys.md) | 配置文件信息。 |
| [GetDownloadableProfileMetadataResult](arkts-telephony-esim-getdownloadableprofilemetadataresult-i-sys.md) | 获取可下载配置文件的元数据。 |
| [GetDownloadableProfilesResult](arkts-telephony-esim-getdownloadableprofilesresult-i-sys.md) | 获取默认可下载配置文件的列表。 |
| [GetEuiccProfileInfoListResult](arkts-telephony-esim-geteuiccprofileinfolistresult-i-sys.md) | 获取配置文件信息列表。 |
| [OperatorId](arkts-telephony-esim-operatorid-i-sys.md) | 获取eUICC芯片/设备的相关信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CancelReason](arkts-telephony-esim-cancelreason-e-sys.md) | 取消会话的原因。 |
| [OsuStatus](arkts-telephony-esim-osustatus-e-sys.md) | 操作系统升级状态。 |
| [PolicyRules](arkts-telephony-esim-policyrules-e-sys.md) | 配置文件的策略规则。 |
| [ProfileClass](arkts-telephony-esim-profileclass-e-sys.md) | 配置文件类。 |
| [ProfileState](arkts-telephony-esim-profilestate-e-sys.md) | 配置文件状态。 |
| [ResetOption](arkts-telephony-esim-resetoption-e-sys.md) | 重置状态。 |
| [ResultCode](arkts-telephony-esim-resultcode-e-sys.md) | 结果码。 |
| [SolvableErrors](arkts-telephony-esim-solvableerrors-e-sys.md) | 可解决错误码。 |
<!--DelEnd-->
