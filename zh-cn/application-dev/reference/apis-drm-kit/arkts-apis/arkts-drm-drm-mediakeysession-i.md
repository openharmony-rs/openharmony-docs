# MediaKeySession

支持媒体密钥管理。在调用MediaKeySession方法之前，必须使用 [createMediaKeySession](arkts-drm-drm-mediakeysystem-i.md#createMediaKeySession) 获取一个MediaKeySession实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-drm-interface MediaKeySession--><!--Device-drm-interface MediaKeySession-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

## checkMediaKeyStatus

```TypeScript
checkMediaKeyStatus(): MediaKeyStatus[]
```

检查当前媒体密钥状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-checkMediaKeyStatus(): MediaKeyStatus[]--><!--Device-MediaKeySession-checkMediaKeyStatus(): MediaKeyStatus[]-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaKeyStatus](arkts-drm-drm-mediakeystatus-i.md)[] | 当前媒体密钥状态值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## clearMediaKeys

```TypeScript
clearMediaKeys(): void
```

清除当前媒体密钥。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-clearMediaKeys(): void--><!--Device-MediaKeySession-clearMediaKeys(): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## destroy

```TypeScript
destroy(): void
```

销毁MediaKeySession实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-destroy(): void--><!--Device-MediaKeySession-destroy(): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## generateMediaKeyRequest

```TypeScript
generateMediaKeyRequest(mimeType: string, initData: Uint8Array, mediaKeyType: int, options?: OptionsData[]): Promise<MediaKeyRequest>
```

生成媒体密钥请求。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-generateMediaKeyRequest(mimeType: string, initData: Uint8Array, mediaKeyType: int, options?: OptionsData[]): Promise<MediaKeyRequest>--><!--Device-MediaKeySession-generateMediaKeyRequest(mimeType: string, initData: Uint8Array, mediaKeyType: int, options?: OptionsData[]): Promise<MediaKeyRequest>-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mimeType | string | 是 | 媒体类型，DRM解决方案名称，可通过 [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md#isMediaKeySystemSupported) 查询。 |
| initData | Uint8Array | 是 | 初始数据，即加密流中的PSSH box中的实际PSSH数据。可通过监听AVPlayer的'mediaKeySystemInfoUpdate'事件（ on('mediaKeySystemInfoUpdate') ）获取DRM信息，从中提取pssh字段生成initData。具体开发流程可参考 [基于AVPlayer播放DRM节目(ArkTS)](../../../media/drm/drm-avplayer-arkts-integration.md)。 |
| mediaKeyType | int | 是 | 媒体密钥类型。取值范围为[0, 1]。0表示在线，1表示离线。&lt;br&gt;传入指定范围外的参数会导致参数校验失败，抛出错误码401。 |
| options | [OptionsData](arkts-drm-drm-optionsdata-i.md)[] | 否 | 可选数据。默认值为空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[MediaKeyRequest](arkts-drm-drm-mediakeyrequest-i.md)&gt; | Promise对象，媒体密钥请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## generateOfflineReleaseRequest

```TypeScript
generateOfflineReleaseRequest(mediaKeyId: Uint8Array): Promise<Uint8Array>
```

生成离线媒体密钥释放请求。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-generateOfflineReleaseRequest(mediaKeyId: Uint8Array): Promise<Uint8Array>--><!--Device-MediaKeySession-generateOfflineReleaseRequest(mediaKeyId: Uint8Array): Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaKeyId | Uint8Array | 是 | 离线媒体密钥标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，设备上的DRM解决方案支持离线媒体密钥释放处理，则返回离线媒体密钥释放请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## getContentProtectionLevel

```TypeScript
getContentProtectionLevel(): ContentProtectionLevel
```

获取当前会话的内容保护级别。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-getContentProtectionLevel(): ContentProtectionLevel--><!--Device-MediaKeySession-getContentProtectionLevel(): ContentProtectionLevel-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContentProtectionLevel](arkts-drm-drm-contentprotectionlevel-e.md) | 返回当前会话内容保护级别。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## offExpirationUpdate

```TypeScript
offExpirationUpdate(callback?: (eventInfo: EventInfo) => void): void
```

