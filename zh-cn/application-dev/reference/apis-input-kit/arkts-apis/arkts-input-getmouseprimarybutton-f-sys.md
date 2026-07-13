# getMousePrimaryButton（系统接口）

## getMousePrimaryButton

```TypeScript
function getMousePrimaryButton(callback: AsyncCallback<PrimaryButton>): void
```

获取当前鼠标主键，使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;PrimaryButton&gt; | 是 | 回调函数。当获取当前鼠标主键成功，err为undefined，PrimaryButton为获取到的键值；否则为错误对象。 |

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
            // 获取鼠标主键
            pointer.getMousePrimaryButton((error: BusinessError, primary: pointer.PrimaryButton) => {
              if (error) {
                console.error(`Failed to get mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting mouse primary button, primary: ${JSON.stringify(primary)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## getMousePrimaryButton

```TypeScript
function getMousePrimaryButton(): Promise<PrimaryButton>
```

获取当前鼠标主键，使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PrimaryButton&gt; | Promise对象，返回鼠标主键。 |

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
            // 获取鼠标主键
            pointer.getMousePrimaryButton().then((primary: pointer.PrimaryButton) => {
              console.info(`Succeeded in getting mouse primary button, primary: ${JSON.stringify(primary)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

