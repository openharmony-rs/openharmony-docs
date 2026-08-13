# @ohos.multimedia.drm(Defines the DRM capability.)

/*
 Copyright (C) 2023 Huawei Device Co., Ltd.
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


**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace drm--><!--Device-unnamed-declare namespace drm-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createMediaKeySystem](arkts-drm-drm-createmediakeysystem-f.md#createMediaKeySystem) | Creates a MediaKeySystem instance. |
| [createMediaKeySystem](arkts-drm-drm-createmediakeysystem-f.md#createMediaKeySystem) | Creates a MediaKeySystem instance. |
| [getMediaKeySystemUuid](arkts-drm-drm-getmediakeysystemuuid-f.md#getMediaKeySystemUuid) | Get a MediaKeySystem's UUID. |
| [getMediaKeySystems](arkts-drm-drm-getmediakeysystems-f.md#getMediaKeySystems) | Get all media key systems supported. |
| [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md#isMediaKeySystemSupported) | Judge whether a system that specifies name, mimetype and content protection level is supported. |
| [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md#isMediaKeySystemSupported) | Judge whether a system that specifies name, mimetype is supported. |
| [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md#isMediaKeySystemSupported) | Judge whether a system that specifies name is supported. |

### 接口

| 名称 | 说明 |
| --- | --- |
| [EventInfo](arkts-drm-drm-eventinfo-i.md) | 事件信息。 |
| [KeysInfo](arkts-drm-drm-keysinfo-i.md) | 媒体密钥中密钥信息。 |
| [MediaKeyRequest](arkts-drm-drm-mediakeyrequest-i.md) | 媒体密钥请求参数。 |
| [MediaKeySession](arkts-drm-drm-mediakeysession-i.md) | 支持媒体密钥管理。在调用MediaKeySession方法之前，必须使用 [createMediaKeySession](arkts-drm-drm-mediakeysystem-i.md#createMediaKeySession) 获取一个MediaKeySession实例。 |
| [MediaKeyStatus](arkts-drm-drm-mediakeystatus-i.md) | 媒体密钥状态。 |
| [MediaKeySystem](arkts-drm-drm-mediakeysystem-i.md) | 支持MediaKeySystem实例管理、设备证书申请与处理、会话创建、离线媒体密钥管理、获取DRM度量记录、设备属性等。在调用MediaKeySystem方法之前，必须使用 [createMediaKeySystem](arkts-drm-drm-createmediakeysystem-f.md#createMediaKeySystem)创建一个MediaKeySystem实例。 |
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

