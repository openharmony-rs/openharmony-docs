# on（系统接口）

## 导入模块

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
```

## on('cooperation')

```TypeScript
function on(type: 'cooperation', callback: AsyncCallback<{ deviceDescriptor: string, eventMsg: EventMsg }>): void
```

注册监听键鼠穿越状态，使用callback异步回调。

**起始版本：** 9

**废弃版本：** 23

**替代接口：** [on](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-cooperate-on-f-sys.md)

**系统能力：** SystemCapability.MultimodalInput.Input.Cooperator

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cooperation' | 是 | 注册类型，取值'cooperation'。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{ deviceDescriptor: string, eventMsg: EventMsg }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

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
          let callback = (error: BusinessError | undefined, data: { deviceDescriptor: string, eventMsg: EventMsg }) => {
            if (error) {
              console.error(`Failed to monitor cooperation, Code: ${error.code}, message: ${error.message}.`);
              return;
            }
            console.info(`Succeeded in monitoring cooperation, data: ${JSON.stringify(data)}.`);
          };
          try {
            inputDeviceCooperate.on('cooperation', callback);
          } catch (error) {
            console.error(`Failed to register keyboard and mouse traversal status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
