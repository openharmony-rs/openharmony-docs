# InputEventListener

```TypeScript
export declare type InputEventListener = (
  event: RawInputEventWrapper
) => InputEventInterceptResult
```

Defines the input event listener callback function type. Performance Warning: Do not perform time-consuming operations in the callback, otherwise it may cause the application to freeze. The listener executes synchronously in the UI thread and will directly block the event processing flow. It is recommended to only perform simple judgments and calculations, avoiding: - Synchronous I/O operations - Complex data processing - Network requests - Massive log output

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare type InputEventListener = (  event: RawInputEventWrapper) => InputEventInterceptResult--><!--Device-unnamed-export declare type InputEventListener = (  event: RawInputEventWrapper) => InputEventInterceptResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Input event wrapper  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | - Event intercept result |

