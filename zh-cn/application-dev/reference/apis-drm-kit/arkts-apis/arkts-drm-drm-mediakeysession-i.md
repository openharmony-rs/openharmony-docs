# MediaKeySession

支持媒体密钥管理。在调用MediaKeySession方法之前，必须使用 [createMediaKeySession](arkts-drm-drm-mediakeysystem-i.md#createmediakeysession) 获取一个MediaKeySession实例。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Drm.Core

## 导入模块

```TypeScript
import { drm } from '@kit.DrmKit';
```

## checkMediaKeyStatus

```TypeScript
checkMediaKeyStatus(): MediaKeyStatus[]
```

检查当前媒体密钥状态。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaKeyStatus](arkts-drm-drm-mediakeystatus-i.md)[] | 当前媒体密钥状态值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
let keyStatus: drm.MediaKeyStatus[] =  mediaKeySession.checkMediaKeyStatus();
```

## clearMediaKeys

```TypeScript
clearMediaKeys(): void
```

清除当前媒体密钥。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem("com.clearplay.drm");
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
// mediaKeyResponse是从DRM服务获取的媒体密钥响应，按实际值填入。
let mediaKeyResponse = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.processMediaKeyResponse(mediaKeyResponse).then((mediaKeyId: Uint8Array) => {
  console.info('processMediaKeyResponse:' + mediaKeyId);
});
mediaKeySession.clearMediaKeys();
```

## destroy

```TypeScript
destroy(): void
```

销毁MediaKeySession实例。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
mediaKeySession.destroy();
```

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
mediaKeySystem.destroy();
```

## generateMediaKeyRequest

```TypeScript
generateMediaKeyRequest(mimeType: string, initData: Uint8Array, mediaKeyType: number, options?: OptionsData[]): Promise<MediaKeyRequest>
```

