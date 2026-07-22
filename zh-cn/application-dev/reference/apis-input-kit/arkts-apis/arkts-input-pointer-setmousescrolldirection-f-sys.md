# setMouseScrollDirection（系统接口）

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setMouseScrollDirection

```TypeScript
function setMouseScrollDirection(inverted: boolean): Promise<void>
```

设置鼠标滚轮滚动的方向，使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.INPUT_DEVICE_CONTROLLER

<!--Device-pointer-function setMouseScrollDirection(inverted: boolean): Promise<void>--><!--Device-pointer-function setMouseScrollDirection(inverted: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inverted | boolean | 是 | inverted为鼠标滚轮滚动的方向。<br>true与鼠标滚轮滚动的手指方向一致，false与鼠标滚轮滚动的手指方向相反。<br>默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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
      Button('setMouseScrollDirection')
        .onClick(() => {
          try {
            // 设置鼠标滚动方向
            pointer.setMouseScrollDirection(false).then(() => {
              console.info(`Succeeded in setting mouse scroll direction.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

