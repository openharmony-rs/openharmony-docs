# InputEventListener

```TypeScript
declare type InputEventListener = (
  event: RawInputEventWrapper
) => InputEventInterceptResult
```

输入事件监听器回调函数类型。

> **说明：**
>
> - RawInputEventWrapper是抽象类，开发者无法使用`new`运算符创建实例。
>
> - 系统会在事件触发时自动创建实例并通过此参数传递给回调函数。
>
> - 当前回调参数event仅会封装以下原始输入事件类型：
> [MouseEvent](arkts-arkui-common-mouseevent-i.md#MouseEvent)、[TouchEvent](arkts-arkui-common-touchevent-i.md#TouchEvent)、[KeyEvent](arkts-arkui-common-keyevent-i.md#KeyEvent)。开发者可通过
> [asMouseEvent](arkts-arkui-rawinputeventwrapper-c.md#asMouseEvent-1)、[asTouchEvent](arkts-arkui-rawinputeventwrapper-c.md#asTouchEvent-1)、
> [asKeyEvent](arkts-arkui-rawinputeventwrapper-c.md#asKeyEvent-1)获取对应事件对象。
>
> - 请勿在回调中执行耗时操作（如复杂计算或网络请求），否则可能导致应用卡顿。
>
> - 监听器在UI线程中同步执行会直接阻塞事件处理流程。建议只进行简单的判断和计算。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | RawInputEventWrapper | 是 | 输入事件包装器，系统自动创建和传递，开发者无需手动创建。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| InputEventInterceptResult | 事件拦截结果。 |

