# getPointerSpeed（系统接口）

## 导入模块

```TypeScript
import { pointer } from '@kit.InputKit';
```

## getPointerSpeed

```TypeScript
function getPointerSpeed(callback: AsyncCallback<number>): void
```

获取鼠标移动速度，使用callback异步回调。

**起始版本：** 9

<!--Device-pointer-function getPointerSpeed(callback: AsyncCallback<int>): void--><!--Device-pointer-function getPointerSpeed(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当获取鼠标移动速度成功，err为undefined，number为鼠标移动速度；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |

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
            // 获取鼠标光标速度
            pointer.getPointerSpeed((error: BusinessError, speed: number) => {
              if (error) {
                console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting pointer speed, speed: ${JSON.stringify(speed)}.`);
            });
          } catch (error) {
            console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## getPointerSpeed

```TypeScript
function getPointerSpeed(): Promise<number>
```

获取当前鼠标移动速度，使用Promise异步回调。

**起始版本：** 9

<!--Device-pointer-function getPointerSpeed(): Promise<int>--><!--Device-pointer-function getPointerSpeed(): Promise<int>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回鼠标移动速度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |

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
            // 获取鼠标指针速度
            pointer.getPointerSpeed().then(speed => {
              console.info(`Succeeded in getting pointer speed, speed: ${JSON.stringify(speed)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

