# getEffectInfoSync

## getEffectInfoSync

```TypeScript
function getEffectInfoSync(effectId: string, param?: VibratorInfoParam): EffectInfo
```

通过设备ID和马达ID获取预置振动效果信息，用于判断该预置振动效果是否受指定设备的指定马达支持。 用于多设备多马达场景下确认指定设备的指定马达是否支持某个预置振动效果，不传param时默认查询本地设备。适用于触发振动前确认效果可用性，避免在不支持的设备或马达上触发振动效果不佳。返回EffectInfo对象， isEffectSupported字段指示是否支持该预置振动效果：返回true时可直接用于startVibration (#vibratorstartvibration9)，返回false时使用该effectId触发振动可能效果不 佳。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-vibrator-function getEffectInfoSync(effectId: string, param?: VibratorInfoParam): EffectInfo--><!--Device-vibrator-function getEffectInfoSync(effectId: string, param?: VibratorInfoParam): EffectInfo-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effectId | string | 是 | 待确认的预置振动效果ID。字符串最大长度64，超出部分截取前64个字符。使用场景：不同设备预置的振动效果可能不同，需传入具体的effectId查询是否支持。取值可参考 [EffectId](arkts-sensorservice-vibrator-effectid-e.md#EffectId)和[HapticFeedback](arkts-sensorservice-vibrator-hapticfeedback-e.md#HapticFeedback)中定义的值。 |
| param | [VibratorInfoParam](arkts-sensorservice-vibrator-vibratorinfoparam-i.md) | 否 | 指出需要查询的设备和马达信息。不传param时默认查询本地设备。deviceId默认值为-1（本地设备），vibratorId默认值为0（该设备的全部马达）。 deviceId和vibratorId可通过[vibrator.getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md#getVibratorInfoSync)或 vibrator.on查询获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EffectInfo](arkts-sensorservice-vibrator-effectinfo-i.md) | 预置振动效果信息。isEffectSupported为true表示支持该效果，可用于 [startVibration]{ |

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
  const effectInfo: vibrator.EffectInfo = vibrator.getEffectInfoSync('haptic.clock.timer', { deviceId: 1, vibratorId: 3});
  console.info(`isEffectSupported: ${effectInfo.isEffectSupported}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

