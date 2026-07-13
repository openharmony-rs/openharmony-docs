# getDeviceIds

## getDeviceIds

```TypeScript
function getDeviceIds(callback: AsyncCallback<Array<number>>): void
```

获取所有输入设备的ID列表，使用callback异步回调。

> **说明**：

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getDeviceList

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;number&gt;&gt; | 是 | 回调函数。当获取成功，err为undefined，data为所有输入设备的ID列表；否则为错误对象。 |

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
          // 获取输入设备ID列表
          inputDevice.getDeviceIds((error: BusinessError, ids: Array<number>) => {
            if (error) {
              console.error(`Failed to get device id list, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              return;
            }
            console.info(`Succeeded in getting device id list: ${JSON.stringify(ids)}.`);
          });
        })
    }
  }
}

```


## getDeviceIds

```TypeScript
function getDeviceIds(): Promise<Array<number>>
```

获取所有输入设备的ID列表，使用Promise异步回调。

> **说明**：

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getDeviceList

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise对象，返回所有输入设备的ID列表。ID是输入设备的唯一标识。 |

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
          // 获取输入设备ID列表
          inputDevice.getDeviceIds().then((ids: Array<number>) => {
            console.info(`Succeeded in getting device id list: ${JSON.stringify(ids)}.`);
          }).catch((error: BusinessError) => {
            console.error(`Failed to get device id list, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          })
        })
    }
  }
}

```

