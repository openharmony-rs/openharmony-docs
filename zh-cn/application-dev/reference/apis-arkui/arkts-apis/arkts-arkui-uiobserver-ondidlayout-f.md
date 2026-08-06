# onDidLayout

## onDidLayout

```TypeScript
export function onDidLayout(context: UIContext, callback: Callback<void>): void
```

Registers a callback function to be called when the layout is done.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function onDidLayout(context: UIContext, callback: Callback<void>): void--><!--Device-uiObserver-export function onDidLayout(context: UIContext, callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The context scope of the observer. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | The callback function to be called when the layout is done. |

