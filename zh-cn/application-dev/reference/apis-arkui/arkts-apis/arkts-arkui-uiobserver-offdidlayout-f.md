# off_didLayout

## off_didLayout

```TypeScript
export function off(type: 'didLayout', context: UIContext, callback?: Callback<void>): void
```

取消监听每一帧布局完成情况。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'didLayout', context: UIContext, callback?: Callback<void>): void--><!--Device-uiObserver-export function off(type: 'didLayout', context: UIContext, callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didLayout' | 是 | 监听事件，固定为'didLayout'，即是否布局完成。 |
| context | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 需要被注销的回调函数。 |

