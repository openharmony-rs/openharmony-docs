# removeFusionFence（系统接口）

## 导入模块

```TypeScript
```

## removeFusionFence

```TypeScript
function removeFusionFence(identifier: string): Promise<void>
```

删除一个融合围栏，并取消订阅该围栏事件。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| identifier | string | 是 | 融合围栏唯一标识。必须与addFusionFence传入的identifier相同才能成功删除围栏。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.removeFusionFence} due to limited device. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301602](../errorcode-geoLocationManager.md#3301602-地理围栏id错误导致删除围栏失败) | Failed to delete a fusion fence due to an incorrect identifier. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  // 必须与addFusionFence传入的identifier相同才能成功删除围栏
  let identifier = "123456789";
  await geoLocationManager.removeFusionFence(identifier).then(() => {
    // 围栏删除成功
    console.info("removeFusionFence success");
  }).catch((error : BusinessError) => {
    console.error("removeFusionFence: BusinessError=" + JSON.stringify(error));
  });
} catch(error) {
  console.error("removeFusionFence: error=" + JSON.stringify(error));
}
```
