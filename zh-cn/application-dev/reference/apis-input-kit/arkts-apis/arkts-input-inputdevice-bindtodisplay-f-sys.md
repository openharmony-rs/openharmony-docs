# bindToDisplay（系统接口）

## 导入模块

```TypeScript
```

## bindToDisplay

```TypeScript
function bindToDisplay(inputDeviceId: number, displayId: number): Promise<void>
```

将输入设备绑定到显示器。仅支持外接USB和蓝牙的鼠标、触摸板、键盘和游戏手柄。绑定后，输入设备将固定在指定显示器所在的显示器组上操作。使用Promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.INPUT_DEVICE_CONTROLLER

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputDeviceId | number | 是 | 输入设备的ID。如果输入服务重启或输入设备重连，此ID可能会发生变化。 |
| displayId | number | 是 | 目标显示器的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [3800001](../errorcode-infraredemitter.md#3800001-多模输入服务内部错误) | Input service exception. |
| [3900001](../errorcode-inputdevice.md#3900001-指定的设备不存在) | The specified input device does not exist. |
| [3900004](../errorcode-inputdevice.md#3900004-指定的显示器不存在) | The specified display does not exist. |
| [3900005](../errorcode-inputdevice.md#3900005-不支持的输入设备) | Unsupported input device. |

**示例**

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
            // 将输入设备ID为1的设备绑定到显示器ID为0的显示器上
            inputDevice.bindToDisplay(1, 0).then(() => {
              console.info(`Succeeded in binding input device to display.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to bind input device to display, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to bind input device to display, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
