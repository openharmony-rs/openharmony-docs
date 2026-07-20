# on

## 导入模块

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

<a id="on"></a>
## on('change')

```TypeScript
function on(type: 'change', listener: Callback<DeviceListener>): void
```

注册监听输入设备的热插拔事件，使用时需连接鼠标、键盘、触摸屏等外部设备。使用callback异步回调。

**起始版本：** 9

<!--Device-inputDevice-function on(type: 'change', listener: Callback<DeviceListener>): void--><!--Device-inputDevice-function on(type: 'change', listener: Callback<DeviceListener>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'change' | 是 | 输入设备的事件类型，固定值为'change'。 |
| listener | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;DeviceListener&gt; | 是 | 回调函数，返回输入设备热插拔事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { inputDevice } from '@kit.InputKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

const DOMAIN = 0x0000;

@Entry
@Component
struct Index {
  @State isPhysicalKeyboardExist: boolean = false;
  @State message: string = 'Click to obtain the device list and monitor device hot-plug events';
  keyboards: Map<number, inputDevice.KeyboardType> = new Map();

  build() {
    RelativeContainer() {
      Column() {
        Text(this.message)
          .onClick(() => {
            try {
              // 1.获取设备列表，判断是否有物理键盘连接
              inputDevice.getDeviceList().then(data => {
                for (let i = 0; i < data.length; ++i) {
                  // 获取键盘类型
                  inputDevice.getKeyboardType(data[i]).then(type => {
                    if (type === inputDevice.KeyboardType.ALPHABETIC_KEYBOARD) {
                      // 物理键盘已连接
                      this.isPhysicalKeyboardExist = true;
                      this.keyboards.set(data[i], type);
                    }
                  }).catch((error: BusinessError) => {
                    console.error(`Failed to get keyboard type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                  });
                }
              }).catch((error: BusinessError) => {
                console.error(`Failed to get Device List, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              });
              // 2.监听设备热插拔
              inputDevice.on('change', (data) => {
                // 打印日志
                hilog.info(DOMAIN, 'InputDevice', `Device event info: %{public}s`, JSON.stringify(data));
                // 获取键盘类型
                inputDevice.getKeyboardType(data.deviceId).then((type) => {
                  // 打印日志
                  hilog.info(DOMAIN, 'InputDevice', 'The keyboard type is: %{public}d', type);
                  if (type === inputDevice.KeyboardType.ALPHABETIC_KEYBOARD && data.type === 'add') {
                    // 物理键盘已插入
                    this.isPhysicalKeyboardExist = true;
                    this.keyboards.set(data.deviceId, type);
                  }
                }).catch((error: BusinessError) => {
                  console.error(`Failed to get keyboard type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                });
                if (this.keyboards.get(data.deviceId) === inputDevice.KeyboardType.ALPHABETIC_KEYBOARD &&
                  data.type === 'remove') {
                  // 物理键盘已拔掉
                  this.isPhysicalKeyboardExist = false;
                  this.keyboards.delete(data.deviceId);
                }
              });
              this.message = 'Device monitoring enabled successfully'
            } catch (error) {
              // 打印错误日志
              hilog.error(DOMAIN, 'InputDevice', `Execute failed, error: %{public}s`,
                JSON.stringify(error, ['code', 'message']));
              this.message = `Failed to enable device monitoring. Click to retry. Error message:${JSON.stringify(error,
                ["code", "message"])}`
            }
          })
      }
    }
  }
}

```

