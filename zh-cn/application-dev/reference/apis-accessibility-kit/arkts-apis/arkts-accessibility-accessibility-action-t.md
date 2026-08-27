# Action

```TypeScript
type Action = 'accessibilityFocus' | 'clearAccessibilityFocus' | 'focus' | 'clearFocus' | 'clearSelection' |
  'click' | 'longClick' | 'cut' | 'copy' | 'paste' | 'select' | 'setText' | 'delete' |
  'scrollForward' | 'scrollBackward' | 'setSelection' | 'setCursorPosition' | 'home' |
  'back' | 'recentTask' | 'notificationCenter' | 'controlCenter' | 'common' | 'injectAction' | 'executeCustomAction'
```

应用所支持的目标动作，需要配置参数的目标动作已在下表各动作的说明列中标明。

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

| 类型 | 说明 |
| --- | --- |
| 'accessibilityFocus' | 表示获得无障碍焦点操作，需配置参数accessibilityFocusScene，参数值为无障碍聚焦的场景类型。 |
| 'clearAccessibilityFocus' | 表示清除无障碍焦点操作。 |
| 'focus' | 表示获得焦点操作。 |
| 'clearFocus' | 表示清除焦点操作。 |
| 'clearSelection' | 表示清除选择操作。当前版本暂不支持。 |
| 'click' | 表示点击操作。 |
| 'longClick' | 表示长按操作。 |
| 'cut' | 表示剪切操作。 |
| 'copy' | 表示复制操作。 |
| 'paste' | 表示粘贴操作。 |
| 'select' | 表示选择操作。 |
| 'setText' | 表示设置文本操作，需配置参数setText，参数值为要设置的文本内容。 |
| 'delete' | 表示删除操作。当前版本暂不支持。 |
| 'scrollForward' | 表示向前滚动操作，需配置参数scrollType，参数值为'fullScreen'或'halfScreen'。 |
| 'scrollBackward' | 表示向后滚动操作，需配置参数scrollType，参数值为'fullScreen'或'halfScreen'。 |
| 'setSelection' | 表示设置文本选择范围操作，需配置参数selectTextBegin、selectTextEnd、selectTextInForWard，参数值为选定文本的起始坐标、结 束坐标及是否向前选择。 |
| 'setCursorPosition' | 表示设置光标位置操作，需配置参数offset，参数值为光标的字符偏移量。 [since 12] |
| 'home' | 表示返回桌面操作。 [since 12] |
| 'back' | 表示返回上一级操作。 [since 12] |
| 'recentTask' | 表示打开最近任务操作。 [since 12] |
| 'notificationCenter' | 表示打开通知栏操作。 [since 12] |
| 'controlCenter' | 表示打开控制中心操作。 [since 12] |
| 'common' | 表示没有特定操作，用于主动聚焦、主动播报等场景。 [since 12] |
| 'injectAction' | 表示注入动作，需配置参数injectActionType，参数值为注入动作类型。 [since 26.0.0] |
| 'executeCustomAction' | 表示执行自定义操作，需配置参数customAction，参数值为自定义操作的名称。 [since 26.0.0] |
