# getTouchpadScrollDirection（系统接口）

## getTouchpadScrollDirection

```TypeScript
function getTouchpadScrollDirection(callback: AsyncCallback<boolean>): void
```

获取触控板滚轴方向，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pointer-function getTouchpadScrollDirection(callback: AsyncCallback<boolean>): void--><!--Device-pointer-function getTouchpadScrollDirection(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。当获取触控板滚轴方向成功，err为undefined，state是true与手指滑动的方向一致；否则为错误对象。 |

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
            // 获取触控板滚动方向
            pointer.getTouchpadScrollDirection((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Failed to get touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting touchpad scroll direction, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
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
            // 获取触摸板滚动方向
            pointer.getTouchpadScrollDirection((error: BusinessError | null, state: boolean | undefined) => {
              console.info(`Succeeded in getting touchpad scroll direction, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## getTouchpadScrollDirection

```TypeScript
function getTouchpadScrollDirection(): Promise<boolean>
```

获取触控板滚轴方向，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pointer-function getTouchpadScrollDirection(): Promise<boolean>--><!--Device-pointer-function getTouchpadScrollDirection(): Promise<boolean>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示触控板滚轴方向与手指滑动的方向一致；返回false表示触控板滚轴方向与手指滑动的方向相反。默认为true。 |

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
            // 获取触摸板滚动方向
            pointer.getTouchpadScrollDirection().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad scroll direction, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
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
            // 获取触摸板滚动方向
            pointer.getTouchpadScrollDirection().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad scroll direction, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

