# MediaKeySystem

支持MediaKeySystem实例管理、设备证书申请与处理、会话创建、离线媒体密钥管理、获取DRM度量记录、设备属性等。在调用MediaKeySystem方法之前，必须使用 [createMediaKeySystem](arkts-drm-drm-createmediakeysystem-f.md#createMediaKeySystem)创建一个MediaKeySystem实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-drm-interface MediaKeySystem--><!--Device-drm-interface MediaKeySystem-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

## clearOfflineMediaKeys

```TypeScript
clearOfflineMediaKeys(mediaKeyId: Uint8Array): void
```

删除指定媒体密钥标识的离线媒体密钥。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-clearOfflineMediaKeys(mediaKeyId: Uint8Array): void--><!--Device-MediaKeySystem-clearOfflineMediaKeys(mediaKeyId: Uint8Array): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaKeyId | Uint8Array | 是 | 离线媒体密钥标识。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed.Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## createMediaKeySession

```TypeScript
createMediaKeySession(level: ContentProtectionLevel): MediaKeySession
```

创建指定内容保护级别的MediaKeySession实例。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-createMediaKeySession(level: ContentProtectionLevel): MediaKeySession--><!--Device-MediaKeySystem-createMediaKeySession(level: ContentProtectionLevel): MediaKeySession-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | [ContentProtectionLevel](arkts-drm-drm-contentprotectionlevel-e.md) | 是 | 内容保护级别。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaKeySession](arkts-drm-drm-mediakeysession-i.md) | MediaKeySession实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700104](../errorcode-drm.md#24700104-mediakeysession数量达到极限) | Meet max MediaKeySession num limit. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.The param level exceeds reasonable range, please use value in ContentProtectionLevel. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## createMediaKeySession

```TypeScript
createMediaKeySession(level: ContentProtectionLevel): MediaKeySession | undefined
```

Create a MediaKeySession instance with level.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySystem-createMediaKeySession(level: ContentProtectionLevel): MediaKeySession | undefined--><!--Device-MediaKeySystem-createMediaKeySession(level: ContentProtectionLevel): MediaKeySession | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| level | [ContentProtectionLevel](arkts-drm-drm-contentprotectionlevel-e.md) | 是 | Used to specify the content protection level. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaKeySession](arkts-drm-drm-mediakeysession-i.md) | A MediaKeySession instance or undefined. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700104](../errorcode-drm.md#24700104-mediakeysession数量达到极限) | Meet max MediaKeySession num limit. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.The param level exceeds reasonable range, please use value in ContentProtectionLevel. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## createMediaKeySession

```TypeScript
createMediaKeySession(): MediaKeySession
```

创建DRM解决方案默认内容保护级别的MediaKeySession实例。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-createMediaKeySession(): MediaKeySession--><!--Device-MediaKeySystem-createMediaKeySession(): MediaKeySession-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaKeySession](arkts-drm-drm-mediakeysession-i.md) | MediaKeySession实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700104](../errorcode-drm.md#24700104-mediakeysession数量达到极限) | Meet max MediaKeySession num limit. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## createMediaKeySession

```TypeScript
createMediaKeySession(): MediaKeySession | undefined
```

Create a MediaKeySession instance.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySystem-createMediaKeySession(): MediaKeySession | undefined--><!--Device-MediaKeySystem-createMediaKeySession(): MediaKeySession | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaKeySession](arkts-drm-drm-mediakeysession-i.md) | A MediaKeySession instance or undefined. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700104](../errorcode-drm.md#24700104-mediakeysession数量达到极限) | Meet max MediaKeySession num limit. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## destroy

```TypeScript
destroy(): void
```

销毁MediaKeySystem实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-destroy(): void--><!--Device-MediaKeySystem-destroy(): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## generateKeySystemRequest

```TypeScript
generateKeySystemRequest(): Promise<ProvisionRequest>
```

生成获取mediaKeySystem设备证书的请求。使用Promise异步回调。 如果设备上已存在设备证书，调用此接口会返回失败。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-generateKeySystemRequest(): Promise<ProvisionRequest>--><!--Device-MediaKeySystem-generateKeySystemRequest(): Promise<ProvisionRequest>-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ProvisionRequest](arkts-drm-drm-provisionrequest-i.md)&gt; | Promise对象，mediaKeySystem设备证书的请求。设备上如果已存在设备证书，会返回失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## getCertificateStatus

