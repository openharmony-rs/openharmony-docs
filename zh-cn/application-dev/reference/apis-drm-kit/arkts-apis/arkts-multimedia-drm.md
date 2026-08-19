# @ohos.multimedia.drm(Defines the DRM capability.)

DRM（Digital Rights Management）框架组件支持音视频媒体业务数字版权管理功能的开发。开发者可以调用系统提供的DRM插件，完成以下功能： - DRM证书管理：生成证书请求、设置证书响应，实现对证书Provision（下载）功能。 - DRM媒体密钥管理：生成媒体密钥请求、设置媒体密钥响应、管理离线媒体密钥功能。 - DRM节目授权：支持DRM插件根据媒体密钥权限对DRM节目授权。 - DRM节目解密：支持媒体播放功能的解密调用，实现对DRM节目的解密。

**起始版本：** 23

<!--Device-unnamed-declare namespace drm--><!--Device-unnamed-declare namespace drm-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

## 导入模块

```TypeScript
import { drm } from '@kit.DrmKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createMediaKeySystem(Defines the DRM capability.)](arkts-drm-drm-createmediakeysystem-f.md) | Creates a MediaKeySystem instance. |
| [createMediaKeySystem(Defines the DRM capability.)](arkts-drm-drm-createmediakeysystem-f.md) | Creates a MediaKeySystem instance. |
| [getMediaKeySystemUuid(Defines the DRM capability.)](arkts-drm-drm-getmediakeysystemuuid-f.md) | Get a MediaKeySystem's UUID. |
| [getMediaKeySystems(Defines the DRM capability.)](arkts-drm-drm-getmediakeysystems-f.md) | Get all media key systems supported. |
| [isMediaKeySystemSupported(Defines the DRM capability.)](arkts-drm-drm-ismediakeysystemsupported-f.md) | Judge whether a system that specifies name, mimetype and content protection level is supported. |
| [isMediaKeySystemSupported(Defines the DRM capability.)](arkts-drm-drm-ismediakeysystemsupported-f.md) | Judge whether a system that specifies name, mimetype is supported. |
| [isMediaKeySystemSupported(Defines the DRM capability.)](arkts-drm-drm-ismediakeysystemsupported-f.md) | Judge whether a system that specifies name is supported. |

### 接口

| 名称 | 说明 |
| --- | --- |
| [EventInfo(Defines the DRM capability.)](arkts-drm-drm-eventinfo-i.md) | 事件信息。 |
| [KeysInfo(Defines the DRM capability.)](arkts-drm-drm-keysinfo-i.md) | 媒体密钥中密钥信息。 |
| [MediaKeyRequest(Defines the DRM capability.)](arkts-drm-drm-mediakeyrequest-i.md) | 媒体密钥请求参数。 |
| [MediaKeySession(Defines the DRM capability.)](arkts-drm-drm-mediakeysession-i.md) | 支持媒体密钥管理。在调用MediaKeySession方法之前，必须使用 [createMediaKeySession](arkts-drm-drm-mediakeysystem-i.md#createmediakeysession) 获取一个MediaKeySession实例。 |
| [MediaKeyStatus(Defines the DRM capability.)](arkts-drm-drm-mediakeystatus-i.md) | 媒体密钥状态。 |
| [MediaKeySystem(Defines the DRM capability.)](arkts-drm-drm-mediakeysystem-i.md) | 支持MediaKeySystem实例管理、设备证书申请与处理、会话创建、离线媒体密钥管理、获取DRM度量记录、设备属性等。在调用MediaKeySystem方法之前，必须使用 [createMediaKeySystem](arkts-drm-drm-createmediakeysystem-f.md)创建一个MediaKeySystem实例。 |
| [MediaKeySystemDescription(Defines the DRM capability.)](arkts-drm-drm-mediakeysystemdescription-i.md) | 插件信息。 |
| [MediaKeySystemInfo(Defines the DRM capability.)](arkts-drm-drm-mediakeysysteminfo-i.md) | 加密媒体内容的DRM信息。 |
| [OptionsData(Defines the DRM capability.)](arkts-drm-drm-optionsdata-i.md) | 设备证书请求的可选数据。 |
| [ProvisionRequest(Defines the DRM capability.)](arkts-drm-drm-provisionrequest-i.md) | 设备证书请求。 |
| [StatisticKeyValue(Defines the DRM capability.)](arkts-drm-drm-statistickeyvalue-i.md) | 度量记录。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CertificateStatus(Defines the DRM capability.)](arkts-drm-drm-certificatestatus-e.md) | 枚举，设备证书状态。 |
| [ContentProtectionLevel(Defines the DRM capability.)](arkts-drm-drm-contentprotectionlevel-e.md) | 枚举，内容保护级别。 |
| [DrmErrorCode(Defines the DRM capability.)](arkts-drm-drm-drmerrorcode-e.md) | 枚举，错误码。 |
| [MediaKeyRequestType(Defines the DRM capability.)](arkts-drm-drm-mediakeyrequesttype-e.md) | 枚举，媒体密钥请求类型。 |
| [MediaKeyType(Defines the DRM capability.)](arkts-drm-drm-mediakeytype-e.md) | 枚举，媒体密钥类型。 |
| [OfflineMediaKeyStatus(Defines the DRM capability.)](arkts-drm-drm-offlinemediakeystatus-e.md) | 枚举，离线媒体密钥状态。 |
| [PreDefinedConfigName(Defines the DRM capability.)](arkts-drm-drm-predefinedconfigname-e.md) | 枚举，预定义的配置属性。 |

