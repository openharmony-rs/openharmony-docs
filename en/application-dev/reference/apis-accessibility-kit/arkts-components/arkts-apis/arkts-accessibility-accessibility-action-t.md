# Action

```TypeScript
type Action = 'accessibilityFocus' | 'clearAccessibilityFocus' | 'focus' | 'clearFocus' | 'clearSelection' |
  'click' | 'longClick' | 'cut' | 'copy' | 'paste' | 'select' | 'setText' | 'delete' |
  'scrollForward' | 'scrollBackward' | 'setSelection' | 'setCursorPosition' | 'home' |
  'back' | 'recentTask' | 'notificationCenter' | 'controlCenter' | 'common' | 'injectAction' | 'executeCustomAction'
```

Target actions supported by the app. Target actions that require configuration parameters are indicated in the description column of each action in the table below.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'accessibilityFocus' | Obtain accessibility focus. The parameter **accessibilityFocusScene** must be configured, with the value being the type of the accessibility focus scene. |
| 'clearAccessibilityFocus' | Clear accessibility focus. |
| 'focus' | Obtain focus. |
| 'clearFocus' | Clear focus. |
| 'clearSelection' | Clear selection. This feature is not supported in the current version. |
| 'click' | Click. |
| 'longClick' | Long press. |
| 'cut' | Cut. |
| 'copy' | Copy. |
| 'paste' | Paste. |
| 'select' | Select. |
| 'setText' | Set text. The parameter **setText** must be configured, with the value being the text content to set. |
| 'delete' | Delete. This feature is not supported in the current version. |
| 'scrollForward' | Scroll forward. The parameter **scrollType** must be configured, with the value **'fullScreen'** or **'halfScreen'**. |
| 'scrollBackward' | Scroll backward. The parameter **scrollType** must be configured, with the value **'fullScreen'** or **'halfScreen'**. |
| 'setSelection' | Set the text selection range. The parameters **selectTextBegin**, **selectTextEnd**, and **selectTextInForWard** must be configured, with the values being the start coordinate, end coordinate, and whether to select forward. |
| 'setCursorPosition' | Set the cursor position. The parameter **offset** must be configured, with the value being the character offset of the cursor. [since 12] |
| 'home' | Return to the home screen. [since 12] |
| 'back' | Return to the previous level. [since 12] |
| 'recentTask' | Open recent tasks. [since 12] |
| 'notificationCenter' | Open the notification panel. [since 12] |
| 'controlCenter' | Open the control center. [since 12] |
| 'common' | No specific action, used for scenarios such as active focus and active announcement. [since 12] |
| 'injectAction' | Inject an action. The parameter **injectActionType** must be configured, with the value being the type of the injected action. [since 26.0.0] |
| 'executeCustomAction' | Execute a custom action. The parameter **customAction** must be configured, with the value being the name of the custom action. [since 26.0.0] |
