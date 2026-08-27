# isMediaKeySystemSupported

## 导入模块

```TypeScript
import { drm } from '@kit.DrmKit';
```

## isMediaKeySystemSupported

```TypeScript
function isMediaKeySystemSupported(name: string, mimeType: string, level: ContentProtectionLevel): boolean
```

判断设备是否支持指定的DRM解决方案、媒体类型及内容保护级别。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | DRM解决方案名称。可通过[getMediaKeySystems](arkts-drm-drm-getmediakeysystems-f.md)接口获取设备支持的DRM解决方案名称，如"com.clearplay.drm"。 |
| mimeType | string | 是 | 媒体类型，支持的媒体类型取决于DRM解决方案。 |
| level | [ContentProtectionLevel](arkts-drm-drm-contentprotectionlevel-e.md) | 是 | 内容保护级别，用于指定DRM内容的安全保护程度，不同级别对应不同的解密能力和安全要求。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否支持指定的DRM解决方案、媒体类型以及内容保护级别。当name、mimeType和level都支持时返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let supported: boolean = drm.isMediaKeySystemSupported('com.clearplay.drm', 'video/avc', drm.ContentProtectionLevel.CONTENT_PROTECTION_LEVEL_SW_CRYPTO);
console.info("isMediaKeySystemSupported: ", supported);
```


## isMediaKeySystemSupported

```TypeScript
function isMediaKeySystemSupported(name: string, mimeType: string): boolean
```

判断设备是否支持指定的DRM解决方案及媒体类型。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | DRM解决方案名称。从API版本12开始，可通过[getMediaKeySystems](arkts-drm-drm-getmediakeysystems-f.md)接口获取设备支持的DRM解决方案名称，如"com.clearplay.drm"。 |
| mimeType | string | 是 | 媒体类型，支持的媒体类型取决于DRM解决方案，如：video/avc、video/hevc。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否支持指定的DRM解决方案及媒体类型。当name和mimeType都支持时返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let supported: boolean = drm.isMediaKeySystemSupported('com.clearplay.drm', 'video/avc');
console.info("isMediaKeySystemSupported: ", supported);
```


## isMediaKeySystemSupported

```TypeScript
function isMediaKeySystemSupported(name: string): boolean
```

判断设备是否支持指定的DRM解决方案。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | DRM解决方案名称，长度不超过4096字节。可通过[getMediaKeySystems](arkts-drm-drm-getmediakeysystems-f.md)接口获取设备支持的DRM解决方案名称，如"com.clearplay.drm"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否支持指定的DRM解决方案。true表示支持，false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed, the param name's length is zero or too big(exceeds 4096 Bytes). |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let supported: boolean = drm.isMediaKeySystemSupported('com.clearplay.drm');
console.info("isMediaKeySystemSupported: ", supported);
```
