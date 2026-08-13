# setTouchpadScrollSwitch（系统接口）

## setTouchpadScrollSwitch

```TypeScript
function setTouchpadScrollSwitch(state: boolean, callback: AsyncCallback<void>): void
```

设置触控板滚轴开关，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pointer-function setTouchpadScrollSwitch(state: boolean, callback: AsyncCallback<void>): void--><!--Device-pointer-function setTouchpadScrollSwitch(state: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | boolean | 是 | 滚轴开关开启的状态，true代表开启，false代表关闭，默认为开启。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当设置触控板滚轴开关成功，err为undefined，否则为错误对象。 |

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
            // 设置触控板滚动开关
            pointer.setTouchpadScrollSwitch(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad scroll switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
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
            // 设置触摸板滚动开关
            pointer.setTouchpadScrollSwitch(true, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Failed to set touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad scroll switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## setTouchpadScrollSwitch

```TypeScript
function setTouchpadScrollSwitch(state: boolean): Promise<void>
```

设置触控板滚轴开关，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pointer-function setTouchpadScrollSwitch(state: boolean): Promise<void>--><!--Device-pointer-function setTouchpadScrollSwitch(state: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | boolean | 是 | 滚轴开关开启的状态，true代表开启，false代表关闭，默认为开启。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

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
            // 设置触摸板滚动开关
            pointer.setTouchpadScrollSwitch(false).then(() => {
              console.info(`Succeeded in setting touchpad scroll switch.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
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
            // 设置触摸板滚动开关
            pointer.setTouchpadScrollSwitch(false).then(() => {
              console.info(`Succeeded in setting touchpad scroll switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

