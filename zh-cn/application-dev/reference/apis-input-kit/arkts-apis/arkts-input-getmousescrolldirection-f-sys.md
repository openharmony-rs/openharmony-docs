# getMouseScrollDirection（系统接口）

## getMouseScrollDirection

```TypeScript
function getMouseScrollDirection(): Promise<boolean>
```

获取鼠标滚轮滚动方向，使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.INPUT_DEVICE_CONTROLLER

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示鼠标滚轮滚动方向与手指方向一致；返回false表示鼠标滚轮滚动方向与手指方向相反。默认为true。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |
| [3800001](../errorcode-infraredemitter.md#3800001-多模输入服务内部错误) | Input service exception. |

**示例：**

```TypeScript
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button("getMouseScrollDirection")
        .onClick(() => {
          try {
            // 获取鼠标滚动方向
            pointer.getMouseScrollDirection().then((state: boolean) => {
              console.info(`Succeeded in getting mouse scroll direction, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

