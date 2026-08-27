# isSupportEffectSync

## 导入模块

```TypeScript
```

## isSupportEffectSync

```TypeScript
function isSupportEffectSync(effectId: string): boolean
```

查询当前设备是否支持预设的振动效果。此接口为同步接口，会阻塞主线程直到查询完成，容易影响UI交互，需谨慎使用。 当开发者需要在触发预置振动前立即确认当前设备是否支持指定的振动效果时使用此接口。适用于对实时性要求高且查询逻辑简单的场景。返回boolean结果：返回true表示设备支持该effectId，可用于 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md) ；返回false表示不支持，使用该effectId触发振动可能效果不佳或无法振动。与异步版本 [vibrator.isSupportEffect](arkts-sensorservice-vibrator-issupporteffect-f.md)相比，本接 口为同步接口，直接返回结果无需回调，但会阻塞主线程。建议在非UI线程中使用，或在UI线程中优先使用异步版本以避免影响交互响应。

**起始版本：** 12

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effectId | string | 是 | 待确认的预置振动效果ID。字符串最大长度64，超出部分截取前64个字符。使用场景：不同设备预置的振动效果可能不同，需传入具体的effectId查询是否支持。取值可参考 [EffectId](arkts-sensorservice-vibrator-effectid-e.md)和[HapticFeedback](arkts-sensorservice-vibrator-hapticfeedback-e.md)中定义的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回对象。返回true表示设备支持该effectId，可用于 [startVibration]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14600101](../errorcode-vibrator.md#14600101-操作设备失败) | Device operation failed. |

**示例**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 查询是否支持预设'haptic.notice.success'
  let ret = vibrator.isSupportEffectSync('haptic.notice.success');
  console.info(`The query result is ${ret}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```
