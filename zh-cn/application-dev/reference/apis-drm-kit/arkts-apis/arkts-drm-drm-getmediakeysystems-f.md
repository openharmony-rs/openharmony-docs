# getMediaKeySystems

## 导入模块

```TypeScript
import { drm } from '@kit.DrmKit';
```

## getMediaKeySystems

```TypeScript
function getMediaKeySystems(): MediaKeySystemDescription[]
```

获取设备支持的插件信息列表。

**起始版本：** 12

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Drm.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaKeySystemDescription](arkts-drm-drm-mediakeysystemdescription-i.md)[] | 设备支持的插件信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [24700101](../errorcode-drm.md#24700101-未知错误) | All unknown errors. |
| [24700201](../errorcode-drm.md#24700201-服务异常) | Fatal service error, for example, service died. |

**示例**

```TypeScript
import { drm } from '@kit.DrmKit';

let description: drm.MediaKeySystemDescription[] = drm.getMediaKeySystems();
// 验证返回结果，description为插件信息列表，包含插件名称和唯一标识。
if (description.length > 0) {
  console.info(`getMediaKeySystems success, count: ${description.length}`);
  for (let i = 0; i < description.length; i++) {
    console.info(`name: ${description[i].name}, uuid: ${description[i].uuid}`);
  }
} else {
  console.info('No DRM system available');
}
```
