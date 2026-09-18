# off

## 导入模块

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## off('vibratorStateChange')

```TypeScript
function off(type: 'vibratorStateChange', callback?: Callback<VibratorStatusEvent>): void
```

注销马达上线或下线事件的回调函数。当开发者不再需要监听马达上下线状态变化时使用此接口注销回调。传入callback时注销指定回调；不传callback时注销该类型下所有已注册的回调。注销成功后，不再触发对应的回调函数。若传入的callback未注册过，注销操作无效但不会报错。需先通过[vibrator.on](arkts-sensorservice-vibrator-on-f.md#onvibratorstatechange)注册回调后才能注销。同一type重复注册同一callback不会覆盖，需先off再on。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'vibratorStateChange' | 是 | 监听类型，该值固定为vibratorStateChange，表示马达上下线状态变化事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[VibratorStatusEvent](arkts-sensorservice-vibrator-vibratorstatusevent-i.md)&gt; | 否 | 回调函数，需要注销的回调函数。不传此参数时注销所有vibratorStateChange类型的回调。使用场景：若仅需注销特定回调则传入对应callback；若需注销全部回调则不传此参数。 |

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
  // 取消订阅 vibratorStateChange事件
  vibrator.off('vibratorStateChange', vibratorStateChangeCallback);
  // 取消订阅所有 vibratorStateChange事件
  // vibrator.off('vibratorStateChange');
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```
