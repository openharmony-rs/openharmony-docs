# setInputDeviceEnabled（系统接口）

## setInputDeviceEnabled

```TypeScript
function setInputDeviceEnabled(deviceId: int, enabled: boolean): Promise<void>
```

设置输入设备的开关状态。以触摸屏为例：关闭时，点击触摸屏设备不响应；开启时，可正常操作触摸屏。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INPUT_DEVICE_CONTROLLER

<!--Device-inputDevice-function setInputDeviceEnabled(deviceId: int, enabled: boolean): Promise<void>--><!--Device-inputDevice-function setInputDeviceEnabled(deviceId: int, enabled: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | int | 是 | 输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。 |
| enabled | boolean | 是 | 输入设备的开关状态，取值为true表示开启输入设备，取值为false表示关闭输入设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [3900001](../errorcode-inputdevice.md#3900001-指定的设备不存在) | The specified device does not exist. |

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
          try {
            // 设置设备ID为0
            inputDevice.setInputDeviceEnabled(0, true).then(() => {
              console.info(`Succeeded in setting input device enabled.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set device enabled, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set device enabled, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { inputDevice } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            inputDevice.setInputDeviceEnabled(0, true).then(() => {
              console.info(`Succeeded in setting input device enabled.`);
            }).catch((error) => {
              console.error(`Failed to set device enable, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set device enable, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

