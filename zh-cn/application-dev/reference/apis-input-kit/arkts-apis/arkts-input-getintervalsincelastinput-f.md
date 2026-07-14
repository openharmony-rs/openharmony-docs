# getIntervalSinceLastInput

## getIntervalSinceLastInput

```TypeScript
function getIntervalSinceLastInput(): Promise<number>
```

获取距离上次系统输入事件的时间间隔（包含设备休眠时间），使用Promise异步回调。

**起始版本：** 14

**系统能力：** SystemCapability.MultimodalInput.Input.InputDevice

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回距离上次系统输入事件的时间间隔，单位为微秒（μs）。 |

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
            // 获取距上次输入的时间间隔
            inputDevice.getIntervalSinceLastInput().then((timeInterval: number) => {
              console.info(`Succeeded in getting interval since last input: ${JSON.stringify(timeInterval)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get interval since last input, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get interval since last input, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