生成媒体密钥请求。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mimeType | string | 是 | 媒体类型，DRM解决方案名称，可通过 [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md) 查询。 |
| initData | Uint8Array | 是 | 初始数据，即加密流中的PSSH box中的实际PSSH数据。可通过监听AVPlayer的'mediaKeySystemInfoUpdate'事件（ on('mediaKeySystemInfoUpdate') ）获取DRM信息，从中提取pssh字段生成initData。具体开发流程可参考 [基于AVPlayer播放DRM节目(ArkTS)](../../../media/drm/drm-avplayer-arkts-integration.md)。 |
| mediaKeyType | number | 是 | 媒体密钥类型。取值范围为[0, 1]。0表示在线，1表示离线。传入指定范围外的参数会导致参数校验失败，抛出错误码401。 |
| options | [OptionsData](arkts-drm-drm-optionsdata-i.md)[] | 否 | 可选数据。默认值为空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[MediaKeyRequest](arkts-drm-drm-mediakeyrequest-i.md)&gt; | Promise对象，媒体密钥请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [401](../../errorcode-universal.md#401-参数检查失败) |  |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
// pssh数据为版权保护系统描述头，封装在加密码流中，mp4文件中位于pssh box、dash码流中位于mpd及mp4的pssh box、hls+ts的码流位于m3u8及每个ts片段中，请按实际值传入。
let uint8pssh = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.generateMediaKeyRequest('video/avc', uint8pssh, drm.MediaKeyType.MEDIA_KEY_TYPE_ONLINE).then((mediaKeyRequest: drm.MediaKeyRequest) =>{
  console.info('generateMediaKeyRequest' + mediaKeyRequest);
});
```

## generateOfflineReleaseRequest

```TypeScript
generateOfflineReleaseRequest(mediaKeyId: Uint8Array): Promise<Uint8Array>
```

生成离线媒体密钥释放请求。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaKeyId | Uint8Array | 是 | 离线媒体密钥标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Uint8Array&gt; | Promise对象，设备上的DRM解决方案支持离线媒体密钥释放处理，则返回离线媒体密钥释放请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem("com.clearplay.drm");
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
// mediaKeyId是processMediaKeyResponse或getOfflineMediaKeyIds接口返回的媒体密钥标识，请按实际值传入。
let mediaKeyId = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.generateOfflineReleaseRequest(mediaKeyId).then((offlineReleaseRequest: Uint8Array) => {
  console.info('generateOfflineReleaseRequest:' + offlineReleaseRequest);
});
```

## getContentProtectionLevel

```TypeScript
getContentProtectionLevel(): ContentProtectionLevel
```

获取当前会话的内容保护级别。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ContentProtectionLevel](arkts-drm-drm-contentprotectionlevel-e.md) | 返回当前会话内容保护级别。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem('com.clearplay.drm');
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
let contentProtectionLevel: drm.ContentProtectionLevel = mediaKeySession.getContentProtectionLevel();
console.info(`contentProtectionLevel: ${contentProtectionLevel}`);
```

## off('keyRequired')

```TypeScript
off(type: 'keyRequired', callback?: (eventInfo: EventInfo) => void): void
```

注销密钥请求事件监听。使用callback异步回调。该接口用于注销已在on('keyRequired')中注册的监听，当播放DRM节目需要获取媒体密钥时触发的事件。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

## off('keyExpired')

```TypeScript
off(type: 'keyExpired', callback?: (eventInfo: EventInfo) => void): void
```

注销密钥过期事件监听。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

## off('vendorDefined')

```TypeScript
off(type: 'vendorDefined', callback?: (eventInfo: EventInfo) => void): void
```

注销DRM解决方案自定义事件监听。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

## off('expirationUpdate')

```TypeScript
off(type: 'expirationUpdate', callback?: (eventInfo: EventInfo) => void): void
```

注销过期更新事件监听。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

## off('keysChange')

```TypeScript
off(type: 'keysChange', callback?: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void
```

注销密钥变化事件监听。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keysChange' | 是 | 监听事件类型，固定为'keysChange'。 |
| callback | (keyInfo: KeysInfo[], newKeyAvailable: boolean) =&gt; void | 否 | 回调函数，返回事件信息，包含密钥标识和密钥状态描述的列表及密钥是否可用。可选参数，不传时注销该事件类型的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

## on('keyRequired')

```TypeScript
on(type: 'keyRequired', callback: (eventInfo: EventInfo) => void): void
```

监听密钥请求事件。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

## on('keyExpired')

```TypeScript
on(type: 'keyExpired', callback: (eventInfo: EventInfo) => void): void
```

监听密钥过期事件。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

## on('vendorDefined')

```TypeScript
on(type: 'vendorDefined', callback: (eventInfo: EventInfo) => void): void
```

监听DRM解决方案自定义事件。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

## on('expirationUpdate')

```TypeScript
on(type: 'expirationUpdate', callback: (eventInfo: EventInfo) => void): void
```

监听密钥过期更新事件。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

## on('keysChange')

```TypeScript
on(type: 'keysChange', callback: (keyInfo: KeysInfo[], newKeyAvailable: boolean) => void): void
```

监听密钥变化事件。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

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

## processMediaKeyResponse

```TypeScript
processMediaKeyResponse(response: Uint8Array): Promise<Uint8Array>
```

处理媒体密钥响应。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | Uint8Array | 是 | 媒体密钥响应。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Uint8Array&gt; | Promise对象，媒体密钥标识。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem("com.clearplay.drm");
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
// mediaKeyResponse是从DRM服务获取的媒体密钥响应，按实际值填入。
let mediaKeyResponse = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.processMediaKeyResponse(mediaKeyResponse).then((mediaKeyId: Uint8Array) => {
  console.info('processMediaKeyResponse:' + mediaKeyId);
});
```

## processOfflineReleaseResponse

```TypeScript
processOfflineReleaseResponse(mediaKeyId: Uint8Array, response: Uint8Array): Promise<void>
```

处理离线媒体密钥释放响应。使用Promise异步回调。如果设备上的DRM解决方案不支持离线媒体密钥释放，将抛出错误码24700101。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaKeyId | Uint8Array | 是 | 离线媒体密钥标识。 |
| response | Uint8Array | 是 | 离线媒体密钥释放响应。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem("com.clearplay.drm");
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
// mediaKeyId是processMediaKeyResponse或getOfflineMediaKeyIds接口返回的媒体密钥标识，请按实际长度申请内存。
let mediaKeyId = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.generateOfflineReleaseRequest(mediaKeyId).then((offlineReleaseRequest: Uint8Array) => {
  console.info('generateOfflineReleaseRequest:' + offlineReleaseRequest);
});
// offlineReleaseResponse是从DRM服务获取的离线媒体密钥释放响应，请按实际长度申请内存。
let offlineReleaseResponse = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.processOfflineReleaseResponse(mediaKeyId, offlineReleaseResponse).then(() => {
  console.info('processOfflineReleaseResponse');
});
```

## requireSecureDecoderModule

```TypeScript
requireSecureDecoderModule(mimeType: string): boolean
```

是否需要安全解码。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mimeType | string | 是 | 媒体类型，支持的媒体类型取决于DRM解决方案，可通过 [isMediaKeySystemSupported](arkts-drm-drm-ismediakeysystemsupported-f.md) 查询。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否需要安全解码，true表示需要安全解码，false表示不需要安全解码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem("com.clearplay.drm");
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
let status: boolean = mediaKeySession.requireSecureDecoderModule('video/avc');
```

## restoreOfflineMediaKeys

```TypeScript
restoreOfflineMediaKeys(mediaKeyId: Uint8Array): Promise<void>
```

恢复离线媒体密钥。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaKeyId | Uint8Array | 是 | 离线媒体密钥标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified or too many parameters. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem("com.clearplay.drm");
let mediaKeySession: drm.MediaKeySession = mediaKeySystem.createMediaKeySession();
// mediaKeyId是processMediaKeyResponse或getOfflineMediaKeyIds接口返回的媒体密钥标识，请按实际数据传入。
let mediaKeyId = new Uint8Array([0x00, 0x00, 0x00, 0x00]);
mediaKeySession.restoreOfflineMediaKeys(mediaKeyId).then(() => {
  console.info("restoreOfflineMediaKeys");
});
```
