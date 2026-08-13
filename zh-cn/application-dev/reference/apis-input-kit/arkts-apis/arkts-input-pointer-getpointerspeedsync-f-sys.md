# getPointerSpeedSync（系统接口）

## getPointerSpeedSync

```TypeScript
function getPointerSpeedSync(): int
```

使用同步方式获取当前鼠标移动速度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pointer-function getPointerSpeedSync(): int--><!--Device-pointer-function getPointerSpeedSync(): int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回鼠标移动速度，范围1-20。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
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
            let speed = pointer.getPointerSpeedSync();
            console.info(`Succeeded in getting pointer speed, speed: ${JSON.stringify(speed)}.`);
          } catch (error) {
            console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
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
            let speed = pointer.getPointerSpeedSync();
            console.info(`Succeeded in getting pointer speed, speed: ${JSON.stringify(speed)}.`);
          } catch (error) {
            console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

