# onChange

## 导入模块

```TypeScript
import { inputDevice } from '@kit.InputKit';
import { inputDeviceCooperate } from '@kit.InputKit';
```

## onChange

```TypeScript
function onChange(listener: Callback<DeviceListener>): void
```

注册监听输入设备的热插拔事件，使用时需连接鼠标、键盘、触摸屏等外部设备。

**起始版本：** 23

<!--Device-inputDevice-function onChange(listener: Callback<DeviceListener>): void--><!--Device-inputDevice-function onChange(listener: Callback<DeviceListener>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| listener | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceListener](arkts-input-inputdevice-devicelistener-i.md)&gt; | 是 | 回调函数，返回输入设备热插拔事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

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
            // 监听设备热插拔事件
            inputDevice.onChange((data: inputDevice.DeviceListener) => {
              console.info(`Succeeded in listening to device change, data: ${JSON.stringify(data)}.`);
            });
          } catch (error) {
            console.error(`Failed to listen device event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

