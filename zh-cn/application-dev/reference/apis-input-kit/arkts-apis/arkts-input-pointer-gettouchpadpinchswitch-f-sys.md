# getTouchpadPinchSwitch（系统接口）

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

## getTouchpadPinchSwitch

```TypeScript
function getTouchpadPinchSwitch(callback: AsyncCallback<boolean>): void
```

获取触控板双指捏合功能开启状态，使用callback异步回调。

**起始版本：** 10

<!--Device-pointer-function getTouchpadPinchSwitch(callback: AsyncCallback<boolean>): void--><!--Device-pointer-function getTouchpadPinchSwitch(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当获取触控板双指捏合功能开启状态成功，err为undefined，state是true代表功能开启，false代表功能关闭，默认开启；否则为错误对象。 |

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
            // 获取触控板捏合开关
            pointer.getTouchpadPinchSwitch((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Failed to get touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting touchpad pinch switch, state: ${JSON.stringify(state)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## getTouchpadPinchSwitch

```TypeScript
function getTouchpadPinchSwitch(): Promise<boolean>
```

获取触控板双指捏合功能开启状态，使用Promise异步回调。

**起始版本：** 10

<!--Device-pointer-function getTouchpadPinchSwitch(): Promise<boolean>--><!--Device-pointer-function getTouchpadPinchSwitch(): Promise<boolean>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示触控板双指捏合功能开启；返回false表示触控板双指捏合功能关闭。默认开启。 |

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
            // 获取触摸板捏合开关
            pointer.getTouchpadPinchSwitch().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad pinch switch, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

