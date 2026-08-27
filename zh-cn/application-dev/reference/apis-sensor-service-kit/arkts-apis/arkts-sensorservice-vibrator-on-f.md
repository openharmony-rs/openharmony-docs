# on

## 导入模块

```TypeScript
```

## on('vibratorStateChange')

```TypeScript
function on(type: 'vibratorStateChange', callback: Callback<VibratorStatusEvent>): void
```

注册马达上线或下线事件的回调函数。当马达设备上线或下线时触发回调。 当开发者需要实时感知马达设备的上下线状态变化时使用此接口。适用于分布式多设备场景中动态获取马达设备信息，以便在马达上线时及时触发振动或在下线时停止振动。注册成功后，当马达设备上线或下线时，系统将回调 VibratorStatusEvent对象，包含设备ID、马达数量、上下线状态等信息。回调中获取的deviceId可用于 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md) 和[stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md)等接口指定目标设备。 注册回调后，需在合适的时机调用 vibrator.off注销回调，避免内存泄 露。同一type重复注册同一callback不会覆盖，需先off再on。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'vibratorStateChange' | 是 | 监听类型，该值固定为vibratorStateChange，表示马达上下线状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VibratorStatusEvent](arkts-sensorservice-vibrator-vibratorstatusevent-i.md)&gt; | 是 | 回调函数。当马达设备上线或下线时触发，回调参数为VibratorStatusEvent对象，包含timestamp、deviceId、 vibratorCount、isVibratorOnline等信息。回调中获取的deviceId可用于 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md) 和[stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md)等接口指定目标设备。 |

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
  vibrator.on('vibratorStateChange', vibratorStateChangeCallback);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```
