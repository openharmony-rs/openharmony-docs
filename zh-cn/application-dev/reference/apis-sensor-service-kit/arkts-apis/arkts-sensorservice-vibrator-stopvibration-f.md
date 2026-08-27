# stopVibration

## 导入模块

```TypeScript
```

## stopVibration

```TypeScript
function stopVibration(stopMode: VibratorStopMode): Promise<void>
```

按照指定模式停止马达的振动。调用成功后马达停止对应模式的振动。使用promise异步回调。 用于停止VibrateTime触发的指定时长振动或VibratePreset触发的预置振动。调用成功返回Promise resolve，失败返回错误对象；若无对应振动正在进行，仍返回成功。此接口无法停止自定义振动（ VibrateFromFile和VibrateFromPattern），需使用vibrator.stopVibration (#vibratorstopvibration10-1)。stopMode须与启动振动时的 VibrateEffect类型对应，否则停止无效：VibrateTime对应VIBRATOR_STOP_MODE_TIME，VibratePreset对应VIBRATOR_STOP_MODE_PRESET。

**起始版本：** 9

**需要权限：** ohos.permission.VIBRATE

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| stopMode | [VibratorStopMode](arkts-sensorservice-vibrator-vibratorstopmode-e.md) | 是 | 指定的停止振动模式，用于停止对应模式的马达振动，支持两种：VIBRATOR_STOP_MODE_TIME：停止 [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md)类型的指定时长振动；VIBRATOR_STOP_MODE_PRESET：停止 [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md)类型的预置振动。此接口无法停止自定义振动（ [VibrateFromFile](arkts-sensorservice-vibrator-vibratefromfile-i.md)和[VibrateFromPattern](arkts-sensorservice-vibrator-vibratefrompattern-i.md)），请使用 [vibrator.stopVibration&lt;sup&gt;10+&lt;/sup&gt;](#stopvibration)。stopMode需与启动振动时的VibrateEffect类型对应，否则停止操作可能无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。调用成功时Promise resolve，表示振动成功停止；调用失败时Promise reject，返回错误对象包含错误码和错误信息，可用于排查停止失败的原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

停止指定时长振动：

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 按照指定时长振动
  vibrator.startVibration({
    type: 'time',
    duration: 1000,
  }, {
    id: 0,
    usage: 'alarm' // 根据实际选择类型归属不同的开关管控
  }).then(() => {
    console.info('Succeed in starting vibration');
  }, (error: BusinessError) => {
    console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}

try {
  // 按照VIBRATOR_STOP_MODE_TIME模式停止振动
  vibrator.stopVibration(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_TIME).then(() => {
    console.info('Succeed in stopping vibration');
  }, (error: BusinessError) => {
    console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

停止预置振动：

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 按照预置效果振动
  vibrator.startVibration({
    type: 'preset',
    effectId: 'haptic.notice.success',
    count: 1,
  }, {
    id: 0,
    usage: 'notification' // 根据实际选择类型归属不同的开关管控
  }).then(() => {
    console.info('Succeed in starting vibration');
  }, (error: BusinessError) => {
    console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}

try {
  // 按照VIBRATOR_STOP_MODE_PRESET模式停止振动
  vibrator.stopVibration(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_PRESET).then(() => {
    console.info('Succeed in stopping vibration');
  }, (error: BusinessError) => {
    console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```


## stopVibration

```TypeScript
function stopVibration(stopMode: VibratorStopMode, callback: AsyncCallback<void>): void
```

按照指定模式停止马达振动。调用成功后马达停止对应模式的振动。使用callback异步回调。 stopMode需与启动振动时的VibrateEffect类型对应：VIBRATOR_STOP_MODE_TIME用于停止VibrateTime类型振动，VIBRATOR_STOP_MODE_PRESET用于停止 VibratePreset类型振动，否则停止操作可能无效。调用成功后指定模式振动停止，若无对应振动正在进行也会成功返回。此接口无法停止自定义振动（VibrateFromFile和VibrateFromPattern），如需停止自定 义振动或所有模式振动，请使用vibrator.stopVibration (#vibratorstopvibration10)。

**起始版本：** 9

**需要权限：** ohos.permission.VIBRATE

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| stopMode | [VibratorStopMode](arkts-sensorservice-vibrator-vibratorstopmode-e.md) | 是 | 指定的停止振动模式，用于停止对应模式的马达振动，支持两种：VIBRATOR_STOP_MODE_TIME：停止 [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md)类型的固定时长振动；VIBRATOR_STOP_MODE_PRESET：停止 [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md)类型的预置振动。此接口无法停止自定义振动（ [VibrateFromFile](arkts-sensorservice-vibrator-vibratefromfile-i.md)和[VibrateFromPattern](arkts-sensorservice-vibrator-vibratefrompattern-i.md)），请使用 [vibrator.stopVibration&lt;sup&gt;10+&lt;/sup&gt;](#stopvibration)。stopMode需与启动振动时的 VibrateEffect类型对应，否则停止操作可能无效。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当马达停止振动成功，err为undefined，否则为错误对象。回调结果可用于确认振动是否成功停止。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

停止指定时长振动：

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 按照指定时长振动
  vibrator.startVibration({
    type: 'time',
    duration: 1000,
  }, {
    id: 0,
    usage: 'alarm' // 根据实际选择类型归属不同的开关管控
  }, (error: BusinessError) => {
    if (error) {
      console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeed in starting vibration');
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}

try {
  // 按照VIBRATOR_STOP_MODE_TIME模式停止振动
  vibrator.stopVibration(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_TIME, (error: BusinessError) => {
    if (error) {
      console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeed in stopping vibration');
  })
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

停止预置振动：

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 按照预置效果振动
  vibrator.startVibration({
    type: 'preset',
    effectId: 'haptic.notice.success',
    count: 1,
  }, {
    id: 0,
    usage: 'notification' // 根据实际选择类型归属不同的开关管控
  }, (error: BusinessError) => {
    if (error) {
      console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeed in starting vibration');
  });
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}

try {
  // 按照VIBRATOR_STOP_MODE_PRESET模式停止振动
  vibrator.stopVibration(vibrator.VibratorStopMode.VIBRATOR_STOP_MODE_PRESET, (error: BusinessError) => {
    if (error) {
      console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeed in stopping vibration');
  })
} catch (err) {
  let e: BusinessError = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```


## stopVibration

```TypeScript
function stopVibration(callback: AsyncCallback<void>): void
```

停止所有模式的马达振动。调用成功后马达停止振动。使用callback异步回调。 用于停止设备上所有类型的振动（包括VibrateTime、VibratePreset、VibrateFromFile、VibrateFromPattern），适用于应用退出、页面切换等需立即终止所有振动的场景。与 vibrator.stopVibration (#vibratorstopvibration9)（需传入stopMode）不同，本接口无需指定停止模式，可停止包括自定义振动在内的所有振动。

**起始版本：** 10

**需要权限：** ohos.permission.VIBRATE

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当马达停止振动成功，err为undefined，否则为错误对象，包含错误码和错误信息。回调结果可用于确认所有振动是否成功停止。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 停止所有模式的马达振动
  vibrator.stopVibration((error: BusinessError) => {
    if (error) {
      console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeed in stopping vibration');
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```


## stopVibration

```TypeScript
function stopVibration(): Promise<void>
```

停止所有模式的马达振动。调用成功后马达停止振动。使用promise异步回调。 用于停止设备上所有类型的振动（包括VibrateTime、VibratePreset、VibrateFromFile、VibrateFromPattern），适用于应用退出、页面切换等需立即终止所有振动的场景。调用成功返回 Promise resolve，失败返回错误对象。与vibrator.stopVibration (#vibratorstopvibration9-1)（需传入stopMode）不同，本接口无需指定停止模式，可停止包括自定义振动在 内的所有振动。

**起始版本：** 10

**需要权限：** ohos.permission.VIBRATE

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.MiscDevice

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。调用成功时Promise resolve，表示所有振动成功停止；调用失败时Promise reject，返回错误对象包含错误码和错误信息，可用于排查停止失败的原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 停止所有模式的马达振动
  vibrator.stopVibration().then(() => {
    console.info('Succeed in stopping vibration');
  }, (error: BusinessError) => {
    console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```


## stopVibration

```TypeScript
function stopVibration(param?: VibratorInfoParam): Promise<void>
```

停止指定设备马达振动。不传参默认停止本地设备所有马达的振动。使用promise异步回调。 用于多设备多马达场景下停止指定设备或指定马达的振动。不传参时默认停止本地设备全部马达振动；传入VibratorInfoParam可指定远程设备的特定马达。调用成功返回Promise resolve，失败返回错误对象。与 vibrator.stopVibration (#vibratorstopvibration10-1)（无参数版本）相比，本接口新增VibratorInfoParam可选参数，支持精确控制停止范围，前者仅能停止本地设备所有马达振动 。

**起始版本：** 19

**需要权限：** ohos.permission.VIBRATE

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [VibratorInfoParam](arkts-sensorservice-vibrator-vibratorinfoparam-i.md) | 否 | 指出需要停止振动的设备和马达信息。不传参时默认停止本地设备的全部马达振动。deviceId默认值为-1（本地设备），vibratorId默认值为0（该设备的全部马 达）。deviceId和vibratorId可通过[vibrator.getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md)或 [vibrator.on](arkts-sensorservice-vibrator-on-f.md#onvibratorstatechange)查询获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。调用成功时Promise resolve，表示指定设备马达振动成功停止；调用失败时Promise reject，返回错误对象包含错误码和错误信息，可用于排查停止失败的 原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [14600101](../errorcode-vibrator.md#14600101-操作设备失败) | Device operation failed. |

**示例**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function vibratorDemo() {
  // 查询所有马达设备信息。
  const vibratorInfoList: vibrator.VibratorInfo[] = vibrator.getVibratorInfoSync();
  // 根据实际业务逻辑获取目标马达，例如查找本地马达，此处示例仅做展示，开发者需要自行调整筛选逻辑。
  const targetVibrator = vibratorInfoList.find((vibrator: vibrator.VibratorInfo) => {
    return vibrator.isLocalVibrator;
  });
  if (!targetVibrator) {
    return;
  }
  // 调用 vibrator.startVibration 开始振动。
  // ...

  // 使用try catch对可能出现的异常进行捕获。
  try {
    // 根据实际业务场景停止马达振动。
    vibrator.stopVibration({ deviceId: targetVibrator.deviceId, vibratorId: targetVibrator.vibratorId }).then(() => {
      console.info('Succeed in stopping vibration');
    }, (error: BusinessError) => {
      console.error(`Failed to stop vibration. Code: ${error.code}, message: ${error.message}`);
    });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
  }
}
```
