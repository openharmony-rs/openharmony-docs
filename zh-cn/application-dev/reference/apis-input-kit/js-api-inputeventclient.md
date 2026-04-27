# @ohos.multimodalInput.inputEventClient (输入事件注入)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

输入事件注入模块，提供键盘和鼠标输入事件模拟能力。

> **说明：**
>
> 本模块首批接口从API version 26开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { inputEventClient } from '@kit.InputKit';
```

## inputEventClient.createKeyboardController<sup>26+</sup>

createKeyboardController(): Promise&lt;KeyboardController&gt;

创建键盘控制器,用于模拟按键操作。使用Promise异步回调。

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**需要权限：** ohos.permission.CONTROL_DEVICE

**返回值：**

| 类型                   | 说明       |
| --------------------- | --------- |
| Promise&lt;[KeyboardController](#keyboardcontroller26)&gt; | Promise对象,返回键盘控制器实例。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | 权限校验失败。  |
| 801  | 能力不支持。  |
| 3800001  | 输入服务异常。  |

**示例：**

```js
import { inputEventClient } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let keyboardController = await inputEventClient.createKeyboardController();
            console.log('键盘控制器创建成功');
          } catch (error) {
            console.error(`创建键盘控制器失败, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## inputEventClient.createMouseController<sup>26+</sup>

createMouseController(): Promise&lt;MouseController&gt;

创建鼠标控制器,用于模拟鼠标操作。使用Promise异步回调。

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**需要权限：** ohos.permission.CONTROL_DEVICE

**返回值：**

| 类型                   | 说明       |
| --------------------- | --------- |
| Promise&lt;[MouseController](#mousecontroller26)&gt; | Promise对象,返回鼠标控制器实例。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | 权限校验失败。  |
| 801  | 能力不支持。  |
| 3800001  | 输入服务异常。  |

**示例：**

```js
import { inputEventClient } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            console.log('鼠标控制器创建成功');
          } catch (error) {
            console.error(`创建鼠标控制器失败, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## KeyboardController<sup>26+</sup>

提供模拟按键操作的功能。模拟按键操作序列必须满足以下要求：

1. 按键只能在释放状态下被按下,或者在该按键是最近按下的按键且未释放的情况下被按下。
2. 按键只能在被按下后才能释放。
3. 最多可以同时按下并保持五个按键。

### pressKey<sup>26+</sup>

pressKey(keyCode: KeyCode): Promise&lt;void&gt;

按下按键。使用Promise异步回调。

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**需要权限：** ohos.permission.CONTROL_DEVICE

**参数：**

| 参数名      | 类型                   | 必填  | 说明       |
| -------- | --------------------- | ---- | --------- |
| keyCode | [KeyCode](js-apis-keycode.md#keycode) | 是   | 要按下的按键键码。|

**返回值：**

| 类型                   | 说明       |
| --------------------- | --------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | 权限校验失败。  |
| 3800001  | 输入服务异常。  |
| 4300001  | 按键已被按下且不是最近按下的按键。  |

**示例：**

```js
import { inputEventClient, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let keyboardController = await inputEventClient.createKeyboardController();
            await keyboardController.pressKey(KeyCode.KEYCODE_A);
            console.log('按键按下成功');
          } catch (error) {
            console.error(`按键按下失败, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

### releaseKey<sup>26+</sup>

releaseKey(keyCode: KeyCode): Promise&lt;void&gt;

释放按键。使用Promise异步回调。

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**需要权限：** ohos.permission.CONTROL_DEVICE

**参数：**

| 参数名      | 类型                   | 必填  | 说明       |
| -------- | --------------------- | ---- | --------- |
| keyCode | [KeyCode](js-apis-keycode.md#keycode) | 是   | 要释放的按键键码。|

**返回值：**

| 类型                   | 说明       |
| --------------------- | --------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | 权限校验失败。  |
| 3800001  | 输入服务异常。  |
| 4300001  | 按键未被按下。  |

**示例：**

```js
import { inputEventClient, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let keyboardController = await inputEventClient.createKeyboardController();
            await keyboardController.pressKey(KeyCode.KEYCODE_A);
            await keyboardController.releaseKey(KeyCode.KEYCODE_A);
            console.log('按键释放成功');
          } catch (error) {
            console.error(`按键释放失败, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

## MouseController<sup>26+</sup>

提供模拟鼠标操作的功能。模拟鼠标操作序列必须满足以下要求：

1. 鼠标按键只能在释放状态下被按下。
2. 鼠标按键只能在被按下后才能释放。
3. 有效的轴事件序列必须先开始,包含零个或多个更新,然后结束。
4. 同一时间只能有一个进行中的轴事件序列。

### moveTo<sup>26+</sup>

moveTo(displayId: number, displayX: number, displayY: number): Promise&lt;void&gt;

将鼠标光标移动到指定的显示器坐标。使用Promise异步回调。

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**需要权限：** ohos.permission.CONTROL_DEVICE

**参数：**

| 参数名      | 类型                   | 必填  | 说明       |
| -------- | --------------------- | ---- | --------- |
| displayId | int | 是   | 目标显示器ID。|
| displayX | int | 是   | 目标位置相对于显示器左边缘的X坐标,单位:px。|
| displayY | int | 是   | 目标位置相对于显示器上边缘的Y坐标,单位:px。|

**返回值：**

| 类型                   | 说明       |
| --------------------- | --------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | 权限校验失败。  |
| 3800001  | 输入服务异常。  |
| 4300002  | 显示器不存在。  |

**示例：**

```js
import { inputEventClient } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            await mouseController.moveTo(0, 100, 200);
            console.log('鼠标移动成功');
          } catch (error) {
            console.error(`鼠标移动失败, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

### pressButton<sup>26+</sup>

pressButton(button: Button): Promise&lt;void&gt;

按下鼠标按键。使用Promise异步回调。

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**需要权限：** ohos.permission.CONTROL_DEVICE

**参数：**

| 参数名      | 类型                   | 必填  | 说明       |
| -------- | --------------------- | ---- | --------- |
| button | [Button](js-apis-mouseevent.md#button) | 是   | 要按下的鼠标按键。|

**返回值：**

| 类型                   | 说明       |
| --------------------- | --------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | 权限校验失败。  |
| 3800001  | 输入服务异常。  |
| 4300001  | 鼠标按键已被按下。  |

**示例：**

```js
import { inputEventClient, Button } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            await mouseController.pressButton(Button.LEFT);
            console.log('鼠标按键按下成功');
          } catch (error) {
            console.error(`鼠标按键按下失败, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

### releaseButton<sup>26+</sup>

releaseButton(button: Button): Promise&lt;void&gt;

释放鼠标按键。使用Promise异步回调。

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**需要权限：** ohos.permission.CONTROL_DEVICE

**参数：**

| 参数名      | 类型                   | 必填  | 说明       |
| -------- | --------------------- | ---- | --------- |
| button | [Button](js-apis-mouseevent.md#button) | 是   | 要释放的鼠标按键。|

**返回值：**

| 类型                   | 说明       |
| --------------------- | --------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | 权限校验失败。  |
| 3800001  | 输入服务异常。  |
| 4300001  | 鼠标按键未被按下。  |

**示例：**

```js
import { inputEventClient, Button } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            await mouseController.pressButton(Button.LEFT);
            await mouseController.releaseButton(Button.LEFT);
            console.log('鼠标按键释放成功');
          } catch (error) {
            console.error(`鼠标按键释放失败, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

### beginAxis<sup>26+</sup>

beginAxis(axis: Axis, value: number): Promise&lt;void&gt;

开始轴事件。使用Promise异步回调。

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**需要权限：** ohos.permission.CONTROL_DEVICE

**参数：**

| 参数名      | 类型                   | 必填  | 说明       |
| -------- | --------------------- | ---- | --------- |
| axis | [Axis](js-apis-mouseevent.md#axis) | 是   | 轴类型。|
| value | int | 是   | 轴值。|

**返回值：**

| 类型                   | 说明       |
| --------------------- | --------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | 权限校验失败。  |
| 3800001  | 输入服务异常。  |
| 4300001  | 轴事件正在进行中。  |

**示例：**

```js
import { inputEventClient, Axis } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            await mouseController.beginAxis(Axis.VERTICAL_SCROLL, 10);
            console.log('轴事件开始成功');
          } catch (error) {
            console.error(`轴事件开始失败, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

### updateAxis<sup>26+</sup>

updateAxis(axis: Axis, value: number): Promise&lt;void&gt;

更新轴事件。使用Promise异步回调。

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**需要权限：** ohos.permission.CONTROL_DEVICE

**参数：**

| 参数名      | 类型                   | 必填  | 说明       |
| -------- | --------------------- | ---- | --------- |
| axis | [Axis](js-apis-mouseevent.md#axis) | 是   | 轴类型。|
| value | int | 是   | 轴值。|

**返回值：**

| 类型                   | 说明       |
| --------------------- | --------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | 权限校验失败。  |
| 3800001  | 输入服务异常。  |
| 4300001  | 轴事件未在进行中。  |

**示例：**

```js
import { inputEventClient, Axis } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            await mouseController.beginAxis(Axis.VERTICAL_SCROLL, 10);
            await mouseController.updateAxis(Axis.VERTICAL_SCROLL, 20);
            console.log('轴事件更新成功');
          } catch (error) {
            console.error(`轴事件更新失败, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```

### endAxis<sup>26+</sup>

endAxis(axis: Axis): Promise&lt;void&gt;

结束轴事件。使用Promise异步回调。

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**需要权限：** ohos.permission.CONTROL_DEVICE

**参数：**

| 参数名      | 类型                   | 必填  | 说明       |
| -------- | --------------------- | ---- | --------- |
| axis | [Axis](js-apis-mouseevent.md#axis) | 是   | 轴类型。|

**返回值：**

| 类型                   | 说明       |
| --------------------- | --------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | 权限校验失败。  |
| 3800001  | 输入服务异常。  |
| 4300001  | 轴事件未在进行中。  |

**示例：**

```js
import { inputEventClient, Axis } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(async () => {
          try {
            let mouseController = await inputEventClient.createMouseController();
            await mouseController.beginAxis(Axis.VERTICAL_SCROLL, 10);
            await mouseController.updateAxis(Axis.VERTICAL_SCROLL, 20);
            await mouseController.endAxis(Axis.VERTICAL_SCROLL);
            console.log('轴事件结束成功');
          } catch (error) {
            console.error(`轴事件结束失败, error: ${JSON.stringify(error, [`code`, `message`])}`);
          }
        })
    }
  }
}
```
