# setPointerSpeedSync（系统接口）

## setPointerSpeedSync

```TypeScript
function setPointerSpeedSync(speed: int): void
```

使用同步方式设置鼠标移动速度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pointer-function setPointerSpeedSync(speed: int): void--><!--Device-pointer-function setPointerSpeedSync(speed: int): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| speed | int | 是 | 鼠标移动速度，范围1-20，默认为10。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |

## 示例

ArkTS-Dyn示例：

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
            let speed = pointer.setPointerSpeedSync(5);
            console.info(`Succeeded in setting pointer speed.`);
          } catch (error) {
            console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

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
           pointer.setPointerSpeedSync(5);
            console.info(`Succeeded in setting pointer speed.`);
          } catch (error) {
            console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

