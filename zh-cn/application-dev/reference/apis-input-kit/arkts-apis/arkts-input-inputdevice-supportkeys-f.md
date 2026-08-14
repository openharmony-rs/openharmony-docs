# supportKeys

## supportKeys

```TypeScript
function supportKeys(deviceId: int, keys: Array<KeyCode>, callback: AsyncCallback<Array<boolean>>): void
```

查询指定输入设备是否支持指定按键，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputDevice-function supportKeys(deviceId: int, keys: Array<KeyCode>, callback: AsyncCallback<Array<boolean>>): void--><!--Device-inputDevice-function supportKeys(deviceId: int, keys: Array<KeyCode>, callback: AsyncCallback<Array<boolean>>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | int | 是 | 输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。 |
| keys | Array&lt;[KeyCode](arkts-input-multimodalinput-keycode-keycode-e.md)&gt; | 是 | 需要查询的键值，最多支持5个按键查询。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;boolean&gt;&gt; | 是 | 回调函数。当查询成功，err为undefined，data为按键支持查询结果（数组元素与keys参数一一对应，true表示支 持，false表示不支持）；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 查询ID为1的输入设备对于17、22和2055按键的支持情况。
          try {
            // 查询按键支持情况
            inputDevice.supportKeys(1, [17, 22, 2055], (error: BusinessError, supportResult: Array<Boolean>) => {
              if (error) {
                console.error(`Failed to query support key, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in querying support keys, supportResult: ${JSON.stringify(supportResult)}.`);
            });
          } catch (error) {
            console.error(`Failed to query support key, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputDevice, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 查询ID为1的输入设备对于17、22和2055按键的支持情况。
          try {
            // 查询按键支持情况
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_DOWN, KeyCode.KEYCODE_VOLUME_MUTE, KeyCode.KEYCODE_DEL];
            inputDevice.supportKeys(1, keys, (error: BusinessError<void> | null, supportResult: Array<Boolean> | undefined) => {
              console.info(`Succeeded in querying support keys, supportResult: ${JSON.stringify(supportResult)}.`);
            });
          } catch (error) {
            console.error(`Failed to query support key, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## supportKeys

```TypeScript
function supportKeys(deviceId: int, keys: Array<KeyCode>): Promise<Array<boolean>>
```

查询指定输入设备是否支持指定按键，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputDevice-function supportKeys(deviceId: int, keys: Array<KeyCode>): Promise<Array<boolean>>--><!--Device-inputDevice-function supportKeys(deviceId: int, keys: Array<KeyCode>): Promise<Array<boolean>>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | int | 是 | 输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。 |
| keys | Array&lt;[KeyCode](arkts-input-multimodalinput-keycode-keycode-e.md)&gt; | 是 | 需要查询的键值，最多支持查询5个按键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;boolean&gt;&gt; | Promise对象，返回查询结果。true表示支持，false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 查询ID为1的输入设备对于17、22和2055按键的支持情况。
          try {
            // 查询按键支持情况
            inputDevice.supportKeys(1, [17, 22, 2055]).then((supportResult: Array<Boolean>) => {
              console.info(`Succeeded in querying support keys, result: ${JSON.stringify(supportResult)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to query support Keys, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            });
          } catch (error) {
            console.error(`Failed to query support key, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputDevice, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          // 查询ID为1的输入设备对于17、22和2055按键的支持情况。
          try {
            // 查询按键支持情况
            let keys: Array<KeyCode> = [KeyCode.KEYCODE_VOLUME_DOWN, KeyCode.KEYCODE_VOLUME_MUTE, KeyCode.KEYCODE_DEL];
            inputDevice.supportKeys(1, keys).then((supportResult: Array<Boolean>) => {
              console.info(`Succeeded in querying support keys, result: ${JSON.stringify(supportResult)}.`);
            }).catch((error) => {
              console.error(`Failed to query support Keys, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            });
          } catch (error) {
            console.error(`Failed to query support key, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

