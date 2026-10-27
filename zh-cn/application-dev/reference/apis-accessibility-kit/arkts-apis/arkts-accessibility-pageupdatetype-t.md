# PageUpdateType

```TypeScript
type PageUpdateType = 'pageContentUpdate' | 'pageStateUpdate' | 'pageStatePreUpdate'
```

页面更新类型。页面更新事件在页面内容或状态发生变化时由无障碍服务触发，辅助功能扩展可通过onAccessibilityEvent回调接收并处理对应的页面更新事件。

**起始版本：** 9

<!--Device-unnamed-type PageUpdateType = 'pageContentUpdate' | 'pageStateUpdate' | 'pageStatePreUpdate'--><!--Device-unnamed-type PageUpdateType = 'pageContentUpdate' | 'pageStateUpdate' | 'pageStatePreUpdate'-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

| 类型 | 说明 |
| --- | --- |
| 'pageContentUpdate' | 表示页面内容更新。 |
| 'pageStateUpdate' | 表示页面状态更新。 |
| 'pageStatePreUpdate' | 表示页面状态即将更新。<br>**起始版本：** 26.1.0 |
