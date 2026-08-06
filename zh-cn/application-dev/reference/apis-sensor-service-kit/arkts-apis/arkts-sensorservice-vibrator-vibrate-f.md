# vibrate

## vibrate

```TypeScript
function vibrate(duration: number, callback?: AsyncCallback<void>): void
```

按照指定持续时间触发马达振动。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [vibrator.startVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [vibrator.startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startvibration)(effect:

**需要权限：** ohos.permission.VIBRATE

<!--Device-vibrator-function vibrate(duration: number, callback?: AsyncCallback<void>): void--><!--Device-vibrator-function vibrate(duration: number, callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | number | 是 | 马达振动时长。单位：ms。取值范围：(0,1800000]区间的所有整数。由于实际产品厂商驱动对器件保护设计规格不同，不同设备实际最大振动时长会有差异。建议值：单次触发长振动一般建议不超过10000（10秒），以最大化用户体验。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 回调函数，当马达振动成功，err为undefined，否则为错误对象。使用场景：不填写时仅触发振动不获取回调结果。 |

**示例：**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

vibrator.vibrate(1000, (error: BusinessError) => {
  if (error) {
    console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
  } else {
    console.info('Succeed in vibrating');
  }
})
```


## vibrate

```TypeScript
function vibrate(duration: number): Promise<void>
```

按照指定持续时间触发马达振动。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [vibrator.startVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [vibrator.startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startvibration)(effect:

**需要权限：** ohos.permission.VIBRATE

<!--Device-vibrator-function vibrate(duration: number): Promise<void>--><!--Device-vibrator-function vibrate(duration: number): Promise<void>-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | number | 是 | 马达振动时长。单位：ms。取值范围：(0,1800000]区间的所有整数。由于实际产品厂商驱动对器件保护设计规格不同，不同设备实际最大振动时长会有差异。建议值：单次触发长振动一般建议不超过10000（10秒），以最大化用户体验。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。调用成功时Promise resolve，表示振动成功启动；调用失败时Promise reject，返回错误对象包含错误码和错误信息。 |

**示例：**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

vibrator.vibrate(1000).then(() => {
  console.info('Succeed in vibrating');
}, (error: BusinessError) => {
  console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
});
```


## vibrate

```TypeScript
function vibrate(effectId: EffectId): Promise<void>
```

按照预置振动效果触发马达振动。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [vibrator.startVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [vibrator.startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startvibration)(effect:

**需要权限：** ohos.permission.VIBRATE

<!--Device-vibrator-function vibrate(effectId: EffectId): Promise<void>--><!--Device-vibrator-function vibrate(effectId: EffectId): Promise<void>-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effectId | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 预置的振动效果ID。字符串最大长度64，超出部分截取前64个字符。建议先通过[vibrator.isSupportEffect]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_或[vibrator.isSupportEffectSync]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_查询是否支持。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。调用成功时Promise resolve，表示振动成功启动；调用失败时Promise reject，返回错误对象包含错误码和错误信息。 |

**示例：**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

vibrator.vibrate(vibrator.EffectId.EFFECT_CLOCK_TIMER).then(() => {
  console.info('Succeed in vibrating');
}, (error: BusinessError) => {
  console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
});
```


## vibrate

```TypeScript
function vibrate(effectId: EffectId, callback?: AsyncCallback<void>): void
```

按照指定振动效果触发马达振动。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [vibrator.startVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [vibrator.startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startvibration)(effect:

**需要权限：** ohos.permission.VIBRATE

<!--Device-vibrator-function vibrate(effectId: EffectId, callback?: AsyncCallback<void>): void--><!--Device-vibrator-function vibrate(effectId: EffectId, callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effectId | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 预置的振动效果ID。字符串最大长度64，超出部分截取前64个字符。建议先通过[vibrator.isSupportEffect]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_或[vibrator.isSupportEffectSync]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_查询是否支持。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 回调函数，当马达振动成功，err为undefined，否则为错误对象。使用场景：不填写时仅触发振动不获取回调结果。 |

**示例：**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

vibrator.vibrate(vibrator.EffectId.EFFECT_CLOCK_TIMER, (error: BusinessError) => {
  if (error) {
    console.error(`Failed to vibrate. Code: ${error.code}, message: ${error.message}`);
  } else {
    console.info('Succeed in vibrating');
  }
})
```

