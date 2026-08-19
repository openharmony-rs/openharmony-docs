# isMediaKeySystemSupported

## 导入模块

```TypeScript
import { drm } from '@kit.DrmKit';
```

## isMediaKeySystemSupported

```TypeScript
function isMediaKeySystemSupported(name: string, mimeType: string, level: ContentProtectionLevel): boolean
```

Judge whether a system that specifies name, mimetype and content protection level is supported.

**起始版本：** 23

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-drm-function isMediaKeySystemSupported(name: string, mimeType: string, level: ContentProtectionLevel): boolean--><!--Device-drm-function isMediaKeySystemSupported(name: string, mimeType: string, level: ContentProtectionLevel): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | Used to point a Digital Right Management solution. |
| mimeType | string | 是 | Used to specifies the media type. |
| level | [ContentProtectionLevel](arkts-drm-drm-contentprotectionlevel-e.md) | 是 | Used to specifies the ContentProtectionLevel. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether these conditions will be met. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

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

Judge whether a system that specifies name, mimetype is supported.

**起始版本：** 23

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-drm-function isMediaKeySystemSupported(name: string, mimeType: string): boolean--><!--Device-drm-function isMediaKeySystemSupported(name: string, mimeType: string): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | Used to point a Digital Right Management solution. |
| mimeType | string | 是 | Used to specifies the media type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether these conditions will be met. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

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

Judge whether a system that specifies name is supported.

**起始版本：** 23

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-drm-function isMediaKeySystemSupported(name: string): boolean--><!--Device-drm-function isMediaKeySystemSupported(name: string): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | Used to point a Digital Right Management solution. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether these conditions will be met. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed, the param name's length is zero or too big(exceeds 4096 Bytes). |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let supported: boolean = drm.isMediaKeySystemSupported('com.clearplay.drm');
console.info("isMediaKeySystemSupported: ", supported);
```

