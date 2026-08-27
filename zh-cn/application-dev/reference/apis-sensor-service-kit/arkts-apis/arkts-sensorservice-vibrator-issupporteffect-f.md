# isSupportEffect

## 导入模块

```TypeScript
```

## isSupportEffect

```TypeScript
function isSupportEffect(effectId: string, callback: AsyncCallback<boolean>): void
```

查询当前设备是否支持传入的预置振动效果effectId。使用callback异步回调。 当开发者需要在触发预置振动前确认当前设备是否支持指定的振动效果时使用此接口。由于不同设备可能预置不同的振动效果，建议在使用 [vibrator.startVibration](arkts-sensorservice-vibrator-startvibration-f.md) 的VibratePreset类型前先调用此接口查询，避免在不支持的设备上触发振动效果不佳。调用成功后，通过callback返回boolean结果：返回true表示设备支持该effectId，可直接用于startVibration； 返回false表示不支持，此时使用该effectId触发振动可能效果不佳或无法振动。

**起始版本：** 10

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effectId | string | 是 | 待确认的预置振动效果ID。字符串最大长度64，超出部分截取前64个字符。使用场景：不同设备预置的振动效果可能不同，需传入具体的effectId查询是否支持。取值可参考 [EffectId](arkts-sensorservice-vibrator-effectid-e.md)和[HapticFeedback](arkts-sensorservice-vibrator-hapticfeedback-e.md)中定义的值。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示设备支持该effectId，可用于 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md) ；返回false表示不支持，使用该effectId触发振动可能效果不佳。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 查询是否支持'haptic.notice.success'
  vibrator.isSupportEffect('haptic.notice.success', (err: BusinessError, state: boolean) => {
    if (err) {
      console.error(`Failed to query effect. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeed in querying effect');
    if (state) {
      try {
        // 使用startVibration需要添加ohos.permission.VIBRATE权限
        vibrator.startVibration({
          type: 'preset',
          effectId: 'haptic.notice.success',
          count: 1,
        }, {
          usage: 'unknown' // 根据实际选择类型归属不同的开关管控
        }, (error: BusinessError) => {
          if (error) {
            console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
          } else {
            console.info('Succeed in starting vibration');
          }
        });
      } catch (error) {
        let e: BusinessError = error as BusinessError;
        console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
      }
    }
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```


## isSupportEffect

```TypeScript
function isSupportEffect(effectId: string): Promise<boolean>
```

查询当前设备是否支持传入的预置振动效果effectId。使用promise异步回调。 当开发者需要在触发预置振动前确认当前设备是否支持指定的振动效果时使用此接口。与callback版本功能一致，开发者可根据异步回调风格偏好选择使用。调用成功时Promise resolve返回boolean结果：返回true表示设备 支持该effectId；返回false表示不支持，此时使用该effectId触发振动可能效果不佳或无法振动。

**起始版本：** 10

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effectId | string | 是 | 待确认的预置振动效果ID。字符串最大长度64，超出部分截取前64个字符。使用场景：不同设备预置的振动效果可能不同，需传入具体的effectId查询是否支持。取值可参考 [EffectId](arkts-sensorservice-vibrator-effectid-e.md)和[HapticFeedback](arkts-sensorservice-vibrator-hapticfeedback-e.md)中定义的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | Promise对象。返回true表示设备支持该effectId，可用于 [startVibration]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 查询是否支持'haptic.notice.success'
  vibrator.isSupportEffect('haptic.notice.success').then((state: boolean) => {
    console.info(`The query result is ${state}`);
    if (state) {
      try {
        vibrator.startVibration({
          type: 'preset',
          effectId: 'haptic.notice.success',
          count: 1,
        }, {
          usage: 'unknown' // 根据实际选择类型归属不同的开关管控
        }).then(() => {
          console.info('Succeed in starting vibration');
        }).catch((error: BusinessError) => {
          console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
        });
      } catch (error) {
        let e: BusinessError = error as BusinessError;
        console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
      }
    }
  }, (error: BusinessError) => {
    console.error(`Failed to query effect. Code: ${error.code}, message: ${error.message}`);
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```
