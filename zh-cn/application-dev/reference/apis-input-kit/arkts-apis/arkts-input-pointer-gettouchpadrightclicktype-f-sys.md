# getTouchpadRightClickType（系统接口）

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

## getTouchpadRightClickType

```TypeScript
function getTouchpadRightClickType(callback: AsyncCallback<RightClickType>): void
```

获取触控板右键菜单类型，使用callback异步回调。

**起始版本：** 10

<!--Device-pointer-function getTouchpadRightClickType(callback: AsyncCallback<RightClickType>): void--><!--Device-pointer-function getTouchpadRightClickType(callback: AsyncCallback<RightClickType>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;RightClickType&gt; | 是 | 回调函数。当获取触控板右键菜单类型成功，err为undefined，对象是触控板右键菜单类型；否则为错误对象。 |

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
            // 获取触控板右键点击类型
            pointer.getTouchpadRightClickType((error: BusinessError, type: pointer.RightClickType) => {
              if (error) {
                console.error(`Failed to get touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting touchpad right click type, type: ${JSON.stringify(type)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## getTouchpadRightClickType

```TypeScript
function getTouchpadRightClickType(): Promise<RightClickType>
```

获取触控板右键菜单类型，使用Promise异步回调。

**起始版本：** 10

<!--Device-pointer-function getTouchpadRightClickType(): Promise<RightClickType>--><!--Device-pointer-function getTouchpadRightClickType(): Promise<RightClickType>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RightClickType&gt; | Promise对象，返回触控板右键菜单类型。 |

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
            // 获取触摸板右键点击类型
            pointer.getTouchpadRightClickType().then((type: pointer.RightClickType) => {
              console.info(`Succeeded in getting touchpad right click type, type: ${JSON.stringify(type)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

