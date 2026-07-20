# getDeviceList

## 导入模块

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

<a id="getdevicelist"></a>
## getDeviceList

```TypeScript
function getDeviceList(callback: AsyncCallback<Array<number>>): void
```

获取所有输入设备的ID列表，使用callback异步回调。

**起始版本：** 9

<!--Device-inputDevice-function getDeviceList(callback: AsyncCallback<Array<int>>): void--><!--Device-inputDevice-function getDeviceList(callback: AsyncCallback<Array<int>>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | 是 | 回调函数。当获取成功，err为undefined，data为所有输入设备的ID列表（ID是输入设备的唯一标识）；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

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
          try {
            // 获取输入设备列表
            inputDevice.getDeviceList((error: BusinessError, ids: Array<number>) => {
              if (error) {
                console.error(`Failed to get device id list, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting device id list: ${JSON.stringify(ids)}.`);
            });
          } catch (error) {
            console.error(`Failed to get device id list, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        });
    }
  }
}

```


<a id="getdevicelist-1"></a>
## getDeviceList

```TypeScript
function getDeviceList(): Promise<Array<number>>
```

获取所有输入设备的ID列表，使用Promise异步回调。

**起始版本：** 9

<!--Device-inputDevice-function getDeviceList(): Promise<Array<int>>--><!--Device-inputDevice-function getDeviceList(): Promise<Array<int>>-End-->

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
          try {
            // 获取输入设备列表
            inputDevice.getDeviceList().then((ids: Array<number>) => {
              console.info(`Succeeded in getting device id list: ${JSON.stringify(ids)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get device id list, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            });
          } catch (error) {
            console.error(`Failed to get device id list, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

