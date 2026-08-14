# isHdHapticSupported

## isHdHapticSupported

```TypeScript
function isHdHapticSupported(): boolean
```

查询当前设备是否支持高清振动。 适用于在触发高清振动前确认设备是否支持，避免在不支持的设备上调用VibrateFromFile或VibrateFromPattern类型振动导致振动效果不佳或返回错误码801。返回true表示设备支持高清振动，可使用 VibrateFromFile和VibrateFromPattern类型触发振动；返回false表示不支持，使用自定义振动类型将返回错误码801或效果不佳。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-vibrator-function isHdHapticSupported(): boolean--><!--Device-vibrator-function isHdHapticSupported(): boolean-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持高清振动。true表示支持高清振动，可使用VibrateFromFile和VibrateFromPattern类型；false表示不支持，使用自定义振动类型可能返回错误码801或效果不佳。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14600101](../errorcode-vibrator.md#14600101-操作设备失败) | Device operation failed. |

## 示例

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 查询是否支持高清振动
  let ret = vibrator.isHdHapticSupported();
  console.info(`The query result is ${ret}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

