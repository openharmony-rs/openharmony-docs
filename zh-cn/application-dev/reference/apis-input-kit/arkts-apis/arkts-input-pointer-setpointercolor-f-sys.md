# setPointerColor（系统接口）

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

## setPointerColor

```TypeScript
function setPointerColor(color: number, callback: AsyncCallback<void>): void
```

设置鼠标光标颜色，使用callback异步回调。

> **说明**：  
>  
> 设置和调试时，需连接外部设备，如鼠标、蓝牙等。

**起始版本：** 10

<!--Device-pointer-function setPointerColor(color: int, callback: AsyncCallback<void>): void--><!--Device-pointer-function setPointerColor(color: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | number | 是 | 鼠标光标颜色，默认为黑色：0x000000。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当设置成功，err为undefined，否则为错误对象。 |

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
            // 设置鼠标光标颜色
            pointer.setPointerColor(0xF6C800, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting pointer color.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## setPointerColor

```TypeScript
function setPointerColor(color: number): Promise<void>
```

设置鼠标光标颜色，使用Promise异步回调。

> **说明**：  
>  
> 设置和调试时，需连接外部设备，如鼠标、蓝牙等。

**起始版本：** 10

<!--Device-pointer-function setPointerColor(color: int): Promise<void>--><!--Device-pointer-function setPointerColor(color: int): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | number | 是 | 鼠标光标颜色，默认为黑色：0x000000。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

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
            // 设置鼠标指针颜色
            pointer.setPointerColor(0xF6C800).then(() => {
              console.info(`Succeeded in setting pointer color.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

