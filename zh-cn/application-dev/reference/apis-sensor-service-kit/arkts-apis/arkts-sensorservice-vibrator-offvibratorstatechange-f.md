# offVibratorStateChange

## offVibratorStateChange

```TypeScript
function offVibratorStateChange(callback?: Callback<VibratorStatusEvent>): void
```

Unregister a callback function for vibrator plugin or unplug events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-vibrator-function offVibratorStateChange(callback?: Callback<VibratorStatusEvent>): void--><!--Device-vibrator-function offVibratorStateChange(callback?: Callback<VibratorStatusEvent>): void-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VibratorStatusEvent](arkts-sensorservice-vibrator-vibratorstatusevent-i.md)&gt; | 否 | The callback function to be removed from the event listener. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14600101](../errorcode-vibrator.md#14600101-操作设备失败) | Device operation failed. |

## 示例

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 回调函数 
const vibratorStateChangeCallback = (data: vibrator.VibratorStatusEvent) => {
  console.info('vibrator state callback info:', JSON.stringify(data));
}
// 使用try catch对可能出现的异常进行捕获
try {
  // 取消订阅 vibratorStateChange事件
  vibrator.offVibratorStateChange('vibratorStateChange', vibratorStateChangeCallback);
  // 取消订阅所有 vibratorStateChange事件
  // vibrator.offVibratorStateChange
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