Unregister expirationUpdate event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySession-offExpirationUpdate(callback?: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-offExpirationUpdate(callback?: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (eventInfo: EventInfo) =&gt; void | 否 | Used to listen for expiration update event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## offKeyExpired

```TypeScript
offKeyExpired(callback?: (eventInfo: EventInfo) => void): void
```

Unregister keyExpired event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySession-offKeyExpired(callback?: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-offKeyExpired(callback?: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (eventInfo: EventInfo) =&gt; void | 否 | Used to listen for the key required event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## offKeyRequired

```TypeScript
offKeyRequired(callback?: (eventInfo: EventInfo) => void): void
```

Unregister keyRequired event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySession-offKeyRequired(callback?: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-offKeyRequired(callback?: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (eventInfo: EventInfo) =&gt; void | 否 | used to listen for the key required event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## offKeysChange

```TypeScript
offKeysChange(callback?: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void
```

Unregister keysChange event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySession-offKeysChange(callback?: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void--><!--Device-MediaKeySession-offKeysChange(callback?: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (keyInfo: KeysInfo[], newKeyAvailable: boolean) =&gt; void | 否 | Used to listen for keys change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## offVendorDefined

```TypeScript
offVendorDefined(callback?: (eventInfo: EventInfo) => void): void
```

Unregister vendorDefined event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySession-offVendorDefined(callback?: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-offVendorDefined(callback?: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (eventInfo: EventInfo) =&gt; void | 否 | Used to listen for the vendor defined event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## off_expirationUpdate

```TypeScript
off(type: 'expirationUpdate', callback?: (eventInfo: EventInfo) => void): void
```

注销过期更新事件监听。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-off(type: 'expirationUpdate', callback?: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-off(type: 'expirationUpdate', callback?: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'expirationUpdate' | 是 | 监听事件类型，固定为'expirationUpdate'。 |
| callback | (eventInfo: EventInfo) =&gt; void | 否 | 回调函数，返回事件信息。可选参数，不传时注销该事件类型的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## off_keyExpired

```TypeScript
off(type: 'keyExpired', callback?: (eventInfo: EventInfo) => void): void
```

注销密钥过期事件监听。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-off(type: 'keyExpired', callback?: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-off(type: 'keyExpired', callback?: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyExpired' | 是 | 监听事件类型，固定为'keyExpired'。 |
| callback | (eventInfo: EventInfo) =&gt; void | 否 | 回调函数，返回事件信息。可选参数，不传时注销该事件类型的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## off_keyRequired

```TypeScript
off(type: 'keyRequired', callback?: (eventInfo: EventInfo) => void): void
```

注销密钥请求事件监听。使用callback异步回调。 该接口用于注销已在on('keyRequired')中注册的监听，当播放DRM节目需要获取媒体密钥时触发的事件。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-off(type: 'keyRequired', callback?: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-off(type: 'keyRequired', callback?: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyRequired' | 是 | 监听事件类型，固定为'keyRequired'。 |
| callback | (eventInfo: EventInfo) =&gt; void | 否 | 回调函数，返回事件信息。可选参数，不传时注销该事件类型的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## off_keysChange

```TypeScript
off(type: 'keysChange', callback?: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void
```

注销密钥变化事件监听。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-off(type: 'keysChange', callback?: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void--><!--Device-MediaKeySession-off(type: 'keysChange', callback?: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keysChange' | 是 | 监听事件类型，固定为'keysChange'。 |
| callback | (keyInfo: KeysInfo[], newKeyAvailable: boolean) =&gt; void | 否 | 回调函数，返回事件信息，包含密钥标识和密钥状态描述的列表及密钥是否可用。&lt;br&gt;可选参数，不传时注销该事件类型的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## off_vendorDefined

```TypeScript
off(type: 'vendorDefined', callback?: (eventInfo: EventInfo) => void): void
```

注销DRM解决方案自定义事件监听。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-off(type: 'vendorDefined', callback?: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-off(type: 'vendorDefined', callback?: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'vendorDefined' | 是 | 监听事件，固定为'vendorDefined'。 |
| callback | (eventInfo: EventInfo) =&gt; void | 否 | 回调函数，返回事件信息。可选参数，不传时注销该事件类型的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## onExpirationUpdate

```TypeScript
onExpirationUpdate(callback: (eventInfo: EventInfo) => void): void
```

Register expirationUpdate event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySession-onExpirationUpdate(callback: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-onExpirationUpdate(callback: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (eventInfo: EventInfo) =&gt; void | 是 | Used to listen for expiration update event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## onKeyExpired

```TypeScript
onKeyExpired(callback: (eventInfo: EventInfo) => void): void
```

Register keyExpired event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySession-onKeyExpired(callback: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-onKeyExpired(callback: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (eventInfo: EventInfo) =&gt; void | 是 | Used to listen for the key required event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## onKeyRequired

```TypeScript
onKeyRequired(callback: (eventInfo: EventInfo) => void): void
```

Register keyRequired event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySession-onKeyRequired(callback: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-onKeyRequired(callback: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (eventInfo: EventInfo) =&gt; void | 是 | used to listen for the key required event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## onKeysChange

```TypeScript
onKeysChange(callback: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void
```

Register keysChange event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySession-onKeysChange(callback: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void--><!--Device-MediaKeySession-onKeysChange(callback: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (keyInfo: KeysInfo[], newKeyAvailable: boolean) =&gt; void | 是 | Used to listen for keys change event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## onVendorDefined

```TypeScript
onVendorDefined(callback: (eventInfo: EventInfo) => void): void
```

Register vendorDefined event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MediaKeySession-onVendorDefined(callback: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-onVendorDefined(callback: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (eventInfo: EventInfo) =&gt; void | 是 | Used to listen for the vendor defined event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## on_expirationUpdate

```TypeScript
on(type: 'expirationUpdate', callback: (eventInfo: EventInfo) => void): void
```

监听密钥过期更新事件。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-on(type: 'expirationUpdate', callback: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-on(type: 'expirationUpdate', callback: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'expirationUpdate' | 是 | 监听事件类型，固定为'expirationUpdate'。密钥过期更新时触发。 |
| callback | (eventInfo: EventInfo) =&gt; void | 是 | 回调函数，返回事件信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## on_keyExpired

```TypeScript
on(type: 'keyExpired', callback: (eventInfo: EventInfo) => void): void
```

监听密钥过期事件。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-on(type: 'keyExpired', callback: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-on(type: 'keyExpired', callback: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyExpired' | 是 | 监听事件类型，固定为'keyExpired'。密钥过期时触发。 |
| callback | (eventInfo: EventInfo) =&gt; void | 是 | 回调函数，返回事件信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## on_keyRequired

```TypeScript
on(type: 'keyRequired', callback: (eventInfo: EventInfo) => void): void
```

监听密钥请求事件。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-on(type: 'keyRequired', callback: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-on(type: 'keyRequired', callback: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyRequired' | 是 | 事件类型，固定为'keyRequired'，当播放DRM节目需要获取媒体密钥时触发。 |
| callback | (eventInfo: EventInfo) =&gt; void | 是 | 回调函数，返回事件信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## on_keysChange

```TypeScript
on(type: 'keysChange', callback: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void
```

监听密钥变化事件。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-on(type: 'keysChange', callback: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void--><!--Device-MediaKeySession-on(type: 'keysChange', callback: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keysChange' | 是 | 监听事件类型，固定为'keysChange'。密钥变化时触发。 |
| callback | (keyInfo: KeysInfo[], newKeyAvailable: boolean) =&gt; void | 是 | 回调函数，返回事件信息，包含密钥标识和密钥状态描述的列表及密钥是否可用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## on_vendorDefined

```TypeScript
on(type: 'vendorDefined', callback: (eventInfo: EventInfo) => void): void
```

监听DRM解决方案自定义事件。使用callback异步回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-on(type: 'vendorDefined', callback: (eventInfo: EventInfo) => void): void--><!--Device-MediaKeySession-on(type: 'vendorDefined', callback: (eventInfo: EventInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'vendorDefined' | 是 | 监听事件，固定为'vendorDefined'。自定义事件发生时触发。 |
| callback | (eventInfo: EventInfo) =&gt; void | 是 | 回调函数，返回事件信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## processMediaKeyResponse

```TypeScript
processMediaKeyResponse(response: Uint8Array): Promise<Uint8Array>
```

处理媒体密钥响应。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-processMediaKeyResponse(response: Uint8Array): Promise<Uint8Array>--><!--Device-MediaKeySession-processMediaKeyResponse(response: Uint8Array): Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | Uint8Array | 是 | 媒体密钥响应。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，媒体密钥标识。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## processOfflineReleaseResponse

```TypeScript
processOfflineReleaseResponse(mediaKeyId: Uint8Array, response: Uint8Array): Promise<void>
```

处理离线媒体密钥释放响应。使用Promise异步回调。 如果设备上的DRM解决方案不支持离线媒体密钥释放，将抛出错误码24700101。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-processOfflineReleaseResponse(mediaKeyId: Uint8Array, response: Uint8Array): Promise<void>--><!--Device-MediaKeySession-processOfflineReleaseResponse(mediaKeyId: Uint8Array, response: Uint8Array): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaKeyId | Uint8Array | 是 | 离线媒体密钥标识。 |
| response | Uint8Array | 是 | 离线媒体密钥释放响应。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## requireSecureDecoderModule

```TypeScript
requireSecureDecoderModule(mimeType: string): boolean
```

是否需要安全解码。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-requireSecureDecoderModule(mimeType: string): boolean--><!--Device-MediaKeySession-requireSecureDecoderModule(mimeType: string): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mimeType | string | 是 | 媒体类型，支持的媒体类型取决于DRM解决方案，可通过 [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md#isMediaKeySystemSupported) 查询。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否需要安全解码，true表示需要安全解码，false表示不需要安全解码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## restoreOfflineMediaKeys

```TypeScript
restoreOfflineMediaKeys(mediaKeyId: Uint8Array): Promise<void>
```

恢复离线媒体密钥。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaKeySession-restoreOfflineMediaKeys(mediaKeyId: Uint8Array): Promise<void>--><!--Device-MediaKeySession-restoreOfflineMediaKeys(mediaKeyId: Uint8Array): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaKeyId | Uint8Array | 是 | 离线媒体密钥标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

