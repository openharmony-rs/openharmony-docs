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
| [isOpenAccessibility(辅助功能)](arkts-accessibility-accessibility-isopenaccessibility-f.md) | 判断是否启用了辅助应用。使用callback异步回调。 |
| [isOpenAccessibility(辅助功能)](arkts-accessibility-accessibility-isopenaccessibility-f.md) | 判断是否启用了辅助应用。使用Promise异步回调。 |
| [isOpenAccessibilitySync(辅助功能)](arkts-accessibility-accessibility-isopenaccessibilitysync-f.md) | 查询当前系统内是否存在已开启的辅助应用。如需获取系统内辅助应用信息，推荐使用 [accessibility.getAccessibilityExtensionListSync](arkts-accessibility-accessibility-getaccessibilityextensionlistsync-f.md)。 |
| [isOpenTouchGuide(辅助功能)](arkts-accessibility-accessibility-isopentouchguide-f.md) | 判断触摸浏览模式是否开启。使用callback异步回调。 |
| [isOpenTouchGuide(辅助功能)](arkts-accessibility-accessibility-isopentouchguide-f.md) | 判断触摸浏览模式是否开启。使用Promise异步回调。 |
| [isOpenTouchGuideSync(辅助功能)](arkts-accessibility-accessibility-isopentouchguidesync-f.md) | 查询触摸浏览模式是否开启。 |
| [getAbilityLists(辅助功能)](arkts-accessibility-accessibility-getabilitylists-f.md) | 查询辅助应用列表。使用callback异步回调。 |
| [getAbilityLists(辅助功能)](arkts-accessibility-accessibility-getabilitylists-f.md) | 查询辅助应用列表。使用Promise异步回调。 |
| [getAccessibilityExtensionList(辅助功能)](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md) | 查询辅助应用列表。使用Promise异步回调。 |
| [getAccessibilityExtensionList(辅助功能)](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md) | 查询辅助应用列表。使用callback异步回调。 |
| [getAccessibilityExtensionListSync(辅助功能)](arkts-accessibility-accessibility-getaccessibilityextensionlistsync-f.md) | 查询当前系统内辅助应用列表，支持按条件查询。本接口为同步版本，与[accessibility.getAccessibilityExtensionList](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md)（异步版本）功能相 同，如需立即获取结果可使用本接口，如需在非阻塞场景下查询建议使用异步版本。 |
| [sendEvent(辅助功能)](arkts-accessibility-accessibility-sendevent-f.md) | 发送无障碍事件，事件将被分发到系统中已注册且匹配事件类型的辅助扩展应用进行响应。使用callback异步回调。 |
| [sendEvent(辅助功能)](arkts-accessibility-accessibility-sendevent-f.md) | 发送无障碍事件，事件将被分发到系统中已注册且匹配事件类型的辅助扩展应用进行响应。使用Promise异步回调。 |
| [sendAccessibilityEvent(辅助功能)](arkts-accessibility-accessibility-sendaccessibilityevent-f.md) | 发送无障碍事件，事件将被分发到系统中已注册且匹配事件类型的辅助应用进行响应。使用callback异步回调。 |
| [sendAccessibilityEvent(辅助功能)](arkts-accessibility-accessibility-sendaccessibilityevent-f.md) | 发送无障碍事件，事件将被分发到系统中已注册且匹配事件类型的辅助扩展应用进行响应。使用Promise异步回调。 |
| [on(辅助功能)](arkts-accessibility-accessibility-on-f.md#onaccessibilitystatechange) | 监听辅助应用启用状态变化事件。使用callback异步回调。如需获取系统内辅助应用信息，推荐使用 [accessibility.getAccessibilityExtensionListSync](arkts-accessibility-accessibility-getaccessibilityextensionlistsync-f.md)。 |
| [on(辅助功能)](arkts-accessibility-accessibility-on-f.md#ontouchguidestatechange) | 监听触摸浏览功能启用状态变化事件。使用callback异步回调。如需获取系统内辅助应用信息，推荐使用 [accessibility.getAccessibilityExtensionListSync](arkts-accessibility-accessibility-getaccessibilityextensionlistsync-f.md)。 |
| [off(辅助功能)](arkts-accessibility-accessibility-off-f.md#offaccessibilitystatechange) | 取消监听辅助应用启用状态变化事件。使用callback异步回调。 |
| [off(辅助功能)](arkts-accessibility-accessibility-off-f.md#offtouchguidestatechange) | 取消监听触摸浏览启用状态变化事件。使用callback异步回调。 |
| [getCaptionsManager(辅助功能)](arkts-accessibility-accessibility-getcaptionsmanager-f.md) | 获取无障碍字幕配置管理实例。 |
| [isScreenReaderOpenSync(辅助功能)](arkts-accessibility-accessibility-isscreenreaderopensync-f.md) | 查询屏幕朗读模式是否开启。 |
| [on(辅助功能)](arkts-accessibility-accessibility-on-f.md#onscreenreaderstatechange) | 监听屏幕朗读模式启用状态变化事件。使用callback异步回调。 |
| [off(辅助功能)](arkts-accessibility-accessibility-off-f.md#offscreenreaderstatechange) | 取消监听屏幕朗读启用状态变化事件。使用callback异步回调。 |
| [on(辅助功能)](arkts-accessibility-accessibility-on-f.md#ontouchmodechange) | 监听触摸浏览功能下的单击/双击操作模式变化事件。使用callback异步回调。 |
| [off(辅助功能)](arkts-accessibility-accessibility-off-f.md#offtouchmodechange) | 取消监听触摸浏览功能下的单击/双击操作模式变化事件。使用callback异步回调。 |
| [getTouchModeSync(辅助功能)](arkts-accessibility-accessibility-gettouchmodesync-f.md) | 查询触摸浏览功能下的单击/双击操作模式，可用于根据当前操作模式调整应用的交互响应方式（如单击模式下直接响应点击、双击模式下需双击确认操作）。 |
| [onAnimationReduceStateChange(辅助功能)](arkts-accessibility-accessibility-onanimationreducestatechange-f.md) | 监听减弱动效模式启用状态变化事件。使用callback异步回调。 |
| [offAnimationReduceStateChange(辅助功能)](arkts-accessibility-accessibility-offanimationreducestatechange-f.md) | 取消监听减弱动效模式变化事件。使用callback异步回调。 |
| [isAnimationReduceEnabledSync(辅助功能)](arkts-accessibility-accessibility-isanimationreduceenabledsync-f.md) | 查询减弱动效模式是否开启。本接口为同步版本，与[accessibility.isAnimationReduceEnabled](arkts-accessibility-accessibility-isanimationreduceenabled-f.md)（异步版本）功能相同，如需立即获取结果 可使用本接口，如需在非阻塞场景下查询建议使用异步版本。 |
| [isAnimationReduceEnabled(辅助功能)](arkts-accessibility-accessibility-isanimationreduceenabled-f.md) | 查询减弱动效模式是否开启。使用Promise异步回调。 |
| [onFlashReminderStateChange(辅助功能)](arkts-accessibility-accessibility-onflashreminderstatechange-f.md) | 监听闪烁提醒模式启用状态变化事件。使用callback异步回调。 |
| [offFlashReminderStateChange(辅助功能)](arkts-accessibility-accessibility-offflashreminderstatechange-f.md) | 取消监听闪烁提醒模式变化事件。使用callback异步回调。 |
| [isFlashReminderEnabledSync(辅助功能)](arkts-accessibility-accessibility-isflashreminderenabledsync-f.md) | 查询闪烁提醒模式是否开启。本接口为同步版本，与[accessibility.isFlashReminderEnabled](arkts-accessibility-accessibility-isflashreminderenabled-f.md)（异步版本）功能相同，如需立即获取结果可使用本 接口，如需在非阻塞场景下查询建议使用异步版本。 |
| [isFlashReminderEnabled(辅助功能)](arkts-accessibility-accessibility-isflashreminderenabled-f.md) | 查询闪烁提醒模式是否开启。使用Promise异步回调。 |
| [onAudioMonoStateChange(辅助功能)](arkts-accessibility-accessibility-onaudiomonostatechange-f.md) | 监听单声道音频模式启用状态变化事件。使用callback异步回调。 |
| [offAudioMonoStateChange(辅助功能)](arkts-accessibility-accessibility-offaudiomonostatechange-f.md) | 取消监听单声道音频模式变化事件。使用callback异步回调。 |
| [isAudioMonoEnabledSync(辅助功能)](arkts-accessibility-accessibility-isaudiomonoenabledsync-f.md) | 查询单声道音频模式是否开启。本接口为同步版本，与[accessibility.isAudioMonoEnabled](arkts-accessibility-accessibility-isaudiomonoenabled-f.md)（异步版本）功能相同，如需立即获取结果可使用本接口，如需在非阻 塞场景下查询建议使用异步版本。 |
| [isAudioMonoEnabled(辅助功能)](arkts-accessibility-accessibility-isaudiomonoenabled-f.md) | 查询单声道音频模式是否开启。使用Promise异步回调。 |
| [onSeniorModeStateChange(辅助功能)](arkts-accessibility-accessibility-onseniormodestatechange-f.md) | 监听系统关怀模式启用状态变化事件。使用callback异步回调。 |
| [offSeniorModeStateChange(辅助功能)](arkts-accessibility-accessibility-offseniormodestatechange-f.md) | 取消监听系统关怀模式变化事件。使用callback异步回调。 |
| [isSeniorModeEnabled(辅助功能)](arkts-accessibility-accessibility-isseniormodeenabled-f.md) | 查询系统关怀模式是否开启。使用Promise异步回调。 |
| [onSeniorModeStateChangeForSelf(辅助功能)](arkts-accessibility-accessibility-onseniormodestatechangeforself-f.md) | 监听应用自身“长辈模式”变化事件。使用callback异步回调。与[accessibility.onSeniorModeStateChange](arkts-accessibility-accessibility-onseniormodestatechange-f.md)（监听系统关怀模式状态变化）对应不同作用范围，本接口仅关注应 用自身状态。 |
| [offSeniorModeStateChangeForSelf(辅助功能)](arkts-accessibility-accessibility-offseniormodestatechangeforself-f.md) | 取消监听应用自身“长辈模式”变化事件。使用callback异步回调。 |
| [getSeniorModeStateForSelf(辅助功能)](arkts-accessibility-accessibility-getseniormodestateforself-f.md) | 判断应用是否开启“长辈模式”。使用Promise异步回调。与[accessibility.isSeniorModeEnabled](arkts-accessibility-accessibility-isseniormodeenabled-f.md)（判断系统关怀模式是否开启）对应不同作用范围，本接口仅查询应用自身状态。 |
| [setSeniorModeStateForSelf(辅助功能)](arkts-accessibility-accessibility-setseniormodestateforself-f.md) | 设置应用是否开启“长辈模式”。使用Promise异步回调。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [EventInfo(辅助功能)](arkts-accessibility-accessibility-eventinfo-c.md) | 无障碍事件信息，用于描述界面变更或交互事件，作为[sendAccessibilityEvent](arkts-accessibility-accessibility-sendaccessibilityevent-f.md)的参数定义事件的类型和触发动作。发送的无障碍事 件将被系统分发到已注册且匹配事件类型的辅助应用进行响应，详见[sendAccessibilityEvent](arkts-accessibility-accessibility-sendaccessibilityevent-f.md)。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CaptionsManager(辅助功能)](arkts-accessibility-accessibility-captionsmanager-i.md) | 字幕配置管理。调用CaptionsManager的方法前，先调用[accessibility.getCaptionsManager()](arkts-accessibility-accessibility-getcaptionsmanager-f.md)获取 CaptionsManager实例。 |
| [CaptionsStyle(辅助功能)](arkts-accessibility-accessibility-captionsstyle-i.md) | 字幕风格。 |
| [AccessibilityAbilityInfo(辅助功能)](arkts-accessibility-accessibility-accessibilityabilityinfo-i.md) | 辅助应用信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityType(辅助功能)](arkts-accessibility-accessibility-abilitytype-t.md) | 无障碍辅助应用类型。 |
| [Action(辅助功能)](arkts-accessibility-accessibility-action-t.md) | 应用所支持的目标动作，需要配置参数的目标动作已在下表各动作的说明列中标明。 |
| [EventType(辅助功能)](arkts-accessibility-accessibility-eventtype-t.md) | 无障碍事件类型。 |
| [WindowUpdateType(辅助功能)](arkts-accessibility-accessibility-windowupdatetype-t.md) | 窗口变化类型。 |
| [AbilityState(辅助功能)](arkts-accessibility-accessibility-abilitystate-t.md) | 辅助应用状态类型。 |
| [Capability(辅助功能)](arkts-accessibility-accessibility-capability-t.md) | 辅助应用能力类型。 |
| [TextMoveUnit(辅助功能)](arkts-accessibility-accessibility-textmoveunit-t.md) | 文本无障碍导航移动粒度。 |
| [CaptionsFontEdgeType(辅助功能)](arkts-accessibility-accessibility-captionsfontedgetype-t.md) | 字幕字体边缘类型。 |
| [CaptionsFontFamily(辅助功能)](arkts-accessibility-accessibility-captionsfontfamily-t.md) | 字幕字体。 |
