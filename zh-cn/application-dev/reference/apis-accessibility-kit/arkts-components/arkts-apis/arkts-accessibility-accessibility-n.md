# accessibility(辅助功能)

本模块提供辅助功能相关能力，包括获取辅助应用列表、获取辅助应用启用状态、获取无障碍字幕配置、发送无障碍事件、监听辅助应用状态变化等。

**起始版本：** 7

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [isOpenAccessibility](arkts-accessibility-accessibility-isopenaccessibility-f.md) | 判断是否启用了辅助应用。使用callback异步回调。 |
| [isOpenAccessibility](arkts-accessibility-accessibility-isopenaccessibility-f.md) | 判断是否启用了辅助应用。使用Promise异步回调。 |
| [isOpenAccessibilitySync](arkts-accessibility-accessibility-isopenaccessibilitysync-f.md) | 查询当前系统内是否存在已开启的辅助应用。 |
| [isOpenTouchGuide](arkts-accessibility-accessibility-isopentouchguide-f.md) | 判断触摸浏览模式是否开启。使用callback异步回调。 |
| [isOpenTouchGuide](arkts-accessibility-accessibility-isopentouchguide-f.md) | 判断触摸浏览模式是否开启。使用Promise异步回调。 |
| [isOpenTouchGuideSync](arkts-accessibility-accessibility-isopentouchguidesync-f.md) | 查询触摸浏览模式是否开启。 |
| [getAbilityLists](arkts-accessibility-accessibility-getabilitylists-f.md) | 查询辅助应用列表。使用callback异步回调。 |
| [getAbilityLists](arkts-accessibility-accessibility-getabilitylists-f.md) | 查询辅助应用列表。使用Promise异步回调。 |
| [getAccessibilityExtensionList](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md) | 查询辅助应用列表。使用Promise异步回调。 |
| [getAccessibilityExtensionList](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md) | 查询辅助应用列表。使用callback异步回调。 |
| [getAccessibilityExtensionListSync](arkts-accessibility-accessibility-getaccessibilityextensionlistsync-f.md) | 查询当前系统内辅助应用列表，支持按条件查询。 |
| [sendEvent](arkts-accessibility-accessibility-sendevent-f.md) | 发送无障碍事件，事件将被分发到系统中已注册且匹配事件类型的辅助扩展应用进行响应。使用callback异步回调。 |
| [sendEvent](arkts-accessibility-accessibility-sendevent-f.md) | 发送无障碍事件，事件将被分发到系统中已注册且匹配事件类型的辅助扩展应用进行响应。使用Promise异步回调。 |
| [sendAccessibilityEvent](arkts-accessibility-accessibility-sendaccessibilityevent-f.md) | 发送无障碍事件，事件将被分发到系统中已注册且匹配事件类型的辅助应用进行响应。使用callback异步回调。 |
| [sendAccessibilityEvent](arkts-accessibility-accessibility-sendaccessibilityevent-f.md) | 发送无障碍事件，事件将被分发到系统中已注册且匹配事件类型的辅助扩展应用进行响应。使用Promise异步回调。 |
| [on](arkts-accessibility-accessibility-on-f.md#onaccessibilitystatechange) | 监听辅助应用启用状态变化事件。使用callback异步回调。 |
| [on](arkts-accessibility-accessibility-on-f.md#ontouchguidestatechange) | 监听触摸浏览功能启用状态变化事件。使用callback异步回调。 |
| [off](arkts-accessibility-accessibility-off-f.md#offaccessibilitystatechange) | 取消监听辅助应用启用状态变化事件。使用callback异步回调。 |
| [off](arkts-accessibility-accessibility-off-f.md#offtouchguidestatechange) | 取消监听触摸浏览启用状态变化事件。使用callback异步回调。 |
| [getCaptionsManager](arkts-accessibility-accessibility-getcaptionsmanager-f.md) | 获取无障碍字幕配置管理实例。 |
| [isScreenReaderOpenSync](arkts-accessibility-accessibility-isscreenreaderopensync-f.md) | 查询屏幕朗读模式是否开启。 |
| [on](arkts-accessibility-accessibility-on-f.md#onscreenreaderstatechange) | 监听屏幕朗读模式启用状态变化事件。使用callback异步回调。 |
| [off](arkts-accessibility-accessibility-off-f.md#offscreenreaderstatechange) | 取消监听屏幕朗读启用状态变化事件。使用callback异步回调。 |
| [on](arkts-accessibility-accessibility-on-f.md#ontouchmodechange) | 监听触摸浏览功能下的单击/双击操作模式变化事件。使用callback异步回调。 |
| [off](arkts-accessibility-accessibility-off-f.md#offtouchmodechange) | 取消监听触摸浏览功能下的单击/双击操作模式变化事件。使用callback异步回调。 |
| [getTouchModeSync](arkts-accessibility-accessibility-gettouchmodesync-f.md) | 查询触摸浏览功能下的单击/双击操作模式，可用于根据当前操作模式调整应用的交互响应方式（如单击模式下直接响应点击、双击模式下需双击确认操作）。 |
| [onAnimationReduceStateChange](arkts-accessibility-accessibility-onanimationreducestatechange-f.md) | 监听减弱动效模式启用状态变化事件。使用callback异步回调。 |
| [offAnimationReduceStateChange](arkts-accessibility-accessibility-offanimationreducestatechange-f.md) | 取消监听减弱动效模式变化事件。使用callback异步回调。 |
| [isAnimationReduceEnabledSync](arkts-accessibility-accessibility-isanimationreduceenabledsync-f.md) | 查询减弱动效模式是否开启。 |
| [isAnimationReduceEnabled](arkts-accessibility-accessibility-isanimationreduceenabled-f.md) | 查询减弱动效模式是否开启。使用Promise异步回调。 |
| [onFlashReminderStateChange](arkts-accessibility-accessibility-onflashreminderstatechange-f.md) | 监听闪烁提醒模式启用状态变化事件。使用callback异步回调。 |
| [offFlashReminderStateChange](arkts-accessibility-accessibility-offflashreminderstatechange-f.md) | 取消监听闪烁提醒模式变化事件。使用callback异步回调。 |
| [isFlashReminderEnabledSync](arkts-accessibility-accessibility-isflashreminderenabledsync-f.md) | 查询闪烁提醒模式是否开启。 |
| [isFlashReminderEnabled](arkts-accessibility-accessibility-isflashreminderenabled-f.md) | 查询闪烁提醒模式是否开启。使用Promise异步回调。 |
| [onAudioMonoStateChange](arkts-accessibility-accessibility-onaudiomonostatechange-f.md) | 监听单声道音频模式启用状态变化事件。使用callback异步回调。 |
| [offAudioMonoStateChange](arkts-accessibility-accessibility-offaudiomonostatechange-f.md) | 取消监听单声道音频模式变化事件。使用callback异步回调。 |
| [isAudioMonoEnabledSync](arkts-accessibility-accessibility-isaudiomonoenabledsync-f.md) | 查询单声道音频模式是否开启。 |
| [isAudioMonoEnabled](arkts-accessibility-accessibility-isaudiomonoenabled-f.md) | 查询单声道音频模式是否开启。使用Promise异步回调。 |
| [onSeniorModeStateChange](arkts-accessibility-accessibility-onseniormodestatechange-f.md) | 监听系统关怀模式启用状态变化事件。使用callback异步回调。 |
| [offSeniorModeStateChange](arkts-accessibility-accessibility-offseniormodestatechange-f.md) | 取消监听系统关怀模式变化事件。使用callback异步回调。 |
| [isSeniorModeEnabled](arkts-accessibility-accessibility-isseniormodeenabled-f.md) | 查询系统关怀模式是否开启。使用Promise异步回调。 |
| [onSeniorModeStateChangeForSelf](arkts-accessibility-accessibility-onseniormodestatechangeforself-f.md) | 监听应用自身“长辈模式”变化事件。使用callback异步回调。 |
| [offSeniorModeStateChangeForSelf](arkts-accessibility-accessibility-offseniormodestatechangeforself-f.md) | 取消监听应用自身“长辈模式”变化事件。使用callback异步回调。 |
| [getSeniorModeStateForSelf](arkts-accessibility-accessibility-getseniormodestateforself-f.md) | 判断应用是否开启“长辈模式”。使用Promise异步回调。 |
| [setSeniorModeStateForSelf](arkts-accessibility-accessibility-setseniormodestateforself-f.md) | 设置应用是否开启“长辈模式”。使用Promise异步回调。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [EventInfo](arkts-accessibility-accessibility-eventinfo-c.md) | 无障碍事件信息，用于描述界面变更或交互事件，作为[sendAccessibilityEvent](arkts-accessibility-accessibility-sendaccessibilityevent-f.md)的参数定义事件的类型和触发动作。发送的无障碍事件将被系统分发到已注册且匹配事件类型的辅助应用进行响应，详见[sendAccessibilityEvent](arkts-accessibility-accessibility-sendaccessibilityevent-f.md)。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CaptionsManager](arkts-accessibility-accessibility-captionsmanager-i.md) | 字幕配置管理。调用CaptionsManager的方法前，先调用[accessibility.getCaptionsManager()](arkts-accessibility-accessibility-getcaptionsmanager-f.md)获取CaptionsManager实例。 |
| [CaptionsStyle](arkts-accessibility-accessibility-captionsstyle-i.md) | 字幕风格。 |
| [AccessibilityAbilityInfo](arkts-accessibility-accessibility-accessibilityabilityinfo-i.md) | 辅助应用信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityType](arkts-accessibility-accessibility-abilitytype-t.md) | 无障碍辅助应用类型。 |
| [Action](arkts-accessibility-accessibility-action-t.md) | 应用所支持的目标动作，需要配置参数的目标动作已在下表各动作的说明列中标明。 |
| [EventType](arkts-accessibility-accessibility-eventtype-t.md) | 无障碍事件类型。 |
| [WindowUpdateType](arkts-accessibility-accessibility-windowupdatetype-t.md) | 窗口变化类型。 |
| [AbilityState](arkts-accessibility-accessibility-abilitystate-t.md) | 辅助应用状态类型。 |
| [Capability](arkts-accessibility-accessibility-capability-t.md) | 辅助应用能力类型。 |
| [TextMoveUnit](arkts-accessibility-accessibility-textmoveunit-t.md) | 文本无障碍导航移动粒度。 |
| [CaptionsFontEdgeType](arkts-accessibility-accessibility-captionsfontedgetype-t.md) | 字幕字体边缘类型。 |
| [CaptionsFontFamily](arkts-accessibility-accessibility-captionsfontfamily-t.md) | 字幕字体。 |
