# getState（系统接口）

## 导入模块

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
```

## getState

```TypeScript
function getState(deviceDescriptor: string, callback: AsyncCallback<{ state: boolean }>): void
```

获取键鼠穿越开关的状态，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 23

**替代接口：** [getCooperateSwitchState](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-cooperate-getcooperateswitchstate-f-sys.md)

**系统能力：** SystemCapability.MultimodalInput.Input.Cooperator

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | string | 是 | 键鼠穿越目标设备描述符。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ state: boolean }&gt; | 是 | 回调函数。当获取键鼠穿越开关状态成功，err为undefined，data为键鼠穿越开关状态（true表示打开，false表示关闭）；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | SystemAPI permit error.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let deviceDescriptor = 'descriptor';
          try {
            inputDeviceCooperate.getState(deviceDescriptor, (error: BusinessError, data: object) => {
              if (error) {
                console.error(`Failed to get status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting status, data: ${JSON.stringify(data)}.`);
            });
          } catch (error) {
            console.error(`Failed to get status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


<a id="getstate-1"></a>

## getState

```TypeScript
function getState(deviceDescriptor: string): Promise<{ state: boolean }>
```

获取键鼠穿越开关的状态，使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 23

**替代接口：** [getCooperateSwitchState](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-cooperate-getcooperateswitchstate-f-sys.md)

**系统能力：** SystemCapability.MultimodalInput.Input.Cooperator

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | string | 是 | 键鼠穿越目标设备描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;{ state: boolean }&gt; | Promise对象，返回键鼠穿越开关状态。true表示键鼠穿越开关打开，false表示键鼠穿越开关关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | SystemAPI permit error.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let deviceDescriptor = 'descriptor';
          inputDeviceCooperate.getState(deviceDescriptor).then((data: object) => {
            console.info(`Succeeded in getting the status, data: ${JSON.stringify(data)}.`);
          }).catch((error: BusinessError) => {
            console.error(`Failed to get the status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          });
        })
    }
  }
}
```