```TypeScript
getCertificateStatus(): CertificateStatus
```

获取设备证书状态值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-getCertificateStatus(): CertificateStatus--><!--Device-MediaKeySystem-getCertificateStatus(): CertificateStatus-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CertificateStatus](arkts-drm-drm-certificatestatus-e.md) | 设备证书状态值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## getConfigurationByteArray

```TypeScript
getConfigurationByteArray(configName: string): Uint8Array
```

获取数组类型的配置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-getConfigurationByteArray(configName: string): Uint8Array--><!--Device-MediaKeySystem-getConfigurationByteArray(configName: string): Uint8Array-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configName | string | 是 | 配置属性名，不能为空，属性名参考 [PreDefinedConfigName](arkts-drm-drm-predefinedconfigname-e.md#PreDefinedConfigName)，具体支持的属性名由设备上DRM解决方案决定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 数组类型的配置属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## getConfigurationString

```TypeScript
getConfigurationString(configName: string): string
```

获取字符串类型的配置属性值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-getConfigurationString(configName: string): string--><!--Device-MediaKeySystem-getConfigurationString(configName: string): string-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configName | string | 是 | 配置属性名，不能为空，长度不能超过4096字节。&lt;br&gt;如果参数长度超过4096字节，会抛出错误码401。&lt;br&gt;属性名参考 [PreDefinedConfigName](arkts-drm-drm-predefinedconfigname-e.md#PreDefinedConfigName)，具体支持的属性名由设备上DRM解决方案决定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回字符串类型的配置属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed, the param's length is zero or too big(exceeds 4096 Bytes). |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## getMaxContentProtectionLevel

```TypeScript
getMaxContentProtectionLevel(): ContentProtectionLevel
```

获取当前DRM解决方案支持的最大内容保护级别。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-getMaxContentProtectionLevel(): ContentProtectionLevel--><!--Device-MediaKeySystem-getMaxContentProtectionLevel(): ContentProtectionLevel-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContentProtectionLevel](arkts-drm-drm-contentprotectionlevel-e.md) | 返回设备支持的最大内容保护级别。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## getOfflineMediaKeyIds

```TypeScript
getOfflineMediaKeyIds(): Uint8Array[]
```

获取离线媒体密钥标识列表。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-getOfflineMediaKeyIds(): Uint8Array[]--><!--Device-MediaKeySystem-getOfflineMediaKeyIds(): Uint8Array[]-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array[] | 离线媒体密钥标识列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## getOfflineMediaKeyStatus

```TypeScript
getOfflineMediaKeyStatus(mediaKeyId: Uint8Array): OfflineMediaKeyStatus
```

获取指定离线媒体密钥标识的媒体密钥的状态值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-getOfflineMediaKeyStatus(mediaKeyId: Uint8Array): OfflineMediaKeyStatus--><!--Device-MediaKeySystem-getOfflineMediaKeyStatus(mediaKeyId: Uint8Array): OfflineMediaKeyStatus-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaKeyId | Uint8Array | 是 | 离线媒体密钥标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OfflineMediaKeyStatus](arkts-drm-drm-offlinemediakeystatus-e.md) | 离线媒体密钥状态值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## getStatistics

```TypeScript
getStatistics(): StatisticKeyValue[]
```

获取性能度量记录。其中包括当前会话数、插件版本信息、每个会话最大三次解密耗时、解密次数和解密失败次数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-getStatistics(): StatisticKeyValue[]--><!--Device-MediaKeySystem-getStatistics(): StatisticKeyValue[]-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StatisticKeyValue](arkts-drm-drm-statistickeyvalue-i.md)[] | 度量记录。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## offKeySystemRequired

