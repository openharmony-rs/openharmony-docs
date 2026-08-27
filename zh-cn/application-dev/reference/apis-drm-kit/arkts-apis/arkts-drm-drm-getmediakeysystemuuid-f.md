# getMediaKeySystemUuid

## 导入模块

```TypeScript
import { drm } from '@kit.DrmKit';
```

## getMediaKeySystemUuid

```TypeScript
function getMediaKeySystemUuid(name: string): string
```

获取DRM解决方案支持的DRM内容保护系统唯一标识。

**起始版本：** 12

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | DRM解决方案名称。可通过[getMediaKeySystems](arkts-drm-drm-getmediakeysystems-f.md)接口获取设备支持的DRM解决方案名称，如"com.clearplay.drm"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | DRM内容保护系统的唯一标识。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed.Possibly because:  1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let uuid: string = drm.getMediaKeySystemUuid('com.clearplay.drm');
console.info("getMediaKeySystemUuid: ", uuid);
```
