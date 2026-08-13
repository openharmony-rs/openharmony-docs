# startVibration

## startVibration

```TypeScript
function startVibration(effect: VibrateEffect, attribute: VibrateAttribute, callback: AsyncCallback<void>): void
```

根据指定的振动效果和振动属性触发马达振动，使用callback异步回调。 适用于为用户交互提供触觉反馈、为通知/闹钟等事件提供振动提醒，或在游戏、多媒体等场景中提供沉浸式振动体验。调用成功后，设备马达将按指定效果和属性开始振动；若同一马达已有正在进行的振动，新请求将按系统优先级规则处理。同功能还提供 Promise版本vibrator.startVibration (#vibratorstartvibration9-1)，开发者可根据回调风格偏好选择。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.VIBRATE

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-vibrator-function startVibration(effect: VibrateEffect, attribute: VibrateAttribute, callback: AsyncCallback<void>): void--><!--Device-vibrator-function startVibration(effect: VibrateEffect, attribute: VibrateAttribute, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [VibrateEffect](arkts-sensorservice-vibrator-vibrateeffect-t.md) | 是 | 马达振动效果，支持四种：&lt;br&gt;1、[VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md#VibratePreset)：按照预置振动效果触发马达振动，适用于交互反馈 类的短振场景（如点击长按，滑动，拖拽等），为确保与系统整体振感反馈体验风格一致，推荐使用此接口；&lt;br&gt;2、[VibrateFromFile](arkts-sensorservice-vibrator-vibratefromfile-i.md#VibrateFromFile)：按照文件形式定制自定义振 动效果触发马达振动，适用于匹配复杂场景效果的交互反馈（如表情包触发的拟真效果、游戏场景/操作反馈）；&lt;br&gt;3、[VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md#VibrateTime)：按照指定时长触发马达振动，仅对振动时 长进行启动或停止控制，满足基础功能，无法对振动强度、频率等维度进行个性化设置，此种振动调节不够细腻，无法满足精致体验；&lt;br/&gt;4、 [VibrateFromPattern&lt;sup&gt;18+&lt;/sup&gt;](arkts-sensorservice-vibrator-vibratefrompattern-i.md#VibrateFromPattern)：按照自定义振动效果触发马达振动。使用场景和VibrateFromFile一致。 VibrateFromFile是面向文件中提前定制好的效果，将具体的振动事件以文件描述符形式传递到接口中；VibrateFromPattern提供更加灵活的振动事件排列组合，将振动事件以振动事件数组的形式传递到接口中。&lt;br/&gt; |
| attribute | [VibrateAttribute](arkts-sensorservice-vibrator-vibrateattribute-i.md) | 是 | 马达振动属性，用于指定马达ID、设备ID和振动使用场景。attribute中的usage参数决定振动的场景类型，不同场景类型受系统振动开关管控规则不同，开发者需 根据实际业务场景选择合适的usage值。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当马达振动成功，err为undefined；否则为错误对象，包含错误码和错误信息。回调结果可用于确认振动是否成功启动，若启动失败可根据错误码进行相 应处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [14600101](../errorcode-vibrator.md#14600101-操作设备失败) | Device operation failed |

## 示例

按照预置振动效果触发马达振动：

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
        vibrator.startVibration({
          type: 'preset',
          effectId: 'haptic.notice.success',
          count: 1,
        }, {
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
    }
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

按照自定义振动配置文件触发马达振动：

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const fileName: string = 'xxx.json';

@Entry
@Component
struct Index {
  uiContext = this.getUIContext();

  build() {
    Row() {
      Column() {
        Button('alarm-file')
          .onClick(() => {
            let rawFd: resourceManager.RawFileDescriptor | undefined = this.uiContext.getHostContext()?.resourceManager.getRawFdSync(fileName);
            if (rawFd != undefined) {
              try {
                vibrator.startVibration({
                  type: 'file',
                  hapticFd: { fd: rawFd.fd, offset: rawFd.offset, length: rawFd.length }
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
              } finally {
                vibrator.stopVibration();
                this.uiContext.getHostContext()?.resourceManager.closeRawFdSync(fileName);
              }
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

按照指定时长触发马达振动：

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
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
```


## startVibration

```TypeScript
function startVibration(effect: VibrateEffect, attribute: VibrateAttribute): Promise<void>
```

根据指定的振动效果和振动属性触发马达振动，使用promise异步回调。 适用于交互触觉反馈、事件振动提醒或游戏、多媒体等沉浸式振动场景。调用成功时Promise resolve无返回值；调用失败时Promise reject返回错误对象。若同一马达已有振动正在进行，新请求按系统优先级规则处理。同功能还 提供callback版本vibrator.startVibration (#vibratorstartvibration9)，开发者可根据回调风格偏好选择。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.VIBRATE

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-vibrator-function startVibration(effect: VibrateEffect, attribute: VibrateAttribute): Promise<void>--><!--Device-vibrator-function startVibration(effect: VibrateEffect, attribute: VibrateAttribute): Promise<void>-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [VibrateEffect](arkts-sensorservice-vibrator-vibrateeffect-t.md) | 是 | 马达振动效果，支持四种：&lt;br/&gt;1、[VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md#VibratePreset)：按照预置振动效果触发马达振动，适用于交互反 馈类的短振场景（如点击长按，滑动，拖拽等），为确保与系统整体振感反馈体验风格一致，推荐使用此接口；&lt;br/&gt;2、[VibrateFromFile](arkts-sensorservice-vibrator-vibratefromfile-i.md#VibrateFromFile)：按照文件形式定制自定 义振动效果触发马达振动，适用于匹配复杂场景效果的交互反馈（如表情包触发的拟真效果、游戏场景/操作反馈）；&lt;br/&gt;3、[VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md#VibrateTime)：按照指定时长触发马达振动，仅对 振动时长进行启动或停止控制，满足基础功能，无法对振动强度、频率等维度进行个性化设置，此种振动调节不够细腻，无法满足精致体验；&lt;br/&gt;4、 [VibrateFromPattern&lt;sup&gt;18+&lt;/sup&gt;](arkts-sensorservice-vibrator-vibratefrompattern-i.md#VibrateFromPattern)：按照自定义振动效果触发马达振动。使用场景和VibrateFromFile一致。 VibrateFromFile是面向文件中提前定制好的效果，将具体的振动事件以文件描述符形式传递到接口中；VibrateFromPattern提供更加灵活的振动事件排列组合，将振动事件以振动事件数组的形式传递到接口中。 |
| attribute | [VibrateAttribute](arkts-sensorservice-vibrator-vibrateattribute-i.md) | 是 | 马达振动属性，用于指定马达ID、设备ID和振动使用场景。attribute中的usage参数决定振动的场景类型，不同场景类型受系统振动开关管控规则不同，开发者需 根据实际业务场景选择合适的usage值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。调用成功时Promise resolve，表示振动成功启动；调用失败时Promise reject，返回错误对象包含错误码和错误信息，可用于排查振动启动失 败的原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [14600101](../errorcode-vibrator.md#14600101-操作设备失败) | Device operation failed. |

## 示例

按照预置振动效果触发马达振动：

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 查询是否支持'haptic.notice.success'
  vibrator.isSupportEffect('haptic.notice.success').then((state: boolean) => {
    console.info('Succeed in querying effect');
    if (state) {
      try {
        vibrator.startVibration({
          type: 'preset',
          effectId: 'haptic.notice.success',
          count: 1,
        }, {
          usage: 'notification' // 根据实际选择类型归属不同的开关管控
        }).then(() => {
          console.info('Succeed in starting vibration');

        });
      } catch (err) {
        let e: BusinessError = err as BusinessError;
        console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
      }
    }
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

按照自定义振动配置文件触发马达振动：

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const fileName: string = 'xxx.json';

@Entry
@Component
struct Index {
  uiContext = this.getUIContext();

  build() {
    Row() {
      Column() {
        Button('alarm-file')
          .onClick(() => {
            let rawFd: resourceManager.RawFileDescriptor | undefined = this.uiContext.getHostContext()?.resourceManager.getRawFdSync(fileName);
            if (rawFd != undefined) {
              try {
                vibrator.startVibration({
                  type: "file",
                  hapticFd: { fd: rawFd.fd, offset: rawFd.offset, length: rawFd.length }
                }, {
                  id: 0,
                  usage: 'alarm' // 根据实际选择类型归属不同的开关管控
                }).then(() => {
                  console.info('Succeed in starting vibration');
                }).catch((error: BusinessError) => {
                  console.error(`Failed to start vibration. Code: ${error.code}, message: ${error.message}`);
                });
              } catch (err) {
                let e: BusinessError = err as BusinessError;
                console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
              } finally {
                vibrator.stopVibration();
                this.uiContext.getHostContext()?.resourceManager.closeRawFdSync(fileName);
              }
            }
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

按照指定时长触发马达振动：

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  vibrator.startVibration({
    type: 'time',
    duration: 1000
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
```

