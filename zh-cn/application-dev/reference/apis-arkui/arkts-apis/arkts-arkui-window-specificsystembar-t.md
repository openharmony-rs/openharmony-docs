# SpecificSystemBar

```TypeScript
type SpecificSystemBar = 'status' | 'navigation'| 'navigationIndicator'
```

当前支持显示或隐藏的系统栏类型。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-window-type SpecificSystemBar = 'status' | 'navigation'| 'navigationIndicator'--><!--Device-window-type SpecificSystemBar = 'status' | 'navigation'| 'navigationIndicator'-End-->

**系统能力：** SystemCapability.Window.SessionManager

| 类型 | 说明 |
| --- | --- |
| 'status' | Status bar. |
| 'navigation' | <!--RP13--><!--RP13End-->Three-button navigation bar. |
| 'navigationIndicator' | Bottom navigation bar. <!--RP12-->OpenHarmony devices do not support this capability.<!--RP12End--> |

