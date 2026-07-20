# setMousePrimaryButton（系统接口）

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

<a id="setmouseprimarybutton"></a>
## setMousePrimaryButton

```TypeScript
function setMousePrimaryButton(primary: PrimaryButton, callback: AsyncCallback<void>): void
```

设置鼠标主键，使用callback异步回调。

**起始版本：** 10

<!--Device-pointer-function setMousePrimaryButton(primary: PrimaryButton, callback: AsyncCallback<void>): void--><!--Device-pointer-function setMousePrimaryButton(primary: PrimaryButton, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| primary | [PrimaryButton](arkts-input-pointer-primarybutton-e.md) | 是 | 鼠标主键类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置鼠标主键成功，err为undefined，否则为错误对象。 |

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
            // 设置鼠标主键
            pointer.setMousePrimaryButton(pointer.PrimaryButton.RIGHT, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting mouse primary button.`);
            });
          } catch (error) {
            console.error(`Failed to set mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


<a id="setmouseprimarybutton-1"></a>
## setMousePrimaryButton

```TypeScript
function setMousePrimaryButton(primary: PrimaryButton): Promise<void>
```

设置鼠标主键，使用Promise异步回调。

**起始版本：** 10

<!--Device-pointer-function setMousePrimaryButton(primary: PrimaryButton): Promise<void>--><!--Device-pointer-function setMousePrimaryButton(primary: PrimaryButton): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| primary | [PrimaryButton](arkts-input-pointer-primarybutton-e.md) | 是 | 鼠标主键类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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
            // 设置鼠标主键
            pointer.setMousePrimaryButton(pointer.PrimaryButton.RIGHT).then(() => {
              console.info(`Succeeded in setting mouse primary button.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

