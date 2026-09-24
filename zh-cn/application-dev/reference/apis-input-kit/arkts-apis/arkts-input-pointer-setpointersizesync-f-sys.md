# setPointerSizeSync（系统接口）

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setPointerSizeSync

```TypeScript
function setPointerSizeSync(size: number): void
```

设置鼠标光标大小，使用同步方式进行设置。

**起始版本：** 10

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | number | 是 | 鼠标光标大小，范围为[1, 7]，默认为1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | SystemAPI permission error. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

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
            // 同步设置鼠标指针大小
            pointer.setPointerSizeSync(5);
            console.info(`Succeeded in setting pointer size sync.`);
          } catch (error) {
            console.error(`Failed to set pointer size sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
