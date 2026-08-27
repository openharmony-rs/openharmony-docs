# setPointerSpeed（系统接口）

## 导入模块

```TypeScript
```

## setPointerSpeed

```TypeScript
function setPointerSpeed(speed: number, callback: AsyncCallback<void>): void
```

设置鼠标移动速度，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| speed | number | 是 | 鼠标移动速度，取值范围[1, 20]，默认为10。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当设置鼠标移动速度成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

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
            // 设置鼠标光标速度
            pointer.setPointerSpeed(5, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting pointer speed.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        });
    }
  }
}
```


## setPointerSpeed

```TypeScript
function setPointerSpeed(speed: number): Promise<void>
```

设置鼠标移动速度，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| speed | number | 是 | 鼠标移动速度，取值范围[1, 20]，默认为10。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

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
            // 设置鼠标指针速度
            pointer.setPointerSpeed(5).then(() => {
              console.info(`Succeeded in setting pointer speed.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```
