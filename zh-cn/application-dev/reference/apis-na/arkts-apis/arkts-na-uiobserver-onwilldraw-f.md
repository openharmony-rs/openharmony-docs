# onWillDraw

## 导入模块

```TypeScript
```

## onWillDraw

```TypeScript
export function onWillDraw(context: UIContext, callback: Callback<void>): void
```

Registers a callback function to be called when the draw command will be drawn.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function onWillDraw(context: UIContext, callback: Callback<void>): void--><!--Device-uiObserver-export function onWillDraw(context: UIContext, callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIContext](arkts-na-arkui-uicontext-uicontext-c.md) | 是 | The context scope of the observer. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | The callback function to be called when the draw command will be drawn. |

