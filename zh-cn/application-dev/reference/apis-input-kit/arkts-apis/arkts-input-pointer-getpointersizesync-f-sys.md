# getPointerSizeSync（系统接口）

## getPointerSizeSync

```TypeScript
function getPointerSizeSync(): int
```

获取鼠标光标大小，使用同步方式返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pointer-function getPointerSizeSync(): int--><!--Device-pointer-function getPointerSizeSync(): int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 鼠标光标大小，范围为[1-7]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let pointerSize = pointer.getPointerSizeSync();
            console.info(`Succeeded in getting pointer size sync, pointerSize: ${JSON.stringify(pointerSize)}.`);
          } catch (error) {
            console.error(`Failed to get pointer size sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { pointer } from '@kit.InputKit';
import { BusinessError, AsyncCallback } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let pointerSize = pointer.getPointerSizeSync();
            console.info(`Succeeded in getting pointer size sync, pointerSize: ${JSON.stringify(pointerSize)}.`);
          } catch (error) {
            console.error(`Failed to get pointer size sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