```TypeScript
offKeySystemRequired(callback?: (eventInfo: EventInfo) => void): void
```

Unregister keySystemRequired events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySystem-offKeySystemRequired(callback?: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySystem-offKeySystemRequired(callback?: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (eventInfo: EventInfo) =&gt; void | 否 | Used to listen for the key system required event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## off_keySystemRequired

```TypeScript
off(type: 'keySystemRequired', callback?: (eventInfo: EventInfo) => void): void
```

注销设备证书请求事件的监听。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-off(type: 'keySystemRequired', callback?: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySystem-off(type: 'keySystemRequired', callback?: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keySystemRequired' | 是 | 监听事件类型，通过 [createMediaKeySystem](arkts-drm-drm-createmediakeysystem-f.md#createMediaKeySystem)成功创建MediaKeySystem实例 后可监听。 |
| callback | (eventInfo: EventInfo) =&gt; void | 否 | 回调函数，返回事件信息。可选参数，不传时注销该事件类型的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## onKeySystemRequired

```TypeScript
onKeySystemRequired(callback: (eventInfo: EventInfo) => void): void
```

Register keySystemRequired events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySystem-onKeySystemRequired(callback: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySystem-onKeySystemRequired(callback: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (eventInfo: EventInfo) =&gt; void | 是 | Used to listen for the key system required event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## on_keySystemRequired

```TypeScript
on(type: 'keySystemRequired', callback: (eventInfo: EventInfo) => void): void
```

监听设备证书请求事件，获取事件信息。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-on(type: 'keySystemRequired', callback: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySystem-on(type: 'keySystemRequired', callback: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keySystemRequired' | 是 | 事件类型，通过 [createMediaKeySystem](arkts-drm-drm-createmediakeysystem-f.md#createMediaKeySystem)成功创建MediaKeySystem实例 后可监听，需要设备证书时触发该事件。 |
| callback | (eventInfo: EventInfo) =&gt; void | 是 | 回调函数，返回事件信息。只要有该事件返回就证明需请求设备证书。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## processKeySystemResponse

```TypeScript
processKeySystemResponse(response: Uint8Array): Promise<void>
```

处理获得的设备证书请求的响应。使用Promise异步回调。 如果设备上已存在设备证书，调用此接口会返回失败。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-processKeySystemResponse(response: Uint8Array): Promise<void>--><!--Device-MediaKeySystem-processKeySystemResponse(response: Uint8Array): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | Uint8Array | 是 | 从DRM服务获取的设备证书响应。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## setConfigurationByteArray

```TypeScript
setConfigurationByteArray(configName: string, value: Uint8Array): void
```

设置数组类型的配置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-setConfigurationByteArray(configName: string, value: Uint8Array): void--><!--Device-MediaKeySystem-setConfigurationByteArray(configName: string, value: Uint8Array): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configName | string | 是 | 配置属性名，不能为空，属性名参考 [PreDefinedConfigName](arkts-drm-drm-predefinedconfigname-e.md#PreDefinedConfigName)，具体支持的属性名由设备上DRM解决方案决定。 |
| value | Uint8Array | 是 | 数组类型的配置属性值，具体属性值由设备上DRM解决方案决定。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## setConfigurationString

```TypeScript
setConfigurationString(configName: string, value: string): void
```

设置字符串类型的配置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySystem-setConfigurationString(configName: string, value: string): void--><!--Device-MediaKeySystem-setConfigurationString(configName: string, value: string): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configName | string | 是 | 配置属性名，不能为空，属性名参考 [PreDefinedConfigName](arkts-drm-drm-predefinedconfigname-e.md#PreDefinedConfigName)，具体支持的属性名由设备上DRM解决方案决定。 |
| value | string | 是 | 配置属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

