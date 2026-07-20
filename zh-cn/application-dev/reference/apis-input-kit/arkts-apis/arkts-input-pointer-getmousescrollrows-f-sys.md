# getMouseScrollRows（系统接口）

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

<a id="getmousescrollrows"></a>
## getMouseScrollRows

```TypeScript
function getMouseScrollRows(callback: AsyncCallback<number>): void
```

获取鼠标滚动行数，使用callback异步回调。

**起始版本：** 10

<!--Device-pointer-function getMouseScrollRows(callback: AsyncCallback<int>): void--><!--Device-pointer-function getMouseScrollRows(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当获取鼠标滚动行数成功，err为undefined，number为获取到的滚动行数；否则为错误对象。 |

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
            // 获取鼠标滚动行数
            pointer.getMouseScrollRows((error: BusinessError, rows: number) => {
              if (error) {
                console.error(`Failed to get mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting mouse scroll rows, rows: ${JSON.stringify(rows)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


<a id="getmousescrollrows-1"></a>
## getMouseScrollRows

```TypeScript
function getMouseScrollRows(): Promise<number>
```

获取当前鼠标滚动行数，使用Promise异步回调。

**起始版本：** 10

<!--Device-pointer-function getMouseScrollRows(): Promise<int>--><!--Device-pointer-function getMouseScrollRows(): Promise<int>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回鼠标滚动行数。 |

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
            // 获取鼠标滚动行数
            pointer.getMouseScrollRows().then((rows: number) => {
              console.info(`Succeeded in getting mouse scroll rows, rows: ${JSON.stringify(rows)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

