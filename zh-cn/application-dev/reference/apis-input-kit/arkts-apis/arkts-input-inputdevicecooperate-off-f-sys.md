# off（系统接口）

## 导入模块

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
```

## off('cooperation')

```TypeScript
function off(type: 'cooperation', callback?: AsyncCallback<void>): void
```

关闭监听键鼠穿越状态，使用callback异步回调。

> **说明：**  
>  
> 从 API version 9开始支持，从API version 23开始废弃。建议使用  
> [cooperate.off](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-cooperate-off-f-sys.md#off-2)  
> 替代。

**起始版本：** 9

**废弃版本：** 23

**替代接口：** off

<!--Device-inputDeviceCooperate-function off(type: 'cooperation', callback?: AsyncCallback<void>): void--><!--Device-inputDeviceCooperate-function off(type: 'cooperation', callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Cooperator

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cooperation' | 是 | 注册类型，取值“cooperation”。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 否 | 回调函数。当取消注册成功，err为undefined，否则为错误对象。若无此参数，则取消当前应用注册的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |

**示例：**

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
          // 取消注册单个回调函数
          let callbackOn = (error: BusinessError | undefined, data: { deviceDescriptor: string, eventMsg: EventMsg }) => {
            if (error) {
              console.error(`Failed to monitor cooperation, Code: ${error.code}, message: ${error.message}.`);
              return;
            }
            console.info(`Succeeded in monitoring cooperation, data: ${JSON.stringify(data)}.`);
          };
          try {
            inputDeviceCooperate.on('cooperation', callbackOn);
            inputDeviceCooperate.off('cooperation', callbackOn);
          } catch (error) {
            console.error(`Failed to unregister callback function, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

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
          // 取消注册所有回调函数
          let callback = (error: BusinessError | undefined, data: { deviceDescriptor: string, eventMsg: EventMsg }) => {
            if (error) {
              console.error(`Failed to monitor cooperation, Code: ${error.code}, message: ${error.message}.`);
              return;
            }
            console.info(`Succeeded in monitoring cooperation, data: ${JSON.stringify(data)}.`);
          };
          try {
            inputDeviceCooperate.on('cooperation', callback);
            inputDeviceCooperate.off('cooperation');
          } catch (error) {
            console.error(`Failed to unregister callback function, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

