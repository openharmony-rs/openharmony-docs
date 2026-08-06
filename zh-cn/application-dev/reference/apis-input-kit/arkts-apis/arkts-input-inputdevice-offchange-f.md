# offChange

## offChange

```TypeScript
function offChange(listener?: Callback<DeviceListener>): void
```

Stops listening for an input device event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-inputDevice-function offChange(listener?: Callback<DeviceListener>): void--><!--Device-inputDevice-function offChange(listener?: Callback<DeviceListener>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| listener | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DeviceListener&gt; | 否 | Callback for the input device event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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
          let callback = (data: inputDevice.DeviceListener) => {
            console.info(`Succeeded in listening to device change, data: ${JSON.stringify(data, [`type`, `deviceId`])}.`);
          };
          try {
            // 监听设备热插拔事件
            inputDevice.onChange(callback);
          } catch (error) {
            console.error(`Failed to listen device event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
          // 取消指定的监听。
          try {
            // 取消监听设备热插拔事件
            inputDevice.offChange(callback);
          } catch (error) {
            console.error(`Failed to cancel listening device event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
          // 取消所有监听。
          try {
            // 取消监听设备热插拔事件
            inputDevice.offChange();
          } catch (error) {
            console.error(`Failed to cancel all listening device event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

