# off_densityUpdate

## off_densityUpdate

```TypeScript
export function off(type: 'densityUpdate', context: UIContext, callback?: Callback<DensityInfo>): void
```

取消监听屏幕像素密度的变化。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'densityUpdate', context: UIContext, callback?: Callback<DensityInfo>): void--><!--Device-uiObserver-export function off(type: 'densityUpdate', context: UIContext, callback?: Callback<DensityInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'densityUpdate' | 是 | 监听事件，固定为'densityUpdate'，即屏幕像素密度变化。 |
| context | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DensityInfo](arkts-arkui-uiobserver-densityinfo-c.md)&gt; | 否 | 需要被注销的回调函数。若不指定具体的回调函数，则注销指定UIContext下所有densityUpdate事件监听。 |

