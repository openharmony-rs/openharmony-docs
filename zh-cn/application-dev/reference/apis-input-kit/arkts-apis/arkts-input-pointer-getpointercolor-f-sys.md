# getPointerColor（系统接口）

## getPointerColor

```TypeScript
function getPointerColor(callback: AsyncCallback<int>): void
```

获取鼠标光标颜色，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pointer-function getPointerColor(callback: AsyncCallback<int>): void--><!--Device-pointer-function getPointerColor(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 回调函数。当获取鼠标光标颜色成功，err为undefined，number是获取的鼠标光标颜色；否则为错误对象。 |

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
            // 获取鼠标光标颜色
            pointer.getPointerColor((error: BusinessError, color: number) => {
              if (error) {
                console.error(`Failed to get pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting pointer color, color: ${JSON.stringify(color)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
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
            // 获取鼠标指针颜色
            pointer.getPointerColor((error: BusinessError<void>|null, color: int|undefined) => {
              if (error) {
                console.error(`Failed to get pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting pointer color, color: ${JSON.stringify(color)}.`);
            });
          } catch (error) {
            console.error(`Failed to get pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## getPointerColor

```TypeScript
function getPointerColor(): Promise<int>
```

获取当前鼠标光标颜色，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pointer-function getPointerColor(): Promise<int>--><!--Device-pointer-function getPointerColor(): Promise<int>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回鼠标光标颜色。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
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
            // 获取鼠标指针颜色
            pointer.getPointerColor().then((color: number) => {
              console.info(`Succeeded in getting pointer color, color: ${JSON.stringify(color)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
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
            // 获取鼠标指针颜色
            pointer.getPointerColor().then((color: int) => {
              console.info(`Succeeded in getting pointer color, color: ${JSON.stringify(color)}.`);
            });
          } catch (error) {
            console.error(`Failed to get pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

