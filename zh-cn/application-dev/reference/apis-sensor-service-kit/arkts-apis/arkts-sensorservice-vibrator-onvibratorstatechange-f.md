# onVibratorStateChange

## 导入模块

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## onVibratorStateChange

```TypeScript
function onVibratorStateChange(callback: Callback<VibratorStatusEvent>): void
```

Register a callback function to be called when a vibrator plugin or unplug event occurs.

**起始版本：** 23

<!--Device-vibrator-function onVibratorStateChange(callback: Callback<VibratorStatusEvent>): void--><!--Device-vibrator-function onVibratorStateChange(callback: Callback<VibratorStatusEvent>): void-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[VibratorStatusEvent](arkts-sensorservice-vibrator-vibratorstatusevent-i.md)&gt; | 是 | The callback function to be executed when <br> the event is triggered. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14600101](../errorcode-vibrator.md#14600101-操作设备失败) | Device operation failed. |

**示例**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 回调函数 
const vibratorStateChangeCallback = (data: vibrator.VibratorStatusEvent) => {
  console.info('vibrator state callback info:', JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  // 订阅 vibratorStateChange事件
  vibrator.onVibratorStateChange(vibratorStateChangeCallback);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

