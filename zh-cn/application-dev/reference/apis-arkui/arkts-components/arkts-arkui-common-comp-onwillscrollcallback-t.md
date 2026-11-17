# OnWillScrollCallback

```TypeScript
declare type OnWillScrollCallback =
(scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | ScrollResult
```

滚动组件滑动前触发的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-declare type OnWillScrollCallback =(scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | ScrollResult--><!--Device-unnamed-declare type OnWillScrollCallback =(scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | ScrollResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollOffset | number | 是 | 相对于上一帧的偏移量，滚动组件的内容向上滚动时偏移量为正，向下滚动时偏移量为负。<br>单位vp。 |
| scrollState | [ScrollState](arkts-arkui-list-comp-scrollstate-e.md) | 是 | 当前滑动状态。 |
| scrollSource | [ScrollSource](../arkts-apis/arkts-arkui-scrollsource-e.md) | 是 | 当前滑动操作的来源。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| void &#124; [ScrollResult](arkts-arkui-common-comp-scrollresult-c.md) | 返回ScrollResult时按照开发者指定的相对上一帧的偏移量滑动；不返回时按回调参数scrollOffset滑动。<br>取值范围：(-∞, +∞) |
