# @ohos.multimedia.drm

DRM（Digital Rights Management）框架组件支持音视频媒体业务数字版权管理功能的开发。开发者可以调用系统提供的DRM插件，完成以下功能：

- DRM证书管理：生成证书请求、设置证书响应，实现对证书Provision（下载）功能。  
- DRM媒体密钥管理：生成媒体密钥请求、设置媒体密钥响应、管理离线媒体密钥功能。  
- DRM节目授权：支持DRM插件根据媒体密钥权限对DRM节目授权。  
- DRM节目解密：支持媒体播放功能的解密调用，实现对DRM节目的解密。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Drm.Core

## 导入模块

```TypeScript
import { drm } from '@kit.DrmKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createMediaKeySystem](arkts-drm-drm-createmediakeysystem-f.md) | 创建MediaKeySystem实例。最多可以创建64个MediaKeySystem实例。超过上限时，会抛出错误码24700103。建议及时调用[destroy](arkts-drm-drm-mediakeysystem-i.md#destroy)接口释放不再使用的MediaKeySystem实例。 |
| [getMediaKeySystems](arkts-drm-drm-getmediakeysystems-f.md) | 获取设备支持的插件信息列表。 |
| [getMediaKeySystemUuid](arkts-drm-drm-getmediakeysystemuuid-f.md) | 获取DRM解决方案支持的DRM内容保护系统唯一标识。 |
| [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md) | 判断设备是否支持指定的DRM解决方案、媒体类型及内容保护级别。 |
| [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md) | 判断设备是否支持指定的DRM解决方案及媒体类型。 |
| [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md) | 判断设备是否支持指定的DRM解决方案。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [EventInfo](arkts-drm-drm-eventinfo-i.md) | 事件信息。 |
| [KeysInfo](arkts-drm-drm-keysinfo-i.md) | 媒体密钥中密钥信息。 |
| [MediaKeyRequest](arkts-drm-drm-mediakeyrequest-i.md) | 媒体密钥请求参数。 |
| [MediaKeySession](arkts-drm-drm-mediakeysession-i.md) | 支持媒体密钥管理。在调用MediaKeySession方法之前，必须使用[createMediaKeySession](arkts-drm-drm-mediakeysystem-i.md#createmediakeysession)获取一个MediaKeySession实例。 |
| [MediaKeyStatus](arkts-drm-drm-mediakeystatus-i.md) | 媒体密钥状态。 |
| [MediaKeySystem](arkts-drm-drm-mediakeysystem-i.md) | 支持MediaKeySystem实例管理、设备证书申请与处理、会话创建、离线媒体密钥管理、获取DRM度量记录、设备属性等。在调用MediaKeySystem方法之前，必须使用[createMediaKeySystem](arkts-drm-drm-createmediakeysystem-f.md)创建一个MediaKeySystem实例。 |
| [MediaKeySystemDescription](arkts-drm-drm-mediakeysystemdescription-i.md) | 插件信息。 |
| [MediaKeySystemInfo](arkts-drm-drm-mediakeysysteminfo-i.md) | 加密媒体内容的DRM信息。 |
| [OptionsData](arkts-drm-drm-optionsdata-i.md) | 设备证书请求的可选数据。 |
| [ProvisionRequest](arkts-drm-drm-provisionrequest-i.md) | 设备证书请求。 |
| [StatisticKeyValue](arkts-drm-drm-statistickeyvalue-i.md) | 度量记录。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CertificateStatus](arkts-drm-drm-certificatestatus-e.md) | 枚举，设备证书状态。 |
| [ContentProtectionLevel](arkts-drm-drm-contentprotectionlevel-e.md) | 枚举，内容保护级别。 |
| [DrmErrorCode](arkts-drm-drm-drmerrorcode-e.md) | 枚举，错误码。 |
| [MediaKeyRequestType](arkts-drm-drm-mediakeyrequesttype-e.md) | 枚举，媒体密钥请求类型。 |
| [MediaKeyType](arkts-drm-drm-mediakeytype-e.md) | 枚举，媒体密钥类型。 |
| [OfflineMediaKeyStatus](arkts-drm-drm-offlinemediakeystatus-e.md) | 枚举，离线媒体密钥状态。 |
| [PreDefinedConfigName](arkts-drm-drm-predefinedconfigname-e.md) | 枚举，预定义的配置属性。 |
