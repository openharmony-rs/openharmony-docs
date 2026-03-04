# @ohos.multimodalInput.pointer (鼠标光标)(系统接口)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

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

设置鼠标移动速度，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| speed    | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标移动速度，范围[1, 20]，默认为10，传参大于最大值就会被自动设置为最大值，传参小于最小值就会被设置为最小值。   |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息          |
| -------- | ----------------- |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2.Incorrect parameter types.3.Parameter verification failed. |


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
            pointer.setPointerSpeed(5, (error: BusinessError) => {
              if (error) {
                console.error(`Set pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`Set pointer speed success`);
            });
          } catch (error) {
            console.error(`Set pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setPointerSpeed(5, (error:  BusinessError<void>|null, info: undefined) => {
              if (error) {
                console.error(`Set pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`Set pointer speed success`);
            });
          } catch (error) {
            console.error(`Set pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| speed |  ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标移动速度，范围[1, 20]，默认为10，传参大于最大值就会被自动设置为最大值，传参小于最小值就会被设置为最小值。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息          |
| -------- | ----------------- |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2.Incorrect parameter types.3.Parameter verification failed. |


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
            pointer.setPointerSpeed(5).then(() => {
              console.info(`Set pointer speed success`);
            }).catch((error: BusinessError) => {
              console.error(`Set pointer failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`Set pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setPointerSpeed(5).then(() => {
              console.info(`Set pointer speed success`);
            });
          } catch (error) {
            console.error(`Set pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| speed |  ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标移动速度，范围[1, 20]，默认为10，传参大于最大值就会被自动设置为最大值，传参小于最小值就会被设置为最小值。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            console.info(`Set pointer speed success`);
          } catch (error) {
            console.error(`Set pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            console.info(`Set pointer speed success`);
          } catch (error) {
            console.error(`Set pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getPointerSpeed

ArkTS-Dyn: getPointerSpeed(callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getPointerSpeed(callback: AsyncCallback&lt;int&gt;): void

获取鼠标移动速度，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br> ArkTS-Sta: AsyncCallback&lt;int&gt;| 是    | 回调函数，异步返回鼠标移动速度。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | Permission denied, non-system app called system api. |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |


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
            pointer.getPointerSpeed((error: BusinessError, speed: number) => {
              if (error) {
                console.error(`Get pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`Get pointer speed success, speed: ${JSON.stringify(speed)}`);
            });
          } catch (error) {
            console.error(`Get pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.getPointerSpeed((error: BusinessError<void>|null, speed: int|undefined) => {
              if (error) {
                console.error(`Get pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`Get pointer speed success, speed: ${JSON.stringify(speed)}`);
            });
          } catch (error) {
            console.error(`Get pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getPointerSpeed

getPointerSpeed(): Promise&lt;number&gt;

获取当前鼠标移动速度，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：9

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;int| Promise对象，异步返回鼠标移动速度。 |

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
            pointer.getPointerSpeed().then(speed => {
              console.info(`Get pointer speed success, speed: ${JSON.stringify(speed)}`);
            }).catch((error: BusinessError) => {
              console.error(`Get pointer failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`Get pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.getPointerSpeed().then((speed: int) => {
              console.info(`Get pointer speed success, speed: ${JSON.stringify(speed)}`);
            });
          } catch (error) {
            console.error(`Get pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

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
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            console.info(`Get pointer speed success, speed: ${JSON.stringify(speed)}`);
          } catch (error) {
            console.error(`Get pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            console.info(`Get pointer speed success, speed: ${JSON.stringify(speed)}`);
          } catch (error) {
            console.error(`Get pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setHoverScrollState<sup>10+</sup>

setHoverScrollState(state: boolean, callback: AsyncCallback&lt;void&gt;): void

设置鼠标悬停滚动开关状态，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state    | boolean                    | 是    | 鼠标悬停滚动开关状态。true代表开关开启，false代表开关关闭，默认开启。   |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setHoverScrollState(true, (error: BusinessError) => {
              if (error) {
                console.error(`Set the mouse hover scroll failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`Set the mouse hover scroll success`);
            });
          } catch (error) {
            console.error(`Set the mouse hover scroll failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setHoverScrollState(true, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Set the mouse hover scroll failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`Set the mouse hover scroll success`);
            });
          } catch (error) {
            console.error(`Set the mouse hover scroll failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean | 是    | 鼠标悬停滚动开关状态。true代表开关开启，false代表开关关闭，默认开启。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setHoverScrollState(true).then(() => {
              console.info(`Set the mouse hover scroll success`);
            }).catch((error: BusinessError) => {
              console.error(`Set hover scroll failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`Set the mouse hover scroll failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setHoverScrollState(true).then(() => {
              console.info(`Set the mouse hover scroll success`);
            });
          } catch (error) {
            console.error(`Set the mouse hover scroll failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```
## pointer.getHoverScrollState<sup>10+</sup>

getHoverScrollState(callback: AsyncCallback&lt;boolean&gt;): void

获取鼠标悬停滚动开关状态，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;boolean&gt; | 是    | 回调函数，异步返回鼠标悬停滚动开关状态。true代表开关开启，false代表开关关闭，默认开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getHoverScrollState((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`Get the mouse hover scroll failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
              } else {
                console.info(`Get the mouse hover scroll success, state: ${JSON.stringify(state)}`);
              }
            });
          } catch (error) {
            console.error(`Get the mouse hover scroll failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.getHoverScrollState((error: BusinessError | null, state: boolean | undefined) => {
              console.info(`Get the mouse hover scroll success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`Get the mouse hover scroll failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise&lt;boolean&gt; | Promise对象，异步返回鼠标悬停滚动开关状态。true代表开关开启，false代表开关关闭，默认开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getHoverScrollState().then((state: boolean) => {
              console.info(`Get the mouse hover scroll success, state: ${JSON.stringify(state)}`);
            }).catch((error: BusinessError) => {
              console.error(`Get hover scroll failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`Get the mouse hover scroll failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.getHoverScrollState().then((state: boolean) => {
              console.info(`Get the mouse hover scroll success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`Get the mouse hover scroll failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setMousePrimaryButton<sup>10+</sup>

setMousePrimaryButton(primary: PrimaryButton, callback: AsyncCallback&lt;void&gt;): void

设置鼠标主键，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型                      | 必填  | 说明                                    |
| -------- | ------------------------- | ----  | ------------------------------------- |
| primary  | [PrimaryButton](js-apis-pointer.md#primarybutton10)   | 是    | 鼠标主键类型。   |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setMousePrimaryButton(pointer.PrimaryButton.RIGHT, (error: BusinessError) => {
              if (error) {
                console.error(`Set mouse primary button failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`Set mouse primary button success`);
            });
          } catch (error) {
            console.error(`Set mouse primary button failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setMousePrimaryButton(pointer.PrimaryButton.RIGHT, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`Set mouse primary button failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`Set mouse primary button success`);
            });
          } catch (error) {
            console.error(`Set mouse primary button failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| primary | [PrimaryButton](js-apis-pointer.md#primarybutton10) | 是    | 鼠标主键类型。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setMousePrimaryButton(pointer.PrimaryButton.RIGHT).then(() => {
              console.info(`Set mouse primary button success`);
            }).catch((error: BusinessError) => {
              console.error(`Set mouse failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`Set mouse primary button failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setMousePrimaryButton(pointer.PrimaryButton.RIGHT).then(() => {
              console.info(`Set mouse primary button success`);
            });
          } catch (error) {
            console.error(`Set mouse primary button failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}

```

## pointer.getMousePrimaryButton<sup>10+</sup>

getMousePrimaryButton(callback: AsyncCallback&lt;PrimaryButton&gt;): void

获取当前鼠标主键，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback&lt;[PrimaryButton](js-apis-pointer.md#primarybutton10)&gt; | 是    | 回调函数，异步返回鼠标主键。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getMousePrimaryButton((error: BusinessError, primary: pointer.PrimaryButton) => {
              if (error) {
                console.error(`Get mouse primary button failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
              } else {
                console.info(`Get mouse primary button success, primary: ${JSON.stringify(primary)}`);
              }
            });
          } catch (error) {
            console.error(`Get mouse primary button failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.getMousePrimaryButton((error: BusinessError<void>|null, primary: pointer.PrimaryButton | undefined) => {
              console.info(`Get mouse primary button success, primary: ${JSON.stringify(primary)}`);
            });
          } catch (error) {
            console.error(`Get mouse primary button failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise&lt;[PrimaryButton](js-apis-pointer.md#primarybutton10)&gt; | Promise对象，异步返回鼠标主键。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getMousePrimaryButton().then((primary: pointer.PrimaryButton) => {
              console.info(`Get mouse primary button success, primary: ${JSON.stringify(primary)}`);
            }).catch((error: BusinessError) => {
              console.error(`Get mouse failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`Get mouse primary button failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.getMousePrimaryButton().then((primary: pointer.PrimaryButton) => {
              console.info(`Get mouse primary button success, primary: ${JSON.stringify(primary)}`);
            });
          } catch (error) {
            console.error(`Get mouse primary button failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setMouseScrollRows<sup>10+</sup>

ArkTS-Dyn: setMouseScrollRows(rows: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: setMouseScrollRows(rows: int, callback: AsyncCallback&lt;void&gt;): void

设置鼠标滚动行数，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| rows     |  ArkTS-Dyn: number<br/>ArkTS-Sta: int    | 是    | 鼠标滚动行数，范围[1, 100]，默认为3，传参大于最大值就会被自动设置为最大值，传参小于最小值就会被设置为最小值。   |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setMouseScrollRows(1, (error: BusinessError) => {
              if (error) {
                console.error(`setMouseScrollRows failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setMouseScrollRows success`);
            });
          } catch (error) {
            console.error(`setMouseScrollRows failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setMouseScrollRows(1, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`setMouseScrollRows failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setMouseScrollRows success`);
            });
          } catch (error) {
            console.error(`setMouseScrollRows failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| rows  |  ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标滚动行数，范围[1, 100]，默认为3，传参大于最大值就会被自动设置为最大值，传参小于最小值就会被设置为最小值。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setMouseScrollRows(20).then(() => {
              console.info(`setMouseScrollRows success`);
            }).catch((error: BusinessError) => {
              console.error(`Set mouse scroll rows failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`setMouseScrollRows failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setMouseScrollRows(20).then(() => {
              console.info(`setMouseScrollRows success`);
            });
          } catch (error) {
            console.error(`setMouseScrollRows failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getMouseScrollRows<sup>10+</sup>

ArkTS-Dyn: getMouseScrollRows(callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getMouseScrollRows(callback: AsyncCallback&lt;int&gt;): void

获取鼠标滚动行数，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br>ArkTS-Sta: AsyncCallback&lt;int&gt; | 是    | 回调函数，异步返回鼠标滚动行数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getMouseScrollRows((error: BusinessError, rows: number) => {
              if (error) {
                console.error(`getMouseScrollRows error: ${JSON.stringify(error, [`code`, `message`])}`);
              } else {
                console.info(`getMouseScrollRows success, rows: ${JSON.stringify(rows)}`);
              }
            });
          } catch (error) {
            console.error(`getMouseScrollRows failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getMouseScrollRows((error: BusinessError<void> | null, rows: int | undefined) => {
              console.info(`getMouseScrollRows success, rows: ${JSON.stringify(rows)}`);
            });
          } catch (error) {
            console.error(`getMouseScrollRows failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br> ArkTS-Sta: Promise&lt;int&gt; | Promise对象，异步返回鼠标滚动行数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getMouseScrollRows().then((rows: number) => {
              console.info(`getMouseScrollRows success, rows: ${JSON.stringify(rows)}`);
            }).catch((error: BusinessError) => {
              console.error(`Get mouse scroll rows failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`getMouseScrollRows failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.getMouseScrollRows().then((rows: int) => {
              console.info(`getMouseScrollRows success, rows: ${JSON.stringify(rows)}`);
            });
          } catch (error) {
            console.error(`getMouseScrollRows failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadScrollSwitch<sup>10+</sup>

setTouchpadScrollSwitch(state: boolean, callback: AsyncCallback\<void>): void

设置触控板滚轴开关，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | 是    | 滚轴开关开启的状态，true代表开启，false代表关闭，默认为开启。   |
| callback | AsyncCallback\<void> | 是    | 回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadScrollSwitch(true, (error: BusinessError) => {
              if (error) {
                console.error(`setTouchpadScrollSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadScrollSwitch success`);
            });
          } catch (error) {
            console.error(`setTouchpadScrollSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setTouchpadScrollSwitch(true, (error: BusinessError<void>|null, data: undefined) => {
              if (error) {
                console.error(`setTouchpadScrollSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadScrollSwitch success`);
            });
          } catch (error) {
            console.error(`setTouchpadScrollSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| 是    |  滚轴开关开启的状态，true代表开启，false代表关闭，默认为开启。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadScrollSwitch(false).then(() => {
              console.info(`setTouchpadScrollSwitch success`);
            }).catch((error: BusinessError) => {
              console.error(`Set touchpad scroll switch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`setTouchpadScrollSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setTouchpadScrollSwitch(false).then(() => {
              console.info(`setTouchpadScrollSwitch success`);
            });
          } catch (error) {
            console.error(`setTouchpadScrollSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadScrollSwitch<sup>10+</sup>

getTouchpadScrollSwitch(callback:  AsyncCallback\<boolean>): void

获取触控板滚轴能力开启状态，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | 是    | 回调函数，异步返回触控板滚轴能力开启状态。true代表开启，false代表关闭，默认为开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadScrollSwitch((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`getTouchpadScrollSwitch error: ${JSON.stringify(error, [`code`, `message`])}`);
              } else {
                console.info(`getTouchpadScrollSwitch success, state: ${JSON.stringify(state)}`);
              }
            });
          } catch (error) {
            console.error(`getTouchpadScrollSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.getTouchpadScrollSwitch((error: BusinessError<void> | null, state: boolean  | undefined) => {
              console.info(`getTouchpadScrollSwitch success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadScrollSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise对象，异步返回触控板滚轴能力开启状态。true代表开启，false代表关闭，默认为开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadScrollSwitch().then((state) => {
              console.info(`getTouchpadScrollSwitch success, state: ${JSON.stringify(state)}`);
            }).catch((error: BusinessError) => {
              console.error(`Get touchpad scroll switch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`getTouchpadScrollSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.getTouchpadScrollSwitch().then((state: boolean) => {
              console.info(`getTouchpadScrollSwitch success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadScrollSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadScrollDirection<sup>10+</sup>

setTouchpadScrollDirection(state: boolean, callback: AsyncCallback\<void>): void

设置触控板滚轴的方向，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | 是    | state为触控板滚轴的方向。<br>true与手指滑动的方向一致，false与手指滑动的方向相反。<br>默认为true。   |
| callback | AsyncCallback\<void> | 是    | 回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadScrollDirection(true, (error: BusinessError) => {
              if (error) {
                console.error(`setTouchpadScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadScrollDirection success`);
            });
          } catch (error) {
            console.error(`setTouchpadScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setTouchpadScrollDirection(true, (error: BusinessError<void> | null, data: undefined) => {
              if (error) {
                console.error(`setTouchpadScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadScrollDirection success`);
            });
          } catch (error) {
            console.error(`setTouchpadScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| 是    |  state为触控板滚轴的方向。<br>true与手指滑动的方向一致，false与手指滑动的方向相反。<br>默认为true。|

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadScrollDirection (false).then(() => {
              console.info(`setTouchpadScrollDirection success`);
            }).catch((error: BusinessError) => {
              console.error(`Set touchpad scroll direction failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`setTouchpadScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setTouchpadScrollDirection (false).then(() => {
              console.info(`setTouchpadScrollDirection success`);
            });
          } catch (error) {
            console.error(`setTouchpadScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadScrollDirection<sup>10+</sup>

getTouchpadScrollDirection(callback:  AsyncCallback\<boolean>): void

获取触控板滚轴方向，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | 是    | 回调函数，异步返回触控板滚轴方向。<br>true与手指滑动的方向一致，false与手指滑动的方向相反。<br>默认为true。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadScrollDirection ((error: BusinessError, state: boolean) => {
              console.info(`getTouchpadScrollDirection success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadScrollDirection ((error: BusinessError<void> | null, state: boolean | undefined) => {
              console.info(`getTouchpadScrollDirection success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise对象，异步返回触控板滚轴方向。<br>true与手指滑动的方向一致，false与手指滑动的方向相反。<br>默认为true。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadScrollDirection().then((state: boolean) => {
              console.info(`getTouchpadScrollDirection success, state: ${JSON.stringify(state)}`);
            }).catch((error: BusinessError) => {
              console.error(`Get touchpad scroll direction failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`getTouchpadScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadScrollDirection().then((state: boolean) => {
              console.info(`getTouchpadScrollDirection success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadTapSwitch<sup>10+</sup>

setTouchpadTapSwitch(state: boolean, callback: AsyncCallback\<void>): void

设置触控板轻触功能开关，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | 是    |触控板轻触功能开关开启状态。 true代表轻触开启，false代表轻触关闭，默认开启。   |
| callback | AsyncCallback\<void> | 是    | 回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadTapSwitch(true, (error: BusinessError) => {
              if (error) {
                console.error(`setTouchpadTapSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadTapSwitch success`);
            });
          } catch (error) {
            console.error(`setTouchpadTapSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`); 
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.setTouchpadTapSwitch(true, (error: BusinessError<void> | null, data: undefined) => {
              if (error) {
                console.error(`setTouchpadTapSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadTapSwitch success`);
            });
          } catch (error) {
            console.error(`setTouchpadTapSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| 是    |  触控板轻触功能开关开启状态， true代表轻触开启，false代表轻触关闭，默认开启。  |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadTapSwitch(false).then(() => {
              console.info(`setTouchpadTapSwitch success`);
            }).catch((error: BusinessError) => {
              console.error(`Set touchpad tap switch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`setTouchpadTapSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.setTouchpadTapSwitch(false).then(() => {
              console.info(`setTouchpadTapSwitch success`);
            });
          } catch (error) {
            console.error(`setTouchpadTapSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadTapSwitch<sup>10+</sup>

getTouchpadTapSwitch(callback:  AsyncCallback\<boolean>): void

获取触控板轻触能力开启状态，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | 是    | 回调函数，异步返回触控板轻触功能开启状态， true代表开启，false代表关闭，默认开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadTapSwitch((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`getTouchpadTapSwitch error: ${JSON.stringify(error, [`code`, `message`])}`);
              } else {
                console.info(`getTouchpadTapSwitch success, state: ${JSON.stringify(state)}`);
              }
            });
          } catch (error) {
            console.error(`getTouchpadTapSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadTapSwitch((error: BusinessError<void> | null, state: boolean | undefined) => {
              console.info(`getTouchpadTapSwitch success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadTapSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise对象，异步返回触控板轻触功能开启状态，true代表开启，false代表关闭，默认开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadTapSwitch().then((state: boolean) => {
              console.info(`getTouchpadTapSwitch success, state: ${JSON.stringify(state)}`);
            }).catch((error: BusinessError) => {
              console.error(`Get touchpad tap switch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`getTouchpadTapSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadTapSwitch().then((state: boolean) => {
              console.info(`getTouchpadTapSwitch success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadTapSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadPointerSpeed<sup>10+</sup>

ArkTS-Dyn: setTouchpadPointerSpeed(speed: number, callback: AsyncCallback\<void>): void

ArkTS-Sta: setTouchpadPointerSpeed(speed: int, callback: AsyncCallback\<void>): void

设置触控板光标移动速度，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| speed | ArkTS-Dyn: number<br>ArkTS-Sta: int   | 是    |speed代表光标移动速度。speed取值范围[1, 11]，默认6，传参大于最大值就会被自动设置为最大值，传参小于最小值就会被设置为最小值。  |
| callback | AsyncCallback\<void> | 是    | 回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadPointerSpeed(1, (error: BusinessError) => {
              if (error) {
                console.error(`setTouchpadPointerSpeedfailed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadPointerSpeed success`);
            });
          } catch (error) {
            console.error(`setTouchpadPointerSpeed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Dyn示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.setTouchpadPointerSpeed(1, (error: BusinessError<void> | null, data: undefined) => {
              if (error) {
                console.error(`setTouchpadPointerSpeedfailed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadPointerSpeed success`);
            });
          } catch (error) {
            console.error(`setTouchpadPointerSpeed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| speed| ArkTS-Dyn: number<br>ArkTS-Sta: int | 是    | speed代表光标移动速度。ArkTS-Dyn API version 10到API version 19，参数范围为[1, 11]，默认为6; API version 20开始，参数范围改为[1, 20]，默认为10。传参大于最大值就会被自动设置为最大值，传参小于最小值就会被设置为最小值。    |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadPointerSpeed(10).then(() => {
              console.info(`setTouchpadPointerSpeed success`);
            }).catch((error: BusinessError) => {
              console.error(`Set touchpad pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`setTouchpadPointerSpeed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.setTouchpadPointerSpeed(10).then(() => {
              console.info(`setTouchpadPointerSpeed success`);
            });
          } catch (error) {
            console.error(`setTouchpadPointerSpeed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadPointerSpeed<sup>10+</sup>

ArkTS-Dyn: getTouchpadPointerSpeed(callback: AsyncCallback\<number>): void

ArkTS-Sta: getTouchpadPointerSpeed(callback: AsyncCallback\<int>): void

获取触控板光标移动速度，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | ArkTS-Dyn: AsyncCallback\<number><br>ArkTS-Sta: AsyncCallback\<int> | 是    | 回调函数，异步返回触控板光标移动速度。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadPointerSpeed((error: BusinessError, speed: number) => {
              if (error) {
                console.error(`getTouchpadPointerSpeed error: ${JSON.stringify(error, [`code`, `message`])}`);
              } else {
                console.info(`getTouchpadPointerSpeed success, speed: ${JSON.stringify(speed)}`);
              }
            });
          } catch (error) {
            console.error(`getTouchpadPointerSpeed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadPointerSpeed((error: BusinessError<void> | null, speed: int | undefined) => {
              console.info(`getTouchpadPointerSpeed success, speed: ${JSON.stringify(speed)}`);
            });
          } catch (error) {
            console.error(`getTouchpadPointerSpeed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadPointerSpeed<sup>10+</sup>

ArkTS-Dyn: getTouchpadPointerSpeed(): Promise\<number>

ArkTS-Sta: getTouchpadPointerSpeed(): int\<number>

获取触控板光标移动速度，使用Promise异步回调。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: Promise\<number><br>ArkTS-Sta: Promise\<int> | Promise对象，异步返回触控板光标移动速度。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadPointerSpeed().then((speed: number) => {
              console.info(`getTouchpadPointerSpeed success, speed: ${JSON.stringify(speed)}`);
            }).catch((error: BusinessError) => {
              console.error(`Get touchpad pointer speed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`getTouchpadPointerSpeed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadPointerSpeed().then((speed: int) => {
              console.info(`getTouchpadPointerSpeed success, speed: ${JSON.stringify(speed)}`);
            });
          } catch (error) {
            console.error(`getTouchpadPointerSpeed failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadPinchSwitch<sup>10+</sup>

setTouchpadPinchSwitch(state: boolean, callback: AsyncCallback\<void>): void

设置触控板双指捏合功能开关，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | 是    |触控板双指捏合功能开关开启状态。 true代表开启，false代表关闭，默认开启。   |
| callback | AsyncCallback\<void> | 是    | 回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadPinchSwitch(true, (error: BusinessError) => {
              if (error) {
                console.error(`setTouchpadPinchSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadPinchSwitch success`);
            });
          } catch (error) {
            console.error(`setTouchpadPinchSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.setTouchpadPinchSwitch(true, (error: BusinessError<void> | null, data: undefined) => {
              if (error) {
                console.error(`setTouchpadPinchSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadPinchSwitch success`);
            });
          } catch (error) {
            console.error(`setTouchpadPinchSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| 是    |  触控板双指捏合功能开关开启状态。 true代表开启，false代表关闭，默认开启。  |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadPinchSwitch(false).then(() => {
              console.info(`setTouchpadPinchSwitch success`);
            }).catch((error: BusinessError) => {
              console.error(`Set touchpad pinch switch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`setTouchpadPinchSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.setTouchpadPinchSwitch(false).then(() => {
              console.info(`setTouchpadPinchSwitch success`);
            });
          } catch (error) {
            console.error(`setTouchpadPinchSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadPinchSwitch<sup>10+</sup>

getTouchpadPinchSwitch(callback:  AsyncCallback\<boolean>): void

获取触控板双指捏合功能开启状态，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | 是    | 回调函数，异步返回触控板双指捏合功能开启状态。true代表功能开启，false代表功能关闭，默认开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadPinchSwitch((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`getTouchpadPinchSwitch error: ${JSON.stringify(error, [`code`, `message`])}`);
              } else {
                console.info(`getTouchpadPinchSwitch success, state: ${JSON.stringify(state)}`);
              }
            });
          } catch (error) {
            console.error(`getTouchpadPinchSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadPinchSwitch((error: BusinessError<void> | null, state: boolean | undefined) => {
              console.info(`getTouchpadPinchSwitch success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadPinchSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise对象，异步返回触控板双指捏合功能开启状态。true代表功能开启，false代表功能关闭，默认开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadPinchSwitch().then((state: boolean) => {
              console.info(`getTouchpadPinchSwitch success, state: ${JSON.stringify(state)}`);
            }).catch((error: BusinessError) => {
              console.error(`Get touchpad pinch switch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`getTouchpadPinchSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadPinchSwitch().then((state: boolean) => {
              console.info(`getTouchpadPinchSwitch success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadPinchSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadSwipeSwitch<sup>10+</sup>

setTouchpadSwipeSwitch(state: boolean, callback: AsyncCallback\<void>): void

设置触控板多指滑动功能开关，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state | boolean | 是    |触控板多指滑动开关开启状态。 true代表多指滑动开启，false代表多指滑动关闭，默认开启。   |
| callback | AsyncCallback\<void> | 是    | 回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadSwipeSwitch(true, (error: BusinessError) => {
              if (error) {
                console.error(`setTouchpadSwipeSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadSwipeSwitch success`);
            });
          } catch (error) {
            console.error(`setTouchpadSwipeSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```


ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.setTouchpadSwipeSwitch(true, (error: BusinessError<void> | null, data: undefined) => {
              if (error) {
                console.error(`setTouchpadSwipeSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadSwipeSwitch success`);
            });
          } catch (error) {
            console.error(`setTouchpadSwipeSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| state | boolean| 是    |  触控板多指滑动功能开关开启状态。 true代表多指滑动开启，false代表多指滑动关闭，默认开启。  |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadSwipeSwitch(false).then(() => {
              console.info(`setTouchpadSwipeSwitch success`);
            }).catch((error: BusinessError) => {
              console.error(`Set touchpad swipe switch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`setTouchpadSwipeSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.setTouchpadSwipeSwitch(false).then(() => {
              console.info(`setTouchpadSwipeSwitch success`);
            });
          } catch (error) {
            console.error(`setTouchpadSwipeSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadSwipeSwitch<sup>10+</sup>

getTouchpadSwipeSwitch(callback:  AsyncCallback\<boolean>): void

获取触控板多指滑动功能开启状态，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | 是    | 回调函数，异步返回触控板多指滑动功能开启状态。 true代表多指滑动开启，false代表多指滑动关闭，默认开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadSwipeSwitch((error: BusinessError, state: boolean) => {
              console.info(`getTouchpadSwipeSwitch success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadSwipeSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```


ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadSwipeSwitch((error: BusinessError<void> | null, state: boolean  | undefined) => {
              console.info(`getTouchpadSwipeSwitch success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadSwipeSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise对象，异步返回触控板多指滑动功能开启状态。 true代表多指滑动开启，false代表多指滑动关闭，默认开启。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadSwipeSwitch().then((state: boolean) => {
              console.info(`getTouchpadSwipeSwitch success, state: ${JSON.stringify(state)}`);
            }).catch((error: BusinessError) => {
              console.error(`Get touchpad swipe switch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`getTouchpadSwipeSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadSwipeSwitch().then((state: boolean) => {
              console.info(`getTouchpadSwipeSwitch success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadSwipeSwitch failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadRightClickType<sup>10+</sup>

setTouchpadRightClickType(type: RightClickType, callback: AsyncCallback\<void>): void

设置触控板右键菜单类型，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| type| [RightClickType](js-apis-pointer.md#rightclicktype10)| 是    |type代表触控板右键菜单类型。<br>- TOUCHPAD_RIGHT_BUTTON：按压触控板右键区域。<br>- TOUCHPAD_LEFT_BUTTON：按压触控板左键区域。<br>- TOUCHPAD_TWO_FINGER_TAP：双指轻击或双指按压触控板。<br>- TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON<sup>20+</sup>：双指轻击或双指按压触控板、或按压触控板右键区域。<br>- TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON<sup>20+</sup>：双指轻击或双指按压触控板、或按压触控板左键区域。<br>默认值为TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON。|
| callback | AsyncCallback\<void> | 是    | 回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadRightClickType(pointer.RightClickType.TOUCHPAD_RIGHT_BUTTON , (error: BusinessError) => {
              if (error) {
                console.error(`setTouchpadRightClickType, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadRightClickType success`);
            });
          } catch (error) {
            console.error(`setTouchpadRightClickType failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.setTouchpadRightClickType(pointer.RightClickType.TOUCHPAD_RIGHT_BUTTON , (error: BusinessError<void> | null, data: undefined) => {
              if (error) {
                console.error(`setTouchpadRightClickType, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadRightClickType success`);
            });
          } catch (error) {
            console.error(`setTouchpadRightClickType failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| type| [RightClickType](js-apis-pointer.md#rightclicktype10)| 是    |type代表触控板右键菜单类型。<br>- TOUCHPAD_RIGHT_BUTTON：按压触控板右键区域。<br>- TOUCHPAD_LEFT_BUTTON：按压触控板左键区域。<br>- TOUCHPAD_TWO_FINGER_TAP：双指轻击或双指按压触控板。<br>- TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON<sup>20+</sup>：双指轻击或双指按压触控板、或按压触控板右键区域。<br>- TOUCHPAD_TWO_FINGER_TAP_OR_LEFT_BUTTON<sup>20+</sup>：双指轻击或双指按压触控板、或按压触控板左键区域。<br>默认值为TOUCHPAD_TWO_FINGER_TAP_OR_RIGHT_BUTTON。|

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadRightClickType(pointer.RightClickType.TOUCHPAD_RIGHT_BUTTON).then(() => {
              console.info(`setTouchpadRightClickType success`);
            }).catch((error: BusinessError) => {
              console.error(`Set touchpad right click type failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`setTouchpadRightClickType failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.setTouchpadRightClickType(pointer.RightClickType.TOUCHPAD_RIGHT_BUTTON).then(() => {
              console.info(`setTouchpadRightClickType success`);
            });
          } catch (error) {
            console.error(`setTouchpadRightClickType failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadRightClickType<sup>10+</sup>

getTouchpadRightClickType(callback: AsyncCallback\<RightClickType>): void

获取触控板右键菜单类型，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<[RightClickType](js-apis-pointer.md#rightclicktype10)> | 是    | 回调函数，异步返回触控板右键菜单类型。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadRightClickType((error: BusinessError, type: pointer.RightClickType) => {
              console.info(`getTouchpadRightClickType success, type: ${JSON.stringify(type)}`);
            });
          } catch (error) {
            console.error(`getTouchpadRightClickType failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```


ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadRightClickType((error: BusinessError<void> | null, type: pointer.RightClickType | undefined) => {
              console.info(`getTouchpadRightClickType success, type: ${JSON.stringify(type)}`);
            });
          } catch (error) {
            console.error(`getTouchpadRightClickType failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<[RightClickType](js-apis-pointer.md#rightclicktype10) > | Promise对象，异步返回触控板右键菜单类型。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadRightClickType().then((type: pointer.RightClickType) => {
              console.info(`getTouchpadRightClickType success, typeed: ${JSON.stringify(type)}`);
            });
          } catch (error) {
            console.error(`getTouchpadRightClickType failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadRightClickType().then((type: pointer.RightClickType) => {
              console.info(`getTouchpadRightClickType success, typeed: ${JSON.stringify(type)}`);
            });
          } catch (error) {
            console.error(`getTouchpadRightClickType failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setPointerSize<sup>10+</sup>

ArkTS-Dyn: setPointerSize(size: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: setPointerSize(size: int, callback: AsyncCallback&lt;void&gt;): void

设置鼠标光标大小，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| size     | ArkTS-Dyn: number<br> ArkTS-Sta: int | 是    | 鼠标光标大小，范围为[1, 7]，默认为1，传参大于最大值就会被自动设置为最大值，传参小于最小值就会被设置为最小值。  |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数，当设置成功时，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setPointerSize(1, (error: Error) => {
              if (error) {
                console.error(`setPointerSize failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setPointerSize success`);
            });
          } catch (error) {
            console.error(`setPointerSize failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setPointerSize(1, (error: BusinessError<void> | null, data: undefined) => {
              if (error) {
                console.error(`setPointerSize failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setPointerSize success`);
            });
          } catch (error) {
            console.error(`setPointerSize failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setPointerSize<sup>10+</sup>

ArkTS-Dyn: setPointerSize(size: number): Promise&lt;void&gt;

ArkTS-Sta: setPointerSize(size: int): Promise&lt;void&gt;

设置鼠标光标大小，使用Promise异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| size  | TS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标光标大小，范围为[1, 7]，默认为1，传参大于最大值就会被自动设置为最大值，传参小于最小值就会被设置为最小值。 |

**返回值**：

| 参数                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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
            pointer.setPointerSize(3).then(() => {
              console.info(`setPointerSize success`);
            });
          } catch (error) {
            console.error(`setPointerSize failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setPointerSize(3).then(() => {
              console.info(`setPointerSize success`);
            });
          } catch (error) {
            console.error(`setPointerSize failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| size  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标光标大小，范围为[1, 7]，默认为1，传参大于最大值就会被自动设置为最大值，传参小于最小值就会被设置为最小值。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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
            pointer.setPointerSizeSync(5);
            console.info(`setPointerSizeSync success`);
          } catch (error) {
            console.error(`setPointerSizeSync failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setPointerSizeSync(5);
            console.info(`setPointerSizeSync success`);
          } catch (error) {
            console.error(`setPointerSizeSync failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getPointerSize<sup>10+</sup>

ArkTS-Dyn: getPointerSize(callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getPointerSize(callback: AsyncCallback&lt;int&gt;): void

获取鼠标光标大小，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br>ArkTS-Sta:AsyncCallback&lt;int&gt; | 是    | 回调函数，异步返回鼠标光标大小。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getPointerSize((error: Error, size: number) => {
              console.info(`getPointerSize success, size: ${JSON.stringify(size)}`);
            });
          } catch (error) {
            console.error(`getPointerSize failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.getPointerSize((error: BusinessError<void> | null, size: int | undefined) => {
              console.info(`getPointerSize success, size: ${JSON.stringify(size)}`);
            });
          } catch (error) {
            console.error(`getPointerSize failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getPointerSize<sup>10+</sup>

ArkTS-Dyn: getPointerSize(): Promise&lt;number&gt;

ArkTS-Sta: getPointerSize(): Promise&lt;int&gt;

获取当前鼠标光标大小，使用Promise异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 参数                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br>ArkTS-Sta: Promise&lt;int&gt; | Promise对象，异步返回鼠标光标大小。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |


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
            pointer.getPointerSize().then((size: number) => {
              console.info(`getPointerSize success, size: ${JSON.stringify(size)}`);
            });
          } catch (error) {
            console.error(`getPointerSize failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.getPointerSize().then((size: int) => {
              console.info(`getPointerSize success, size: ${JSON.stringify(size)}`);
            });
          } catch (error) {
            console.error(`getPointerSize failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 参数                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: number<br/>ArkTS-Sta: int | 鼠标光标大小。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |


**示例：**

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
            console.info(`getPointerSizeSync success, pointerSize: ${JSON.stringify(pointerSize)}`);
          } catch (error) {
            console.error(`getPointerSizeSync failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            console.info(`getPointerSizeSync success, pointerSize: ${JSON.stringify(pointerSize)}`);
          } catch (error) {
            console.error(`getPointerSizeSync failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setPointerColor<sup>10+</sup>

ArkTS-Dyn: setPointerColor(color: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: setPointerColor(color: int, callback: AsyncCallback&lt;void&gt;): void

设置鼠标光标颜色，使用AsyncCallback异步方式返回结果。

> **说明**：
>
> 设置和调试时，需连接外部设备，如鼠标、蓝牙等。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| color     | ArkTS-Dyn: number<br/>ArkTS-Sta: int                    | 是    | 鼠标光标颜色，默认为黑色：0x00000000。格式为ARGB，A为透明度，取值范围0-255。例如:0x013F2C4B,01代表透明度。数字越大，透明度越高，颜色越透明，当透明度为负数时也支持。例如color等于-1时，对应的color是0xFFFFFFFF。   |
| callback | AsyncCallback&lt;void&gt; | 是    | 回调函数，当设置成功时，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setPointerColor(0xF6C800, (error: BusinessError) => {
              if (error) {
                console.error(`setPointerColor failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setPointerColor success`);
            });
          } catch (error) {
            console.error(`setPointerColor failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setPointerColor(0xF6C800, (error: BusinessError | null) => {
              if (error) {
                console.error(`setPointerColor failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setPointerColor success`);
            });
        } catch (error) {
          console.error(`setPointerColor failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| color  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标光标颜色，默认为黑色：0x00000000。格式为ARGB，A为透明度，取值范围0-255。例如:0x013F2C4B,01代表透明度。数字越大，透明度越高，颜色越透明，当透明度为负数时也支持。例如color等于-1时，对应的color是0xFFFFFFFF。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setPointerColor(0xF6C800).then(() => {
              console.info(`setPointerColor success`);
            }).catch((error: BusinessError) => {
              console.error(`Set pointer color failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`setPointerColor failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setPointerColor(0xF6C800).then(() => {
              console.info(`setPointerColor success`);
            });
          } catch (error) {
            console.error(`setPointerColor failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| color  |  ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是    | 鼠标光标颜色，默认为黑色：0x00000000。格式为ARGB，A为透明度，取值范围0-255。例如:0x013F2C4B,01代表透明度。数字越大，透明度越高，颜色越透明，当透明度为负数时也支持。例如color等于-1时，对应的color是0xFFFFFFFF。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setPointerColorSync(0xF6C800);
            console.info(`setPointerColorSync success`);
          } catch (error) {
            console.error(`setPointerColorSync failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.setPointerColorSync(0xF6C800);
            console.info(`setPointerColorSync success`);
          } catch (error) {
            console.error(`setPointerColorSync failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getPointerColor<sup>10+</sup>

ArkTS-Dyn: getPointerColor(callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getPointerColor(callback: AsyncCallback&lt;int&gt;): void

获取鼠标光标颜色，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | ArkTS-Dyn: AsyncCallback&lt;number&gt;<br>ArkTS-Sta: AsyncCallback&lt;int&gt; | 是    | 回调函数，异步返回鼠标光标颜色。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getPointerColor((error: BusinessError, color: number) => {
              if (error) {
                console.error(`getPointerColor error: ${JSON.stringify(error, [`code`, `message`])}`);
              } else {
                console.info(`getPointerColor success, color: ${JSON.stringify(color)}`);
              }
            });
          } catch (error) {
            console.error(`getPointerColor failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.getPointerColor((error: BusinessError<void> | null, color: int | undefined) => {
              console.info(`getPointerColor success, color: ${JSON.stringify(color)}`);
            });
          } catch (error) {
            console.error(`getPointerColor failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：10

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| ArkTS-Dyn: Promise&lt;number&gt;<br> ArkTS-Sta: Promise&lt;int&gt; | Promise对象，异步返回鼠标光标颜色。 |

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
            pointer.getPointerColor().then((color: number) => {
              console.info(`getPointerColor success, color: ${JSON.stringify(color)}`);
            }).catch((error: BusinessError) => {
              console.error(`Get pointer color failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`getPointerColor failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            pointer.getPointerColor().then((color: int) => {
              console.info(`getPointerColor success, color: ${JSON.stringify(color)}`);
            });
          } catch (error) {
            console.error(`getPointerColor failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

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
            console.info(`getPointerColorSync success, pointerColor: ${JSON.stringify(pointerColor)}`);
          } catch (error) {
            console.error(`getPointerColorSync failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
            console.info(`getPointerColorSync success, pointerColor: ${JSON.stringify(pointerColor)}`);
          } catch (error) {
            console.error(`getPointerColorSync failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.setTouchpadDoubleTapAndDragState<sup>14+</sup>

setTouchpadDoubleTapAndDragState(isOpen: boolean, callback: AsyncCallback\<void>): void

设置触控板双击拖拽开关状态，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                        | 必填   | 说明                                    |
| -------- | ------------------------- | ---- | ------------------------------------- |
| isOpen | boolean | 是    | 双击拖拽开关的状态，true代表开启，false代表关闭。 |
| callback | AsyncCallback\<void> | 是    | 回调函数。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadDoubleTapAndDragState(true, (error: BusinessError) => {
              if (error) {
                console.error(`setTouchpadDoubleTapAndDragState failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadDoubleTapAndDragState success`);
            });
          } catch (error) {
            console.error(`setTouchpadDoubleTapAndDragState failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.setTouchpadDoubleTapAndDragState(true, (error: BusinessError<void> | null, data: undefined) => {
              if (error) {
                console.error(`setTouchpadDoubleTapAndDragState failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
                return;
              }
              console.info(`setTouchpadDoubleTapAndDragState success`);
            });
          } catch (error) {
            console.error(`setTouchpadDoubleTapAndDragState failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名    | 类型     | 必填   | 说明                                  |
| ----- | ------ | ---- | ----------------------------------- |
| isOpen | boolean | 是    | 双击拖拽开关的状态，true代表开启，false代表关闭。 |

**返回值**：

| 类型                  | 说明               |
| ------------------- | ---------------- |
| Promise\<void> | Promise对象，无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.setTouchpadDoubleTapAndDragState(false).then(() => {
              console.info(`setTouchpadDoubleTapAndDragState success`);
            }).catch((error: BusinessError) => {
              console.error(`Set touchpad failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`setTouchpadDoubleTapAndDragState failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.setTouchpadDoubleTapAndDragState(false).then(() => {
              console.info(`setTouchpadDoubleTapAndDragState success`);
            });
          } catch (error) {
            console.error(`setTouchpadDoubleTapAndDragState failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## pointer.getTouchpadDoubleTapAndDragState<sup>14+</sup>

getTouchpadDoubleTapAndDragState(callback: AsyncCallback\<boolean>): void

获取触控板双击拖拽开关的开启状态，使用AsyncCallback异步方式返回结果。

**系统能力**：SystemCapability.MultimodalInput.Input.Pointer

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：23

**参数**：

| 参数名       | 类型                          | 必填   | 说明             |
| -------- | --------------------------- | ---- | -------------- |
| callback | AsyncCallback\<boolean> | 是    | 回调函数，异步返回触控板双击拖拽开关的开启状态。返回true代表开启，返回false代表关闭。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 202  | SystemAPI permission error.  |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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
            pointer.getTouchpadDoubleTapAndDragState((error: BusinessError, state: boolean) => {
              if (error) {
                console.error(`getTouchpadDoubleTapAndDragState error: ${JSON.stringify(error, [`code`, `message`])}`);
              } else {
                console.info(`getTouchpadDoubleTapAndDragState success, state: ${JSON.stringify(state)}`);
              }
            });
          } catch (error) {
            console.error(`getTouchpadDoubleTapAndDragState failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadDoubleTapAndDragState((error: BusinessError<void> | null, state: boolean | undefined) => {
              console.info(`getTouchpadDoubleTapAndDragState success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadDoubleTapAndDragState failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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

**系统API**: 此接口为系统接口。

**ArkTS-Dyn起始版本**：14

**ArkTS-Sta起始版本**：23

**返回值**：

| 类型                    | 说明                  |
| --------------------- | ------------------- |
| Promise\<boolean> | Promise对象，异步返回触控板双击拖拽开启状态。true代表开启，false代表关闭。|

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
            pointer.getTouchpadDoubleTapAndDragState().then((state) => {
              console.info(`getTouchpadDoubleTapAndDragState success, state: ${JSON.stringify(state)}`);
            }).catch((error: BusinessError) => {
              console.error(`Get touchpad failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`getTouchpadDoubleTapAndDragState failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```


ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            pointer.getTouchpadDoubleTapAndDragState().then((state: boolean) => {
              console.info(`getTouchpadDoubleTapAndDragState success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadDoubleTapAndDragState failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        });
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
| Promise\<void> | Promise对象，无返回结果的Promise对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[鼠标光标错误码](./errorcode-pointer.md)

| 错误码ID   | 错误信息                        |
|---------|-----------------------------|
| 201     | Permission denied.          |
| 202     | SystemAPI permission error. |
| 3800001 | Input service exception.    |

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
      Button("setMouseScrollDirection")
        .onClick(() => {
          try {
            pointer.setMouseScrollDirection(false).then(() => {
              console.info(`setMouseScrollDirection success`);
            }).catch((error: BusinessError) => {
              console.error(`Set mouse scroll direction failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`setMouseScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text("setMouseScrollDirection")
        .onClick(() => {
          try {
            pointer.setMouseScrollDirection (false).then(() => {
              console.info(`setMouseScrollDirection success`);
            });
          } catch (error) {
            console.error(`setMouseScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
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
| Promise\<boolean> | Promise对象，异步返回获取鼠标滚轮滚动方向。<br>true与鼠标滚轮滚动的手指方向一致，false与鼠标滚轮滚动的手指方向相反。<br>默认为true。 |

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
            pointer.getMouseScrollDirection().then((state: boolean) => {
              console.info(`getMouseScrollDirection success, state: ${JSON.stringify(state)}`);
            }).catch((error: BusinessError) => {
              console.error(`Get mouse scroll direction failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
            })
          } catch (error) {
            console.error(`getMouseScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例:

```ts
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { pointer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text("getMouseScrollDirection")
        .onClick(() => {
          try {
            pointer.getTouchpadScrollDirection().then((state: boolean) => {
              console.info(`getTouchpadScrollDirection success, state: ${JSON.stringify(state)}`);
            });
          } catch (error) {
            console.error(`getTouchpadScrollDirection failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```