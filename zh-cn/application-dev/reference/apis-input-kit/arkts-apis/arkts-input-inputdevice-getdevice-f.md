# getDevice

## 导入模块

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## getDevice

```TypeScript
function getDevice(deviceId: number, callback: AsyncCallback<InputDeviceData>): void
```

获取指定id的输入设备信息，使用callback异步回调。

> **说明**：

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getDeviceInfo

<!--Device-inputDevice-function getDevice(deviceId: number, callback: AsyncCallback<InputDeviceData>): void--><!--Device-inputDevice-function getDevice(deviceId: number, callback: AsyncCallback<InputDeviceData>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 是 | 输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<InputDeviceData> | 是 | 回调函数。当获取成功，err为undefined，data为输入设备信息；否则为错误对象。 |

**示例：**

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
          // 获取输入设备ID为1的设备信息。
          inputDevice.getDevice(1, (error: BusinessError, deviceData: inputDevice.InputDeviceData) => {
            if (error) {
              console.error(`Failed to get device info, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              return;
            }
            console.info(`Succeeded in getting device info: ${JSON.stringify(deviceData)}.`);
          });
        })
    }
  }
}

```


## getDevice

```TypeScript
function getDevice(deviceId: number): Promise<InputDeviceData>
```

获取指定id的输入设备信息，使用Promise异步回调。

> **说明**：

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getDeviceInfo

<!--Device-inputDevice-function getDevice(deviceId: number): Promise<InputDeviceData>--><!--Device-inputDevice-function getDevice(deviceId: number): Promise<InputDeviceData>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 是 | 输入设备的唯一标识，同一个物理设备反复插拔或重启，设备ID可能会发生变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<InputDeviceData> | Promise对象，返回输入设备信息，包括输入设备ID、名称、支持的输入能力、物理地址、版本信息及产品信息等。 |

**示例：**

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
          // 获取输入设备ID为1的设备信息。
          inputDevice.getDevice(1).then((deviceData: inputDevice.InputDeviceData) => {
            console.info(`Succeeded in getting device info: ${JSON.stringify(deviceData)}.`);
          }).catch((error: BusinessError) => {
            console.error(`Failed to get device info, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          })
        })
    }
  }
}

```

