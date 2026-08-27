# createMediaKeySystem

## 导入模块

```TypeScript
import { drm } from '@kit.DrmKit';
```

## createMediaKeySystem

```TypeScript
function createMediaKeySystem(name: string): MediaKeySystem
```

创建MediaKeySystem实例。最多可以创建64个MediaKeySystem实例。超过上限时，会抛出错误码24700103。建议及时调用[destroy](arkts-drm-drm-mediakeysystem-i.md#destroy)接口释放不再使用的MediaKeySystem实例。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | DRM解决方案名称。可通过[getMediaKeySystems](arkts-drm-drm-getmediakeysystems-f.md)接口获取设备支持的DRM解决方案名称，如"com.clearplay.drm"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaKeySystem](arkts-drm-drm-mediakeysystem-i.md) | MediaKeySystem实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possibly because: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700103](../errorcode-drm.md#24700103-mediakeysystem数量达到极限) | Meet max MediaKeySystem num limit. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';
// name为DRM解决方案名称，可通过drm.getMediaKeySystems接口获取设备支持的DRM解决方案名称，如"com.clearplay.drm"。
let name = 'com.clearplay.drm';
let mediaKeySystem: drm.MediaKeySystem = drm.createMediaKeySystem(name);
console.info(`createMediaKeySystem success, name: ${name}`);
```
