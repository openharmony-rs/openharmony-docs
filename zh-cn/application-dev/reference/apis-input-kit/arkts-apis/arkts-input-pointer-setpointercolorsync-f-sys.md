# setPointerColorSync（系统接口）

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

<a id="setpointercolorsync"></a>
## setPointerColorSync

```TypeScript
function setPointerColorSync(color: number): void
```

设置鼠标光标颜色，使用同步方式进行设置。

> **说明**：  
>  
> 设置和调试时，需连接外部设备，如鼠标、蓝牙等。

**起始版本：** 10

<!--Device-pointer-function setPointerColorSync(color: int): void--><!--Device-pointer-function setPointerColorSync(color: int): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | number | 是 | 鼠标光标颜色，默认为黑色：0x000000。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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
            // 同步设置鼠标指针颜色
            pointer.setPointerColorSync(0xF6C800);
            console.info(`Succeeded in setting pointer color sync.`);
          } catch (error) {
            console.error(`Failed to set pointer color sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

