# VibratorPatternBuilder

提供添加长振、短振事件和生成VibratorPattern对象的方法。使用流程：先通过 [addContinuousEvent]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或 [addTransientEvent]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_添加振动事件，再通过 [build]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_方法生成VibratorPattern对象，最后将该对象作为 [VibrateFromPattern]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_的pattern参数传入 [vibrator.startVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_ 接口触发振动。 当开发者需要通过灵活组合振动事件（长振和短振）构建自定义振动序列时使用此接口。适用于需要动态排列振动事件的交互反馈场景（如表情包拟真效果、游戏场景反馈），相比VibrateFromFile以文件描述符方式传递振动事件， VibratorPatternBuilder以振动事件数组形式传递，支持更灵活的振动事件排列组合。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-vibrator-class VibratorPatternBuilder--><!--Device-vibrator-class VibratorPatternBuilder-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## addContinuousEvent

ArkTS-Dyn:
```TypeScript
addContinuousEvent(time: number, duration: number, options?: ContinuousParam): VibratorPatternBuilder
```

ArkTS-Sta:
```TypeScript
addContinuousEvent(time: int, duration: int, options?: ContinuousParam): VibratorPatternBuilder
```

添加长振事件的方法。添加后使用build (#build18)方法生成VibratorPattern (#vibratorpattern18)对象。 用于在自定义振动序列中添加一段持续振动事件，适用于需要持续振动反馈的场景（如引擎振动、拉弓振动等）。返回VibratorPatternBuilder对象，支持链式调用addContinuousEvent或 addTransientEvent继续添加振动事件

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-VibratorPatternBuilder-addContinuousEvent(time: int, duration: int, options?: ContinuousParam): VibratorPatternBuilder--><!--Device-VibratorPatternBuilder-addContinuousEvent(time: int, duration: int, options?: ContinuousParam): VibratorPatternBuilder-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| time | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 长振事件的起始时间。单位：ms。取值范围：[0,1800000]区间内所有整数。使用场景：用于指定长振事件在振动序列中的起始时间点，多个事件间time值不能重叠。 |
| duration | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 长振事件的持续时间。单位：ms。取值范围：(0,5000]区间内所有整数。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 可选参数，用于指定长振事件的振动强度、频率、振动调节曲线和通道编号。不填时使用各参数的默认值（intensity默认100，frequency默认50，index默认0）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回已添加连续振动事件的VibratorPatternBuilder对象。可用于继续链式调用addContinuousEvent或addTransientEvent添加 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let builder = new vibrator.VibratorPatternBuilder();
// 使用try catch对可能出现的异常进行捕获
try {
  let pointsMe: vibrator.VibratorCurvePoint[] = [
    { time: 0, intensity: 0, frequency: -7 },
    { time: 42, intensity: 1, frequency: -6 },
    { time: 128, intensity: 0.94, frequency: -4 },
    { time: 217, intensity: 0.63, frequency: -14 },
    { time: 763, intensity: 0.48, frequency: -14 },
    { time: 1125, intensity: 0.53, frequency: -10 },
    { time: 1503, intensity: 0.42, frequency: -14 },
    { time: 1858, intensity: 0.39, frequency: -14 },
    { time: 2295, intensity: 0.34, frequency: -17 },
    { time: 2448, intensity: 0.21, frequency: -14 },
    { time: 2468, intensity: 0, frequency: -21 }
  ] // VibratorCurvePoint参数最少设置4个，最大设置16个
  let param: vibrator.ContinuousParam = {
    intensity: 97,
    frequency: 34,
    points:pointsMe,
    index: 0
  }
  builder.addContinuousEvent(0, 2468, param);
  console.info(`addContinuousEvent builder is ${builder.build()}`);
} catch(error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to add continuous event. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let builder = new vibrator.VibratorPatternBuilder();
// 使用try catch对可能出现的异常进行捕获
try {
  let pointsMe: vibrator.VibratorCurvePoint[] = [
    { time: 0, intensity: 0, frequency: -7 },
    { time: 42, intensity: 1, frequency: -6 },
    { time: 128, intensity: 0.94, frequency: -4 },
    { time: 217, intensity: 0.63, frequency: -14 },
    { time: 763, intensity: 0.48, frequency: -14 },
    { time: 1125, intensity: 0.53, frequency: -10 },
    { time: 1503, intensity: 0.42, frequency: -14 },
    { time: 1858, intensity: 0.39, frequency: -14 },
    { time: 2295, intensity: 0.34, frequency: -17 },
    { time: 2448, intensity: 0.21, frequency: -14 },
    { time: 2468, intensity: 0, frequency: -21 }
  ] // VibratorCurvePoint参数最少设置4个，最大设置16个
  let param: vibrator.ContinuousParam = {
    intensity: 97,
    frequency: 34,
    points:pointsMe,
    index: 0
  }
  builder.addContinuousEvent(0, 2468, param);
  console.info(`addContinuousEvent builder is ${builder.build()}`);
} catch(error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to add continuous event. Code: ${e.code}, message: ${e.message}`);
}
```

## addTransientEvent

ArkTS-Dyn:
```TypeScript
addTransientEvent(time: number, options?: TransientParam): VibratorPatternBuilder
```

ArkTS-Sta:
```TypeScript
addTransientEvent(time: int, options?: TransientParam): VibratorPatternBuilder
```

添加短振事件的方法, 添加后使用[build]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法生成 [VibratorPattern]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_对象。适用于点击、按键等短促振动反馈场景，返回VibratorPatternBuilder对象，支持链式调用继续添加振动事件。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-VibratorPatternBuilder-addTransientEvent(time: int, options?: TransientParam): VibratorPatternBuilder--><!--Device-VibratorPatternBuilder-addTransientEvent(time: int, options?: TransientParam): VibratorPatternBuilder-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| time | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 短振事件的起始时间。单位：ms。取值范围：[0,1800000]区间内所有整数。使用场景：用于指定短振事件在振动序列中的起始时间点，多个事件间time值不能重叠。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 可选参数，用于指定短振事件的振动强度、频率和通道编号。不填时使用各参数的默认值（intensity默认100，frequency默认50，index默认0）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回已添加短振事件的VibratorPatternBuilder对象。可用于继续链式调用addContinuousEvent或addTransientEvent添加更多 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { vibrator } from '@kit.SensorServiceKit';

let builder = new vibrator.VibratorPatternBuilder();
// 使用try catch对可能出现的异常进行捕获
try {
  let param: vibrator.TransientParam = {
    intensity: 80,
    frequency: 70,
    index: 0
  }
  builder.addTransientEvent(0, param);
  console.info(`addTransientEvent builder is ${builder.build()}`);
} catch(error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { vibrator } from '@kit.SensorServiceKit';

let builder = new vibrator.VibratorPatternBuilder();
// 使用try catch对可能出现的异常进行捕获
try {
  let param: vibrator.TransientParam = {
    intensity: 80,
    frequency: 70,
    index: 0
  }
  builder.addTransientEvent(0, param);
  console.info(`addTransientEvent builder is ${builder.build()}`);
} catch(error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

## build

```TypeScript
build(): VibratorPattern
```

构造组合短事件或长事件的振动序列的方法。 适用于需要将自定义振动事件组合为振动序列后，通过[VibrateFromPattern]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_触发马达振动的场景。需先通过 [addContinuousEvent]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_或 [addTransientEvent]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_添加振动事件后，再调用本方法生成VibratorPattern对象。返回 VibratorPattern对象，包含振动序列的起始时间和振动事件数组。该对象可作为VibrateFromPattern的pattern参数传入 [startVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_ 接口触发振动。需先通过[addContinuousEvent]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_或 [addTransientEvent]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_添加至少一个振动事件后调用本方法，否则生成的VibratorPattern 为空序列。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-VibratorPatternBuilder-build(): VibratorPattern--><!--Device-VibratorPatternBuilder-build(): VibratorPattern-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 振动序列对象。包含振动序列的起始时间和振动事件数组，可作为[VibrateFromPattern]{ |

**示例：**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let builder = new vibrator.VibratorPatternBuilder();
try {
  let param: vibrator.TransientParam = {
    intensity: 80,
    frequency: 70,
    index: 0
  }
  builder.addTransientEvent(0, param);
  console.info(`addTransientEvent builder is ${builder.build()}`);
} catch(error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
try {
  vibrator.startVibration({
    type: 'pattern',
    pattern: builder.build()
  }, {
  usage: 'alarm', // 根据实际选择类型归属不同的开关管控
  }, (error) => {
  if (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Vibrate fail. Code: ${e.code}, message: ${e.message}`);
  } else {
    console.info(`vibrate success`);
  }
  });
} catch(error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

