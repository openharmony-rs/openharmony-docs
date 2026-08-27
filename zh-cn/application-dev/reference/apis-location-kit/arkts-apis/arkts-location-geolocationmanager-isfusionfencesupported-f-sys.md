# isFusionFenceSupported（系统接口）

## 导入模块

```TypeScript
```

## isFusionFenceSupported

```TypeScript
function isFusionFenceSupported(): boolean
```

判断系统是否支持融合围栏能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true：支持融合围栏能力。 false：不支持融合围栏能力。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let isFusionFenceSupported = geoLocationManager.isFusionFenceSupported();
} catch (err) {
  console.error("errCode:" + err.code + ", message:"  + err.message);
}
```
