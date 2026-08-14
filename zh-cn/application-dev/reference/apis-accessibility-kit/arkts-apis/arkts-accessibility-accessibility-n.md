# accessibility

辅助功能

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace accessibility--><!--Device-unnamed-declare namespace accessibility-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [isOpenAccessibility](arkts-accessibility-accessibility-isopenaccessibility-f.md#isOpenAccessibility) | 判断是否启用了辅助应用，使用callback异步回调。 |
| [isOpenAccessibility](arkts-accessibility-accessibility-isopenaccessibility-f.md#isOpenAccessibility) | 判断是否启用了辅助应用，使用Promise异步回调。 |
| [isOpenAccessibilitySync](arkts-accessibility-accessibility-isopenaccessibilitysync-f.md#isOpenAccessibilitySync) | 查询当前系统内是否存在已开启的辅助应用。如需获取系统内辅助应用信息，推荐使用 [accessibility.getAccessibilityExtensionListSync](arkts-accessibility-accessibility-getaccessibilityextensionlistsync-f.md#getAccessibilityExtensionListSync)。 |
| [isOpenTouchGuide](arkts-accessibility-accessibility-isopentouchguide-f.md#isOpenTouchGuide) | 判断触摸浏览模式是否开启，使用callback异步回调。 |
| [isOpenTouchGuide](arkts-accessibility-accessibility-isopentouchguide-f.md#isOpenTouchGuide) | 判断触摸浏览模式是否开启，使用Promise异步回调。 |
| [isOpenTouchGuideSync](arkts-accessibility-accessibility-isopentouchguidesync-f.md#isOpenTouchGuideSync) | 是否开启了触摸浏览模式。 |
| [getAbilityLists](arkts-accessibility-accessibility-getabilitylists-f.md#getAbilityLists) | 查询辅助应用列表，使用callback异步回调。 |
| [getAbilityLists](arkts-accessibility-accessibility-getabilitylists-f.md#getAbilityLists) | 查询辅助应用列表，使用Promise异步回调。 |
| [getAccessibilityExtensionList](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md#getAccessibilityExtensionList) | 查询辅助应用列表，使用Promise异步回调。 |
| [getAccessibilityExtensionList](arkts-accessibility-accessibility-getaccessibilityextensionlist-f.md#getAccessibilityExtensionList) | 查询辅助应用列表，使用callback异步回调。 |
| [getAccessibilityExtensionListSync](arkts-accessibility-accessibility-getaccessibilityextensionlistsync-f.md#getAccessibilityExtensionListSync) | 查询当前系统内辅助应用列表，支持按条件查询。 |
| [sendEvent](arkts-accessibility-accessibility-sendevent-f.md#sendEvent) | 发送无障碍事件，使用callback异步回调。 |
| [sendEvent](arkts-accessibility-accessibility-sendevent-f.md#sendEvent) | 发送无障碍事件，使用Promise异步回调。 |
| [sendAccessibilityEvent](arkts-accessibility-accessibility-sendaccessibilityevent-f.md#sendAccessibilityEvent) | 发送无障碍事件，使用callback异步回调。 |
| [sendAccessibilityEvent](arkts-accessibility-accessibility-sendaccessibilityevent-f.md#sendAccessibilityEvent) | 发送无障碍事件，使用Promise异步回调。 |
| on_accessibilityStateChange | 监听辅助应用启用状态变化事件，使用callback异步回调。如需获取系统内辅助应用信息，推荐使用 [accessibility.getAccessibilityExtensionListSync](arkts-accessibility-accessibility-getaccessibilityextensionlistsync-f.md#getAccessibilityExtensionListSync)。 |
| [onAccessibilityStateChange](arkts-accessibility-accessibility-onaccessibilitystatechange-f.md#onAccessibilityStateChange) | Register the observe of the accessibility state changed. |
| on_touchGuideStateChange | 监听触摸浏览功能启用状态变化事件，使用callback异步回调。如需获取系统内辅助应用信息，推荐使用 [accessibility.getAccessibilityExtensionListSync](arkts-accessibility-accessibility-getaccessibilityextensionlistsync-f.md#getAccessibilityExtensionListSync)。 |
| [onTouchGuideStateChange](arkts-accessibility-accessibility-ontouchguidestatechange-f.md#onTouchGuideStateChange) | Register the observe of the touchGuide state changed. |
| off_accessibilityStateChange | 取消监听辅助应用启用状态变化事件，使用callback异步回调。 |
| [offAccessibilityStateChange](arkts-accessibility-accessibility-offaccessibilitystatechange-f.md#offAccessibilityStateChange) | Unregister the observe of the accessibility state changed. |
| off_touchGuideStateChange | 取消监听触摸浏览启用状态变化事件，使用callback异步回调。 |
| [offTouchGuideStateChange](arkts-accessibility-accessibility-offtouchguidestatechange-f.md#offTouchGuideStateChange) | Unregister the observe of the touchGuide state changed. |
| [getCaptionsManager](arkts-accessibility-accessibility-getcaptionsmanager-f.md#getCaptionsManager) | 获取无障碍字幕配置管理实例。 |
| [isScreenReaderOpenSync](arkts-accessibility-accessibility-isscreenreaderopensync-f.md#isScreenReaderOpenSync) | 是否开启了屏幕朗读模式。 |
| on_screenReaderStateChange | 监听屏幕朗读功能启用状态变化事件，使用callback异步回调。 |
| [onScreenReaderStateChange](arkts-accessibility-accessibility-onscreenreaderstatechange-f.md#onScreenReaderStateChange) | Register the observe of the screen reader state changed. |
| off_screenReaderStateChange | 取消监听屏幕朗读启用状态变化事件，使用callback异步回调。 |
| [offScreenReaderStateChange](arkts-accessibility-accessibility-offscreenreaderstatechange-f.md#offScreenReaderStateChange) | Unregister the observe of the screen reader state changed. |
| on_touchModeChange | 监听触摸浏览功能下的单击/双击操作模式变化事件，使用callback异步回调。 |
| [onTouchModeChange](arkts-accessibility-accessibility-ontouchmodechange-f.md#onTouchModeChange) | Register the observe of the touch mode changed. |
| off_touchModeChange | 取消监听触摸浏览功能下的单击/双击操作模式变化事件，使用callback异步回调。 |
| [offTouchModeChange](arkts-accessibility-accessibility-offtouchmodechange-f.md#offTouchModeChange) | Unregister the observe of the touch mode changed. |
| [getTouchModeSync](arkts-accessibility-accessibility-gettouchmodesync-f.md#getTouchModeSync) | 查询触摸浏览功能下的单击/双击操作模式。 |
| [onAnimationReduceStateChange](arkts-accessibility-accessibility-onanimationreducestatechange-f.md#onAnimationReduceStateChange) | 监听减弱动效功能启用状态变化事件。使用callback异步回调。 |
| [offAnimationReduceStateChange](arkts-accessibility-accessibility-offanimationreducestatechange-f.md#offAnimationReduceStateChange) | 取消监听减弱动效模式变化事件。使用callback异步回调。 |
| [isAnimationReduceEnabledSync](arkts-accessibility-accessibility-isanimationreduceenabledsync-f.md#isAnimationReduceEnabledSync) | 使用同步方法判断减弱动效模式是否开启。 |
| [isAnimationReduceEnabled](arkts-accessibility-accessibility-isanimationreduceenabled-f.md#isAnimationReduceEnabled) | 判断减弱动效模式是否开启。使用Promise异步回调。 |
| [onFlashReminderStateChange](arkts-accessibility-accessibility-onflashreminderstatechange-f.md#onFlashReminderStateChange) | 监听闪烁提醒功能启用状态变化事件。使用callback异步回调。 |
| [offFlashReminderStateChange](arkts-accessibility-accessibility-offflashreminderstatechange-f.md#offFlashReminderStateChange) | 取消监听闪烁提醒模式变化事件。使用callback异步回调。 |
| [isFlashReminderEnabledSync](arkts-accessibility-accessibility-isflashreminderenabledsync-f.md#isFlashReminderEnabledSync) | 使用同步方法判断闪烁提醒模式是否开启。 |
| [isFlashReminderEnabled](arkts-accessibility-accessibility-isflashreminderenabled-f.md#isFlashReminderEnabled) | 判断闪烁提醒模式是否开启。使用Promise异步回调。 |
| [onAudioMonoStateChange](arkts-accessibility-accessibility-onaudiomonostatechange-f.md#onAudioMonoStateChange) | 监听单声道音频功能启用状态变化事件。使用callback异步回调。 |
| [offAudioMonoStateChange](arkts-accessibility-accessibility-offaudiomonostatechange-f.md#offAudioMonoStateChange) | 取消监听单声道音频模式变化事件。使用callback异步回调。 |
| [isAudioMonoEnabledSync](arkts-accessibility-accessibility-isaudiomonoenabledsync-f.md#isAudioMonoEnabledSync) | 使用同步方法判断单声道音频模式是否开启。 |
| [isAudioMonoEnabled](arkts-accessibility-accessibility-isaudiomonoenabled-f.md#isAudioMonoEnabled) | 判断单声道音频模式是否开启。使用Promise异步回调。 |
| [onSeniorModeStateChange](arkts-accessibility-accessibility-onseniormodestatechange-f.md#onSeniorModeStateChange) | 监听关怀模式启用状态变化事件。使用callback异步回调。 |
| [offSeniorModeStateChange](arkts-accessibility-accessibility-offseniormodestatechange-f.md#offSeniorModeStateChange) | 取消监听关怀模式变化事件。使用callback异步回调。 |
| [isSeniorModeEnabled](arkts-accessibility-accessibility-isseniormodeenabled-f.md#isSeniorModeEnabled) | 判断关怀模式是否开启。使用Promise异步回调。 |
| [onSeniorModeStateChangeForSelf](arkts-accessibility-accessibility-onseniormodestatechangeforself-f.md#onSeniorModeStateChangeForSelf) | Register an observer for this application's senior mode state changes. |
| [offSeniorModeStateChangeForSelf](arkts-accessibility-accessibility-offseniormodestatechangeforself-f.md#offSeniorModeStateChangeForSelf) | Unregister the observer for this application's senior mode state changes. |
| [getSeniorModeStateForSelf](arkts-accessibility-accessibility-getseniormodestateforself-f.md#getSeniorModeStateForSelf) | Check if this application's senior mode is enabled. |
| [setSeniorModeStateForSelf](arkts-accessibility-accessibility-setseniormodestateforself-f.md#setSeniorModeStateForSelf) | Set this application's senior mode. |

### 类

| 名称 | 说明 |
| --- | --- |
| [EventInfo](arkts-accessibility-accessibility-eventinfo-c.md) | 界面变更事件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CaptionsManager](arkts-accessibility-accessibility-captionsmanager-i.md) | 字幕配置管理，在调用CaptionsManager的方法前，需要先通过 [accessibility.getCaptionsManager()](arkts-accessibility-accessibility-getcaptionsmanager-f.md#getCaptionsManager)获取 CaptionsManager实例。 |
| [CaptionsStyle](arkts-accessibility-accessibility-captionsstyle-i.md) | 字幕风格。 |
| [AccessibilityAbilityInfo](arkts-accessibility-accessibility-accessibilityabilityinfo-i.md) | 辅助应用信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityType](arkts-accessibility-accessibility-abilitytype-t.md) | 无障碍辅助应用类型。 |
| [Action](arkts-accessibility-accessibility-action-t.md) | 应用所支持的目标动作，需要配置参数的目标动作已在描述中标明。 |
| [EventType](arkts-accessibility-accessibility-eventtype-t.md) | 无障碍事件类型。 |
| [WindowUpdateType](arkts-accessibility-accessibility-windowupdatetype-t.md) | 窗口变化类型。 |
| [AbilityState](arkts-accessibility-accessibility-abilitystate-t.md) | 辅助应用状态类型。 |
| [Capability](arkts-accessibility-accessibility-capability-t.md) | 辅助应用能力类型。 |
| [TextMoveUnit](arkts-accessibility-accessibility-textmoveunit-t.md) | 文本无障碍导航移动粒度。 |
| [CaptionsFontEdgeType](arkts-accessibility-accessibility-captionsfontedgetype-t.md) | 字幕字体边缘类型。 |
| [CaptionsFontFamily](arkts-accessibility-accessibility-captionsfontfamily-t.md) | 字幕字体。 |

