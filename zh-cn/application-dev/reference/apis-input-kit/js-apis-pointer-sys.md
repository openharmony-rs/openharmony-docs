# @ohos.multimodalInput.pointer (鼠标光标)(系统接口)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

鼠标光标管理模块，用于查询和设置鼠标光标相关属性。

> **说明**：
>
>- 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.multimodalInput.pointer (鼠标光标)](js-apis-pointer.md)。

## 导入模块

```js
import { pointer } from '@kit.InputKit';
```

## pointer.setPointerSpeed

ArkTS-Dyn: setPointerSpeed(speed: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: setPointerSpeed(speed: int, callback: AsyncCallback&lt;void&gt;): void

设置鼠标移动速度，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| speed    | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标移动速度，范围1-20，默认为10。   |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数。当设置鼠标移动速度成功，err为undefined，否则为错误对象。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息          |
| -------- | ----------------- |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types.3.Parameter verification failed. |


**示例**：

ArkTS-Dyn示例:

```js
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
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 设置鼠标指针速度
            pointer.setPointerSpeed(5, (error:  BusinessError<void>|null, info: undefined) => {
              if (error) {
                console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting pointer speed.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerSpeed

ArkTS-Dyn: setPointerSpeed(speed: number): Promise&lt;void&gt;

ArkTS-Sta: setPointerSpeed(speed: int): Promise&lt;void&gt;

设置鼠标移动速度，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| speed | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标移动速度，范围1-20，默认为10。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息          |
| -------- | ----------------- |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types.3.Parameter verification failed. |


**示例**：

ArkTS-Dyn示例：

```js
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

ArkTS-Sta示例：

```ts
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
            // 设置鼠标指针速度
            pointer.setPointerSpeed(5).then(() => {
              console.info(`Succeeded in setting pointer speed.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerSpeedSync<sup>10+</sup>

ArkTS-Dyn: setPointerSpeedSync(speed: number): void

ArkTS-Sta: setPointerSpeedSync(speed: int): void

使用同步方式设置鼠标移动速度。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| speed | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标移动速度，范围1-20，默认为10。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let speed = pointer.setPointerSpeedSync(5);
            console.info(`Succeeded in setting pointer speed.`);
          } catch (error) {
            console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
           pointer.setPointerSpeedSync(5);
            console.info(`Succeeded in setting pointer speed.`);
          } catch (error) {
            console.error(`Failed to set pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerSpeed

ArkTS-Dyn: getPointerSpeed(callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getPointerSpeed(callback: AsyncCallback&lt;int&gt;): void

获取鼠标移动速度，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br> ArkTS-Sta: AsyncCallback&lt;int&gt;| 是    | 回调函数。当获取鼠标移动速度成功，err为undefined，number为鼠标移动速度；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | Permission denied, non-system app called system api. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


**示例**：

ArkTS-Dyn示例:

```js
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

ArkTS-Sta示例:

```ts
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
            // 获取鼠标指针速度
            pointer.getPointerSpeed((error: BusinessError<void>|null, speed: int|undefined) => {
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

## pointer.getPointerSpeed

ArkTS-Dyn: getPointerSpeed(): Promise&lt;number&gt;

ArkTS-Sta: getPointerSpeed(): Promise&lt;int&gt;

获取当前鼠标移动速度，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;int&gt; | Promise对象，返回鼠标移动速度。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | Permission denied, non-system app called system api. |

**示例**：

ArkTS-Dyn示例:

```js
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

ArkTS-Sta示例:

```ts
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
            // 获取鼠标指针速度
            pointer.getPointerSpeed().then((speed: int) => {
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

## pointer.getPointerSpeedSync<sup>10+</sup>

ArkTS-Dyn: getPointerSpeedSync(): number

ArkTS-Sta: getPointerSpeedSync(): int

使用同步方式获取当前鼠标移动速度。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: number<br/>ArkTS-Sta: int | 返回鼠标移动速度。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let speed = pointer.getPointerSpeedSync();
            console.info(`Succeeded in getting pointer speed, speed: ${JSON.stringify(speed)}.`);
          } catch (error) {
            console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            let speed = pointer.getPointerSpeedSync();
            console.info(`Succeeded in getting pointer speed, speed: ${JSON.stringify(speed)}.`);
          } catch (error) {
            console.error(`Failed to get pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setHoverScrollState<sup>10+</sup>

setHoverScrollState(state: boolean, callback: AsyncCallback&lt;void&gt;): void

设置鼠标悬停滚动开关状态，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state    | boolean                    | 是    | 鼠标悬停滚动开关状态。true代表开关开启，false代表开关关闭，默认开启。   |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数。当设置鼠标悬停滚动开关状态成功，err为undefined，否则为错误对象。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 设置鼠标悬停滚动状态
            pointer.setHoverScrollState(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting mouse hover scroll.`);
            });
          } catch (error) {
            console.error(`Failed to set mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 设置鼠标悬停滚动状态
            pointer.setHoverScrollState(true, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Failed to set mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting mouse hover scroll.`);
            });
          } catch (error) {
            console.error(`Failed to set mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setHoverScrollState<sup>10+</sup>

setHoverScrollState(state: boolean): Promise&lt;void&gt;

设置鼠标悬停滚动开关状态，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean | 是    | 鼠标悬停滚动开关状态。true代表开关开启，false代表开关关闭，默认开启。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 设置鼠标悬停滚动状态
            pointer.setHoverScrollState(true).then(() => {
              console.info(`Succeeded in setting mouse hover scroll.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 设置鼠标悬停滚动状态
            pointer.setHoverScrollState(true).then(() => {
              console.info(`Succeeded in setting mouse hover scroll.`);
            });
          } catch (error) {
            console.error(`Failed to set mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getHoverScrollState<sup>10+</sup>

getHoverScrollState(callback: AsyncCallback&lt;boolean&gt;): void

获取鼠标悬停滚动开关状态，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;boolean&gt; | 是    | 回调函数。当获取鼠标悬停滚动开关状态成功，err为undefined，true代表开关开启，false代表开关关闭，默认开启；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 获取鼠标悬停滚动状态
            pointer.getHoverScrollState((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting mouse hover scroll, state: ${JSON.stringify(state)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 获取鼠标悬停滚动状态
            pointer.getHoverScrollState((error: BusinessError | null, state: boolean | undefined) => {
              console.info(`Succeeded in getting mouse hover scroll, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getHoverScrollState<sup>10+</sup>

getHoverScrollState(): Promise&lt;boolean&gt;

获取当前鼠标悬停滚动开关状态，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示鼠标悬停滚动开关开启；返回false表示鼠标悬停滚动开关关闭。默认开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 获取鼠标悬停滚动状态
            pointer.getHoverScrollState().then((state: boolean) => {
              console.info(`Succeeded in getting mouse hover scroll, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 获取鼠标悬停滚动状态
            pointer.getHoverScrollState().then((state: boolean) => {
              console.info(`Succeeded in getting mouse hover scroll, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get mouse hover scroll, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setMousePrimaryButton<sup>10+</sup>

setMousePrimaryButton(primary: PrimaryButton, callback: AsyncCallback&lt;void&gt;): void

设置鼠标主键，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型                      | 必填  | 说明                                    |
| -------- | ------------------------- | ----  | ------------------------------------- |
| primary  | [PrimaryButton](js-apis-pointer.md#primarybutton10)   | 是    | 鼠标主键类型。   |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数。当设置鼠标主键成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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

ArkTS-Sta示例:

```ts
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
            // 设置鼠标主键
            pointer.setMousePrimaryButton(pointer.PrimaryButton.RIGHT, (error: BusinessError<void>|null, data: undefined) => {
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

## pointer.setMousePrimaryButton<sup>10+</sup>

setMousePrimaryButton(primary: PrimaryButton): Promise&lt;void&gt;

设置鼠标主键，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| primary | [PrimaryButton](js-apis-pointer.md#primarybutton10) | 是    | 鼠标主键类型。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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

ArkTS-Sta示例：

```ts
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
            // 设置鼠标主键
            pointer.setMousePrimaryButton(pointer.PrimaryButton.RIGHT).then(() => {
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

## pointer.getMousePrimaryButton<sup>10+</sup>

getMousePrimaryButton(callback: AsyncCallback&lt;PrimaryButton&gt;): void

获取当前鼠标主键，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;[PrimaryButton](js-apis-pointer.md#primarybutton10)&gt; | 是    | 回调函数。当获取当前鼠标主键成功，err为undefined，PrimaryButton为获取到的键值；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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

ArkTS-Sta示例:

```ts
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
            // 获取鼠标主键
            pointer.getMousePrimaryButton((error: BusinessError<void>|null, primary: pointer.PrimaryButton|undefined) => {
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

## pointer.getMousePrimaryButton<sup>10+</sup>

getMousePrimaryButton(): Promise&lt;PrimaryButton&gt;

获取当前鼠标主键，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise&lt;[PrimaryButton](js-apis-pointer.md#primarybutton10)&gt; | Promise对象，返回鼠标主键。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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

ArkTS-Sta示例：

```ts
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
            // 获取鼠标主键
            pointer.getMousePrimaryButton().then((primary: pointer.PrimaryButton) => {
              console.info(`Succeeded in getting mouse primary button, primary: ${JSON.stringify(primary)}.`);
            });
          } catch (error) {
            console.error(`Failed to get mouse primary button, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setMouseScrollRows<sup>10+</sup>

setMouseScrollRows(rows: number, callback: AsyncCallback&lt;void&gt;): void

设置鼠标滚动行数，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| rows     | ArkTS-Dyn: number<br/>ArkTS-Sta: int                    | 是    | 鼠标滚动行数，范围1-100，默认为3。   |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数。当设置鼠标滚动行数成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 设置鼠标滚动行数
            pointer.setMouseScrollRows(1, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting mouse scroll rows.`);
            });
          } catch (error) {
            console.error(`Failed to set mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 设置鼠标滚动行数
            pointer.setMouseScrollRows(1, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Failed to set mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting mouse scroll rows.`);
            });
          } catch (error) {
            console.error(`Failed to set mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setMouseScrollRows<sup>10+</sup>

ArkTS-Dyn: setMouseScrollRows(rows: number): Promise&lt;void&gt;

ArkTS-Sta: setMouseScrollRows(rows: int): Promise&lt;void&gt;

设置鼠标滚动行数，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| rows  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标滚动行数，范围1-100，默认为3。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 设置鼠标滚动行数
            pointer.setMouseScrollRows(20).then(() => {
              console.info(`Succeeded in setting mouse scroll rows.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 设置鼠标滚动行数
            pointer.setMouseScrollRows(20).then(() => {
              console.info(`Succeeded in setting mouse scroll rows.`);
            });
          } catch (error) {
            console.error(`Failed to set mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getMouseScrollRows<sup>10+</sup>

ArkTS-Dyn: getMouseScrollRows(callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getMouseScrollRows(callback: AsyncCallback&lt;int&gt;): void

获取鼠标滚动行数，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br>ArkTS-Sta: AsyncCallback&lt;int&gt; | 是    | 回调函数。当获取鼠标滚动行数成功，err为undefined，number为获取到的滚动行数；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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

ArkTS-Sta示例:

```ts
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
            // 获取鼠标滚动行数
            pointer.getMouseScrollRows((error: BusinessError<void>|null, rows: int|undefined) => {
              if (error) {
                console.error(`Failed to get mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting mouse scroll rows, rows: ${JSON.stringify(rows)}.`);
            });
          } catch (error) {
            console.error(`Failed to get mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getMouseScrollRows<sup>10+</sup>

ArkTS-Dyn: getMouseScrollRows(): Promise&lt;number&gt;

ArkTS-Sta: getMouseScrollRows(): Promise&lt;int&gt;

获取当前鼠标滚动行数，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;int&gt; | Promise对象，返回鼠标滚动行数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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

ArkTS-Sta示例：

```ts
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
            // 获取鼠标滚动行数
            pointer.getMouseScrollRows().then((rows: int) => {
              console.info(`Succeeded in getting mouse scroll rows, rows: ${JSON.stringify(rows)}.`);
            });
          } catch (error) {
            console.error(`Failed to get mouse scroll rows, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadScrollSwitch<sup>10+</sup>

setTouchpadScrollSwitch(state: boolean, callback: AsyncCallback\<void>): void

设置触控板滚轴开关，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | 是    | 滚轴开关开启的状态，true代表开启，false代表关闭，默认为开启。   |
| callback | AsyncCallback\<void> | 是    | 回调函数。当设置触控板滚轴开关成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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

```ts
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

## pointer.setTouchpadScrollSwitch<sup>10+</sup>

setTouchpadScrollSwitch(state: boolean): Promise\<void>

设置触控板滚轴开关，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| 是    |  滚轴开关开启的状态，true代表开启，false代表关闭，默认为开启。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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

```ts
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

## pointer.getTouchpadScrollSwitch<sup>10+</sup>

getTouchpadScrollSwitch(callback:  AsyncCallback\<boolean>): void

获取触控板滚轴能力开启状态，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | 是    | 回调函数。当获取触控板滚轴能力开启状态成功，err为undefined，state是true代表开启，false代表关闭，默认开启；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 获取触摸板滚动开关
            pointer.getTouchpadScrollSwitch((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Failed to get touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting touchpad scroll switch, state: ${JSON.stringify(state)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 获取触摸板滚动开关
            pointer.getTouchpadScrollSwitch((error: BusinessError | null, state: boolean | undefined) => {
              console.info(`Succeeded in getting touchpad scroll switch, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadScrollSwitch<sup>10+</sup>

getTouchpadScrollSwitch(): Promise\<boolean>

获取触控板滚轴能力开启状态，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise对象。返回true表示触控板滚轴能力开启；返回false表示触控板滚轴能力关闭。默认为开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 获取触摸板滚动开关
            pointer.getTouchpadScrollSwitch().then((state) => {
              console.info(`Succeeded in getting touchpad scroll switch, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 获取触摸板滚动开关
            pointer.getTouchpadScrollSwitch().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad scroll switch, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad scroll switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadScrollDirection<sup>10+</sup>

setTouchpadScrollDirection(state: boolean, callback: AsyncCallback\<void>): void

设置触控板滚轴的方向，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | 是    | state为触控板滚轴的方向。<br>true与手指滑动的方向一致，false与手指滑动的方向相反。<br>默认为true。   |
| callback | AsyncCallback\<void> | 是    | 回调函数。当设置触控板滚轴方向成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 设置触摸板滚动方向
            pointer.setTouchpadScrollDirection(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad scroll direction.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 设置触摸板滚动方向
            pointer.setTouchpadScrollDirection(true, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Failed to set touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad scroll direction.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadScrollDirection<sup>10+</sup>

setTouchpadScrollDirection(state: boolean): Promise\<void>

设置触控板滚轴的方向，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| 是    |  state为触控板滚轴的方向。<br>true与手指滑动的方向一致，false与手指滑动的方向相反。<br>默认为true。|

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 设置触摸板滚动方向
            pointer.setTouchpadScrollDirection (false).then(() => {
              console.info(`Succeeded in setting touchpad scroll direction.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 设置触摸板滚动方向
            pointer.setTouchpadScrollDirection(false).then(() => {
              console.info(`Succeeded in setting touchpad scroll direction.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadScrollDirection<sup>10+</sup>

getTouchpadScrollDirection(callback:  AsyncCallback\<boolean>): void

获取触控板滚轴方向，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | 是    | 回调函数。当获取触控板滚轴方向成功，err为undefined，state是true与手指滑动的方向一致；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            pointer.getTouchpadScrollDirection ((error: BusinessError, state: boolean) => {
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

```ts
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

## pointer.getTouchpadScrollDirection<sup>10+</sup>

getTouchpadScrollDirection(): Promise\<boolean>

获取触控板滚轴方向，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise对象。返回true表示触控板滚轴方向与手指滑动的方向一致；返回false表示触控板滚轴方向与手指滑动的方向相反。默认为true。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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

```ts
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

## pointer.setTouchpadTapSwitch<sup>10+</sup>

setTouchpadTapSwitch(state: boolean, callback: AsyncCallback\<void>): void

设置触控板轻触功能开关，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | 是    |触控板轻触功能开关开启状态。 true代表轻触开启，false代表轻触关闭，默认开启。   |
| callback | AsyncCallback\<void> | 是    | 回调函数。当设置触控板轻触功能开关成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 设置触摸板点击开关
            pointer.setTouchpadTapSwitch(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad tap switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 设置触摸板点击开关
            pointer.setTouchpadTapSwitch(true, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Failed to set touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad tap switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadTapSwitch <sup>10+</sup>

setTouchpadTapSwitch(state: boolean): Promise\<void>

设置触控板轻触功能开关，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| 是    |  触控板轻触功能开关开启状态， true代表轻触开启，false代表轻触关闭，默认开启。  |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 设置触摸板点击开关
            pointer.setTouchpadTapSwitch(false).then(() => {
              console.info(`Succeeded in setting touchpad tap switch.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 设置触摸板点击开关
            pointer.setTouchpadTapSwitch(false).then(() => {
              console.info(`Succeeded in setting touchpad tap switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadTapSwitch<sup>10+</sup>

getTouchpadTapSwitch(callback:  AsyncCallback\<boolean>): void

获取触控板轻触能力开启状态，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | 是    | 回调函数。当获取触控板轻触功能开启状态成功，err为undefined，state是true代表开启，false代表关闭，默认开启；否则为错误对象。 |
**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 获取触摸板点击开关
            pointer.getTouchpadTapSwitch((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Failed to get touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting touchpad tap switch, state: ${JSON.stringify(state)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 获取触摸板点击开关
            pointer.getTouchpadTapSwitch((error: BusinessError | null, state: boolean | undefined) => {
              console.info(`Succeeded in getting touchpad tap switch, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadTapSwitch<sup>10+</sup>

getTouchpadTapSwitch(): Promise\<boolean>

获取触控板轻触功能开启状态，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise对象。返回true表示触控板轻触功能开启；返回false表示触控板轻触功能关闭。默认开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 获取触摸板点击开关
            pointer.getTouchpadTapSwitch().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad tap switch, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 获取触摸板点击开关
            pointer.getTouchpadTapSwitch().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad tap switch, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad tap switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadPointerSpeed<sup>10+</sup>

ArkTS-Dyn: setTouchpadPointerSpeed(speed: number, callback: AsyncCallback\<void>): void

ArkTS-Sta: setTouchpadPointerSpeed(speed: int, callback: AsyncCallback\<void>): void

设置触控板光标移动速度，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| speed | ArkTS-Dyn: number<br/>ArkTS-Sta: int                    | 是    |speed代表光标移动速度。speed取值范围[1,11]，默认6。  |
| callback | AsyncCallback\<void> | 是    | 回调函数。当设置触控板光标移动速度成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 设置触摸板指针速度
            pointer.setTouchpadPointerSpeed(1, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad pointer speed.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 设置触摸板指针速度
            pointer.setTouchpadPointerSpeed(1, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Failed to set touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad pointer speed.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadPointerSpeed<sup>10+</sup>

ArkTS-Dyn: setTouchpadPointerSpeed(speed: number): Promise\<void>

ArkTS-Sta: setTouchpadPointerSpeed(speed: int): Promise\<void>

设置触控板光标移动速度，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| speed| ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | speed代表光标移动速度。speed取值范围[1,11]，默认6。    |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 设置触摸板指针速度
            pointer.setTouchpadPointerSpeed(10).then(() => {
              console.info(`Succeeded in setting touchpad pointer speed.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 设置触摸板指针速度
            pointer.setTouchpadPointerSpeed(10).then(() => {
              console.info(`Succeeded in setting touchpad pointer speed.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadPointerSpeed<sup>10+</sup>

ArkTS-Dyn: getTouchpadPointerSpeed(callback: AsyncCallback\<number>): void

ArkTS-Sta: getTouchpadPointerSpeed(callback: AsyncCallback\<int>): void

获取触控板光标移动速度，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | ArkTS-Dyn: AsyncCallback\<number><br>ArkTS-Sta: AsyncCallback\<int> | 是    | 回调函数。当获取触控板光标移动速度成功，err为undefined，number是获取的触控板光标移动速度；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 获取触摸板指针速度
            pointer.getTouchpadPointerSpeed((error: BusinessError, speed: number) => {
              if (error) {
                console.error(`Failed to get touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting touchpad pointer speed, speed: ${JSON.stringify(speed)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 获取触摸板指针速度
            pointer.getTouchpadPointerSpeed((error: BusinessError<void>|null, speed: int|undefined) => {
              if (error) {
                console.error(`Failed to get touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting touchpad pointer speed, speed: ${JSON.stringify(speed)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadPointerSpeed<sup>10+</sup>

ArkTS-Dyn: getTouchpadPointerSpeed(): Promise\<number>

ArkTS-Sta: getTouchpadPointerSpeed(): Promise\<int>

获取触控板光标移动速度，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象，返回触控板光标移动速度。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 获取触摸板指针速度
            pointer.getTouchpadPointerSpeed().then((speed: number) => {
              console.info(`Succeeded in getting touchpad pointer speed, speed: ${JSON.stringify(speed)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 获取触摸板指针速度
            pointer.getTouchpadPointerSpeed().then((speed: int) => {
              console.info(`Succeeded in getting touchpad pointer speed, speed: ${JSON.stringify(speed)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad pointer speed, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadPinchSwitch<sup>10+</sup>

setTouchpadPinchSwitch(state: boolean, callback: AsyncCallback\<void>): void

设置触控板双指捏合功能开关，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | 是    |触控板双指捏合功能开关开启状态。 true代表开启，false代表关闭，默认开启。   |
| callback | AsyncCallback\<void> | 是    | 回调函数。当设置触控板双指捏合功能开关成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 设置触摸板捏合开关
            pointer.setTouchpadPinchSwitch(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad pinch switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 设置触摸板捏合开关
            pointer.setTouchpadPinchSwitch(true, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Failed to set touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad pinch switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadPinchSwitch<sup>10+</sup>

setTouchpadPinchSwitch(state: boolean): Promise\<void>

设置触控板双指捏合功能开关，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| 是    |  触控板双指捏合功能开关开启状态。 true代表开启，false代表关闭，默认开启。  |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 设置触摸板捏合开关
            pointer.setTouchpadPinchSwitch(false).then(() => {
              console.info(`Succeeded in setting touchpad pinch switch.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 设置触摸板捏合开关
            pointer.setTouchpadPinchSwitch(false).then(() => {
              console.info(`Succeeded in setting touchpad pinch switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadPinchSwitch<sup>10+</sup>

getTouchpadPinchSwitch(callback:  AsyncCallback\<boolean>): void

获取触控板双指捏合功能开启状态，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | 是    | 回调函数。当获取触控板双指捏合功能开启状态成功，err为undefined，state是true代表功能开启，false代表功能关闭，默认开启；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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

ArkTS-Sta示例:

```ts
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
            // 获取触摸板捏合开关
            pointer.getTouchpadPinchSwitch((error: BusinessError | null, state: boolean | undefined) => {
              console.info(`Succeeded in getting touchpad pinch switch, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadPinchSwitch<sup>10+</sup>

getTouchpadPinchSwitch(): Promise\<boolean>

获取触控板双指捏合功能开启状态，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise对象。返回true表示触控板双指捏合功能开启；返回false表示触控板双指捏合功能关闭。默认开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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

ArkTS-Sta示例：

```ts
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
            // 获取触摸板捏合开关
            pointer.getTouchpadPinchSwitch().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad pinch switch, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad pinch switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadSwipeSwitch<sup>10+</sup>

setTouchpadSwipeSwitch(state: boolean, callback: AsyncCallback\<void>): void

设置触控板多指滑动功能开关，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | 是    |触控板多指滑动开关开启状态。 true代表多指滑动开启，false代表多指滑动关闭，默认开启。   |
| callback | AsyncCallback\<void> | 是    | 回调函数。当设置触控板多指滑动功能开关成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 设置触摸板滑动开关
            pointer.setTouchpadSwipeSwitch(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad swipe switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 设置触摸板滑动开关
            pointer.setTouchpadSwipeSwitch(true, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Failed to set touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad swipe switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadSwipeSwitch<sup>10+</sup>

setTouchpadSwipeSwitch(state: boolean): Promise\<void>

设置触控板多指滑动功能开关，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| 是    |  触控板多指滑动功能开关开启状态。 true代表多指滑动开启，false代表多指滑动关闭，默认开启。  |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 设置触摸板滑动开关
            pointer.setTouchpadSwipeSwitch(false).then(() => {
              console.info(`Succeeded in setting touchpad swipe switch.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 设置触摸板滑动开关
            pointer.setTouchpadSwipeSwitch(false).then(() => {
              console.info(`Succeeded in setting touchpad swipe switch.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadSwipeSwitch<sup>10+</sup>

getTouchpadSwipeSwitch(callback:  AsyncCallback\<boolean>): void

获取触控板多指滑动功能开启状态，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | 是    | 回调函数。当获取触控板多指滑动功能开启状态成功，err为undefined，state是true代表多指滑动开启，false代表多指滑动关闭，默认开启；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 获取触摸板滑动开关
            pointer.getTouchpadSwipeSwitch((error: BusinessError, state: boolean) => {
              console.info(`Succeeded in getting touchpad swipe switch, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 获取触摸板滑动开关
            pointer.getTouchpadSwipeSwitch((error: BusinessError | null, state: boolean | undefined) => {
              console.info(`Succeeded in getting touchpad swipe switch, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadSwipeSwitch<sup>10+</sup>

getTouchpadSwipeSwitch(): Promise\<boolean>

获取触控板多指滑动功能开启状态，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise对象。返回true表示触控板多指滑动功能开启；返回false表示触控板多指滑动功能关闭。默认开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 获取触摸板滑动开关
            pointer.getTouchpadSwipeSwitch().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad swipe switch, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 获取触摸板滑动开关
            pointer.getTouchpadSwipeSwitch().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad swipe switch, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad swipe switch, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadRightClickType<sup>10+</sup>

setTouchpadRightClickType(type: RightClickType, callback: AsyncCallback\<void>): void

设置触控板右键菜单类型，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| type| [RightClickType](js-apis-pointer.md#rightclicktype10)| 是    |type代表触控板右键菜单类型。<br>- TOUCHPAD_RIGHT_BUTTON：按压触控板右键区域。<br>- TOUCHPAD_LEFT_BUTTON：按压触控板左键区域。<br>- TOUCHPAD_TWO_FINGER_TAP：双指轻击或双指按压触控板。<br>- TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON<sup>20+</sup>：双指轻击或双指按压触控板、或按压触控板右键区域。<br>- TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON<sup>20+</sup>：双指轻击或双指按压触控板、或按压触控板左键区域。<br>默认值为TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON。|
| callback | AsyncCallback\<void> | 是    | 回调函数。当设置触控板右键菜单类型成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 设置触摸板右键点击类型
            pointer.setTouchpadRightClickType(pointer.RightClickType.TOUCHPAD_RIGHT_BUTTON , (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad right click type.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 设置触摸板右键点击类型
            pointer.setTouchpadRightClickType(pointer.RightClickType.TOUCHPAD_RIGHT_BUTTON, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad right click type.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadRightClickType<sup>10+</sup>

setTouchpadRightClickType(type: RightClickType): Promise\<void>

设置触控板右键菜单类型，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| type| [RightClickType](js-apis-pointer.md#rightclicktype10)| 是    |type代表触控板右键菜单类型。<br>- TOUCHPAD_RIGHT_BUTTON：按压触控板右键区域。<br>- TOUCHPAD_LEFT_BUTTON：按压触控板左键区域。<br>- TOUCHPAD_TWO_FINGER_TAP：双指轻击或双指按压触控板。<br>- TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON<sup>20+</sup>：双指轻击或双指按压触控板、或按压触控板右键区域。<br>- TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON<sup>20+</sup>：双指轻击或双指按压触控板、或按压触控板左键区域。<br>默认值为TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON。|

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 设置触摸板右键点击类型
            pointer.setTouchpadRightClickType(pointer.RightClickType.TOUCHPAD_RIGHT_BUTTON).then(() => {
              console.info(`Succeeded in setting touchpad right click type.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 设置触摸板右键点击类型
            pointer.setTouchpadRightClickType(pointer.RightClickType.TOUCHPAD_RIGHT_BUTTON).then(() => {
              console.info(`Succeeded in setting touchpad right click type.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadRightClickType<sup>10+</sup>

getTouchpadRightClickType(callback: AsyncCallback\<RightClickType>): void

获取触控板右键菜单类型，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<[RightClickType](js-apis-pointer.md#rightclicktype10)> | 是    | 回调函数。当获取触控板右键菜单类型成功，err为undefined，对象是触控板右键菜单类型；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            pointer.getTouchpadRightClickType((error: BusinessError, type: pointer.RightClickType) => {
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

ArkTS-Sta示例:

```ts
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
            // 获取触摸板右键点击类型
            pointer.getTouchpadRightClickType((error: BusinessError<void>|null, type: pointer.RightClickType|undefined) => {
              if (error) {
                console.error(`Failed to get touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting touchpad right click type, type: ${JSON.stringify(type)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get touchpad right click type, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadRightClickType<sup>10+</sup>

getTouchpadRightClickType(): Promise\<RightClickType>

获取触控板右键菜单类型，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<[RightClickType](js-apis-pointer.md#rightclicktype10) > | Promise对象，返回触控板右键菜单类型。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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

ArkTS-Sta示例：

```ts
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
            // 获取触摸板右键点击类型
            pointer.getTouchpadRightClickType().then((type: pointer.RightClickType) => {
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

## pointer.setPointerSize<sup>10+</sup>

ArkTS-Dyn: setPointerSize(size: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: setPointerSize(size: int, callback: AsyncCallback&lt;void&gt;): void

设置鼠标光标大小，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| size     | ArkTS-Dyn: number<br/>ArkTS-Sta: int                    | 是    | 鼠标光标大小，范围为[1-7]，默认为1。   |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数，当设置成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 设置鼠标指针大小
            pointer.setPointerSize(1, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting pointer size.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 设置鼠标指针大小
            pointer.setPointerSize(1, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Failed to set pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting pointer size.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerSize<sup>10+</sup>

ArkTS-Dyn: setPointerSize(size: number): Promise&lt;void&gt;

ArkTS-Sta: setPointerSize(size: int): Promise&lt;void&gt;

设置鼠标光标大小，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| size  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标光标大小，范围为[1-7]，默认为1。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 设置鼠标指针大小
            pointer.setPointerSize(3).then(() => {
              console.info(`Succeeded in setting pointer size.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 设置鼠标指针大小
            pointer.setPointerSize(3).then(() => {
              console.info(`Succeeded in setting pointer size.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerSizeSync<sup>10+</sup>

ArkTS-Dyn: setPointerSizeSync(size: number): void

ArkTS-Sta: setPointerSizeSync(size: int): void

设置鼠标光标大小，使用同步方式进行设置。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| size  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标光标大小，范围为[1-7]，默认为1。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 同步设置鼠标指针大小
            pointer.setPointerSizeSync(5);
            console.info(`Succeeded in setting pointer size sync.`);
          } catch (error) {
            console.error(`Failed to set pointer size sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 同步设置鼠标指针大小
            pointer.setPointerSizeSync(5);
            console.info(`Succeeded in setting pointer size sync.`);
          } catch (error) {
            console.error(`Failed to set pointer size sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerSize<sup>10+</sup>

ArkTS-Dyn: getPointerSize(callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getPointerSize(callback: AsyncCallback&lt;int&gt;): void

获取鼠标光标大小，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;number&gt; | 是    | 回调函数。当获取鼠标光标大小成功，err为undefined，number是获取的鼠标光标大小；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 获取鼠标指针大小
            pointer.getPointerSize((error: BusinessError, size: number) => {
              if (error) {
                console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting pointer size, size: ${JSON.stringify(size)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 获取鼠标指针大小
            pointer.getPointerSize((error: BusinessError<void>|null, size: int|undefined) => {
              if (error) {
                console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting pointer size, size: ${JSON.stringify(size)}.`);
            });
          } catch (error) {
            console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerSize<sup>10+</sup>

ArkTS-Dyn: getPointerSize(): Promise&lt;number&gt;

ArkTS-Sta: getPointerSize(): Promise&lt;int&gt;

获取当前鼠标光标大小，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;int&gt; | Promise对象，返回鼠标光标大小。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |


**示例**：

ArkTS-Dyn示例：

```js
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
            // 获取鼠标指针大小
            pointer.getPointerSize().then((size: number) => {
              console.info(`Succeeded in getting pointer size, size: ${JSON.stringify(size)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 获取鼠标指针大小
            pointer.getPointerSize().then((size: int) => {
              console.info(`Succeeded in getting pointer size, size: ${JSON.stringify(size)}.`);
            });
          } catch (error) {
            console.error(`Failed to get pointer size, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerSizeSync<sup>10+</sup>

ArkTS-Dyn: getPointerSizeSync(): number

ArkTS-Sta: getPointerSizeSync(): int

获取鼠标光标大小，使用同步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: number<br/>ArkTS-Sta: int | 鼠标光标大小。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |


**示例**：

ArkTS-Dyn示例:

```js
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let pointerSize = pointer.getPointerSizeSync();
            console.info(`Succeeded in getting pointer size sync, pointerSize: ${JSON.stringify(pointerSize)}.`);
          } catch (error) {
            console.error(`Failed to get pointer size sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            let pointerSize = pointer.getPointerSizeSync();
            console.info(`Succeeded in getting pointer size sync, pointerSize: ${JSON.stringify(pointerSize)}.`);
          } catch (error) {
            console.error(`Failed to get pointer size sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerColor<sup>10+</sup>

ArkTS-Dyn: setPointerColor(color: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: setPointerColor(color: int, callback: AsyncCallback&lt;void&gt;): void

设置鼠标光标颜色，使用callback异步回调。

> **说明**：
>
> 设置和调试时，需连接外部设备，如鼠标、蓝牙等。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| color     | ArkTS-Dyn: number<br/>ArkTS-Sta: int                    | 是    | 鼠标光标颜色，默认为黑色：0x000000。   |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数，当设置成功，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 设置鼠标指针颜色
            pointer.setPointerColor(0xF6C800, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting pointer color.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 设置鼠标指针颜色
            pointer.setPointerColor(0xF6C800, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting pointer color.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerColor<sup>10+</sup>

ArkTS-Dyn: setPointerColor(color: number): Promise&lt;void&gt;

ArkTS-Sta: setPointerColor(color: int): Promise&lt;void&gt;

设置鼠标光标颜色，使用Promise异步回调。

> **说明**：
>
> 设置和调试时，需连接外部设备，如鼠标、蓝牙等。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| color  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标光标颜色，默认为黑色：0x000000。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例：

```js
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
            // 设置鼠标指针颜色
            pointer.setPointerColor(0xF6C800).then(() => {
              console.info(`Succeeded in setting pointer color.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
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
            // 设置鼠标指针颜色
            pointer.setPointerColor(0xF6C800).then(() => {
              console.info(`Succeeded in setting pointer color.`);
            });
          } catch (error) {
            console.error(`Failed to set pointer color, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setPointerColorSync<sup>10+</sup>

ArkTS-Dyn: setPointerColorSync(color: number): void

ArkTS-Sta: setPointerColorSync(color: int): void

设置鼠标光标颜色，使用同步方式进行设置。

> **说明**：
>
> 设置和调试时，需连接外部设备，如鼠标、蓝牙等。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| color  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标光标颜色，默认为黑色：0x000000。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 同步设置鼠标指针颜色
            pointer.setPointerColorSync(0xF6C800);
            console.info(`Succeeded in setting pointer color sync.`);
          } catch (error) {
            console.error(`Failed to set pointer color sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 同步设置鼠标指针颜色
            pointer.setPointerColorSync(0xF6C800);
            console.info(`Succeeded in setting pointer color sync.`);
          } catch (error) {
            console.error(`Failed to set pointer color sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getPointerColor<sup>10+</sup>

ArkTS-Dyn: getPointerColor(callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getPointerColor(callback: AsyncCallback&lt;int&gt;): void

获取鼠标光标颜色，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br>ArkTS-Sta: AsyncCallback&lt;int&gt; | 是    | 回调函数。当获取鼠标光标颜色成功，err为undefined，number是获取的鼠标光标颜色；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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

```ts
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

## pointer.getPointerColor<sup>10+</sup>

ArkTS-Dyn: getPointerColor(): Promise&lt;number&gt;

ArkTS-Sta: getPointerColor(): Promise&lt;int&gt;

获取当前鼠标光标颜色，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;int&gt; | Promise对象，返回鼠标光标颜色。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |


**示例**：

ArkTS-Dyn示例：

```js
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

```ts
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

## pointer.getPointerColorSync<sup>10+</sup>

ArkTS-Dyn: getPointerColorSync(): number

ArkTS-Sta: getPointerColorSync(): int

获取鼠标光标颜色，使用同步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: number<br/>ArkTS-Sta: int | 鼠标光标颜色。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |


**示例**：

ArkTS-Dyn示例:

```js
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let pointerColor = pointer.getPointerColorSync();
            console.info(`Succeeded in getting pointer color sync, pointerColor: ${JSON.stringify(pointerColor)}.`);
          } catch (error) {
            console.error(`Failed to get pointer color sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            let pointerColor = pointer.getPointerColorSync();
            console.info(`Succeeded in getting pointer color sync, pointerColor: ${JSON.stringify(pointerColor)}.`);
          } catch (error) {
            console.error(`Failed to get pointer color sync, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadDoubleTapAndDragState<sup>14+</sup>

setTouchpadDoubleTapAndDragState(isOpen: boolean, callback: AsyncCallback\<void>): void

设置触控板双击拖拽开关状态，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| isOpen | boolean | 是    | 双击拖拽开关的状态，true代表开启，false代表关闭。 |
| callback | AsyncCallback\<void> | 是    | 回调函数。当设置触控板双击拖拽开关状态成功，err为undefined，否则为错误对象。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 设置触摸板双击拖拽状态
            pointer.setTouchpadDoubleTapAndDragState(true, (error: BusinessError) => {
              if (error) {
                console.error(`Failed to set touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad double tap and drag state.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 设置触摸板双击拖拽状态
            pointer.setTouchpadDoubleTapAndDragState(true, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Failed to set touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in setting touchpad double tap and drag state.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadDoubleTapAndDragState<sup>14+</sup>

setTouchpadDoubleTapAndDragState(isOpen: boolean): Promise\<void>

设置触控板双击拖拽开关状态，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| isOpen | boolean | 是    | 双击拖拽开关的状态，true代表开启，false代表关闭。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 设置触摸板双击拖拽状态
            pointer.setTouchpadDoubleTapAndDragState(false).then(() => {
              console.info(`Succeeded in setting touchpad double tap and drag state.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 设置触摸板双击拖拽状态
            pointer.setTouchpadDoubleTapAndDragState(false).then(() => {
              console.info(`Succeeded in setting touchpad double tap and drag state.`);
            });
          } catch (error) {
            console.error(`Failed to set touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadDoubleTapAndDragState<sup>14+</sup>

getTouchpadDoubleTapAndDragState(callback: AsyncCallback\<boolean>): void

获取触控板双击拖拽开关的开启状态，使用callback异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | 是    | 回调函数。当获取触控板双击拖拽开关的开启状态成功，err为undefined，返回true代表开启，返回false代表关闭；否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 获取触摸板双击拖拽状态
            pointer.getTouchpadDoubleTapAndDragState((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Failed to get touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting touchpad double tap and drag state, state: ${JSON.stringify(state)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 获取触摸板双击拖拽状态
            pointer.getTouchpadDoubleTapAndDragState((error: BusinessError<void>|null, state: boolean|undefined) => {
              if (error) {
                console.error(`Failed to get touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
              } else {
                console.info(`Succeeded in getting touchpad double tap and drag state, state: ${JSON.stringify(state)}.`);
              }
            });
          } catch (error) {
            console.error(`Failed to get touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadDoubleTapAndDragState<sup>14+</sup>

getTouchpadDoubleTapAndDragState(): Promise\<boolean>

获取触控板双击拖拽开关的开启状态，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统接口**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise对象。返回true表示触控板双击拖拽功能开启；返回false表示触控板双击拖拽功能关闭。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |

**示例**：

ArkTS-Dyn示例:

```js
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
            // 获取触摸板双击拖拽状态
            pointer.getTouchpadDoubleTapAndDragState().then((state) => {
              console.info(`Succeeded in getting touchpad double tap and drag state, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
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
            // 获取触摸板双击拖拽状态
            pointer.getTouchpadDoubleTapAndDragState().then((state: boolean) => {
              console.info(`Succeeded in getting touchpad double tap and drag state, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get touchpad double tap and drag state, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.setMouseScrollDirection<sup>24+</sup>

setMouseScrollDirection(inverted: boolean): Promise\<void>

设置鼠标滚轮滚动的方向，使用Promise异步回调。

**需要权限**: ohos.permission.INPUT_DEVICE_CONTROLLER

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：24

**ArkTS-Sta起始版本**：24

**参数**：

| 参数名 | 类型    | 必填 | 说明                                                                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------------------------------------------------------ |
| inverted  | boolean | 是   | inverted为鼠标滚轮滚动的方向。<br>true与鼠标滚轮滚动的手指方向一致，false与鼠标滚轮滚动的手指方向相反。<br>默认为true。 |

**返回值**：

| 类型           | 说明                                   |
| -------------- | -------------------------------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[鼠标光标错误码](./errorcode-pointer.md)

| 错误码ID   | 错误信息                        |
|---------|-----------------------------|
| 201     | Permission denied.          |
| 202     | SystemAPI permission error. |
| 3800001 | Input service exception.    |

**示例**：

ArkTS-Dyn示例:

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button("setMouseScrollDirection")
        .onClick(() => {
          try {
            // 设置鼠标滚动方向
            pointer.setMouseScrollDirection(false).then(() => {
              console.info(`Succeeded in setting mouse scroll direction.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to set mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to set mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { pointer } from '@kit.InputKit';
import { BusinessError, AsyncCallback } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text("setMouseScrollDirection")
        .onClick(() => {
          try {
            // 设置鼠标滚动方向
            pointer.setMouseScrollDirection(false).then(() => {
              console.info(`Succeeded in setting mouse scroll direction.`);
            });
          } catch (error) {
            console.error(`Failed to set mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

## pointer.getMouseScrollDirection<sup>24+</sup>

getMouseScrollDirection(): Promise\<boolean>

获取鼠标滚轮滚动方向，使用Promise异步回调。

**需要权限**: ohos.permission.INPUT_DEVICE_CONTROLLER

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：24

**ArkTS-Sta起始版本**：24

**返回值**：

| 类型              | 说明                                                                                                                         |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Promise\<boolean> | Promise对象。返回true表示鼠标滚轮滚动方向与手指方向一致；返回false表示鼠标滚轮滚动方向与手指方向相反。默认为true。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[鼠标光标错误码](./errorcode-pointer.md)

| 错误码ID   | 错误信息                                                                                                                                       |
|---------| ---------------------------------------------------------------------------------------------------------------------------------------------- |
| 201     | Permission denied.          |
| 202     | SystemAPI permission error. |
| 3800001 | Input service exception.    |

**示例**：

ArkTS-Dyn示例:

```js
import { pointer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button("getMouseScrollDirection")
        .onClick(() => {
          try {
            // 获取鼠标滚动方向
            pointer.getMouseScrollDirection().then((state: boolean) => {
              console.info(`Succeeded in getting mouse scroll direction, state: ${JSON.stringify(state)}.`);
            }).catch((error: BusinessError) => {
              console.error(`Failed to get mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
            })
          } catch (error) {
            console.error(`Failed to get mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { pointer } from '@kit.InputKit';
import { BusinessError, AsyncCallback } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text("getMouseScrollDirection")
        .onClick(() => {
          try {
            // 获取鼠标滚动方向
            pointer.getMouseScrollDirection().then((state: boolean) => {
              console.info(`Succeeded in getting mouse scroll direction, state: ${JSON.stringify(state)}.`);
            });
          } catch (error) {
            console.error(`Failed to get mouse scroll direction, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```