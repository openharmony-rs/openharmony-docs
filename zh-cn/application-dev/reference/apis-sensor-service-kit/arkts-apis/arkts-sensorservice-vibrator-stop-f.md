# stop

## stop

```TypeScript
function stop(stopMode: VibratorStopMode): Promise<void>
```

按照指定模式停止马达的振动。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [vibrator.stopVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [vibrator.stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md#stopvibration)(stopMode:

**需要权限：** ohos.permission.VIBRATE

<!--Device-vibrator-function stop(stopMode: VibratorStopMode): Promise<void>--><!--Device-vibrator-function stop(stopMode: VibratorStopMode): Promise<void>-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| stopMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 马达停止指定的振动模式。需与启动振动时的模式对应：VIBRATOR\_\_\_ESCAPED\_UNDERSCORE\_\_\_STOP\_\_\_ESCAPED\_UNDERSCORE\_\_\_MODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_TIME用于停止时长振动，VIBRATOR\_\_\_ESCAPED\_UNDERSCORE\_\_\_STOP\_\_\_ESCAPED\_UNDERSCORE\_\_\_MODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_PRESET用于停止预置效果振动。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。调用成功时Promise resolve，表示振动成功停止；调用失败时Promise reject，返回错误对象包含错误码和错误信息。 |

**示例：**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 按照effectId类型启动振动
vibrator.vibrate(vibrator.EffectId.EFFECT_CLOCK_TIMER, (error: BusinessError) => {
  if (error) {
    console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
  } else {
    console.info('Succeed in vibrating');
  }
})
// 使用VIBRATOR_STOP_MODE_PRESET模式停止振动
vibrator.stop(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_PRESET).then(() => {
  console.info('Succeed in stopping');
}, (error: BusinessError) => {
  console.error(`Failed to stop. Code: ${error.code}, message: ${error.message}`);
});
```


## stop

```TypeScript
function stop(stopMode: VibratorStopMode, callback?: AsyncCallback<void>): void
```

按照指定模式停止马达的振动。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [vibrator.stopVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [vibrator.stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md#stopvibration)(stopMode:

**需要权限：** ohos.permission.VIBRATE

<!--Device-vibrator-function stop(stopMode: VibratorStopMode, callback?: AsyncCallback<void>): void--><!--Device-vibrator-function stop(stopMode: VibratorStopMode, callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| stopMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 马达停止指定的振动模式。需与启动振动时的模式对应：VIBRATOR\_\_\_ESCAPED\_UNDERSCORE\_\_\_STOP\_\_\_ESCAPED\_UNDERSCORE\_\_\_MODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_TIME用于停止时长振动，VIBRATOR\_\_\_ESCAPED\_UNDERSCORE\_\_\_STOP\_\_\_ESCAPED\_UNDERSCORE\_\_\_MODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_PRESET用于停止预置效果振动。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 回调函数，当马达停止振动成功，err为undefined，否则为错误对象。使用场景：不填写时仅停止振动不获取回调结果。 |

**示例：**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 按照effectId类型启动振动
vibrator.vibrate(vibrator.EffectId.EFFECT_CLOCK_TIMER, (error: BusinessError) => {
  if (error) {
    console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
  } else {
    console.info('Succeed in vibrating');
  }
})
// 使用VIBRATOR_STOP_MODE_PRESET模式停止振动
vibrator.stop(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_PRESET, (error: BusinessError) => {
  if (error) {
    console.error(`Failed to stop. Code: ${error.code}, message: ${error.message}`);
  } else {
    console.info('Succeed in stopping');
  }
})
```

