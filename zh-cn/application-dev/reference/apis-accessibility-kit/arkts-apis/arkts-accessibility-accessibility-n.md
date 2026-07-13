# accessibility

辅助功能

**起始版本：** 7

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [isOpenAccessibility](arkts-accessibility-isopenaccessibility-f.md#isopenaccessibility-1) | 判断是否启用了辅助应用，使用callback异步回调。 |
| [isOpenAccessibility](arkts-accessibility-isopenaccessibility-f.md#isopenaccessibility-2) | 判断是否启用了辅助应用，使用Promise异步回调。 |
| [isOpenAccessibilitySync](arkts-accessibility-isopenaccessibilitysync-f.md#isopenaccessibilitysync-1) | 查询当前系统内是否存在已开启的辅助应用。如需获取系统内辅助应用信息，推荐使用[accessibility.getAccessibilityExtensionListSync](arkts-accessibility-getaccessibilityextensionlistsync-f.md#getaccessibilityextensionlistsync-1)。 |
| [isOpenTouchGuide](arkts-accessibility-isopentouchguide-f.md#isopentouchguide-1) | 判断触摸浏览模式是否开启，使用callback异步回调。 |
| [isOpenTouchGuide](arkts-accessibility-isopentouchguide-f.md#isopentouchguide-2) | 判断触摸浏览模式是否开启，使用Promise异步回调。 |
| [isOpenTouchGuideSync](arkts-accessibility-isopentouchguidesync-f.md#isopentouchguidesync-1) | 是否开启了触摸浏览模式。 |
| [getAbilityLists](arkts-accessibility-getabilitylists-f.md#getabilitylists-1) | 查询辅助应用列表，使用callback异步回调。 |
| [getAbilityLists](arkts-accessibility-getabilitylists-f.md#getabilitylists-2) | 查询辅助应用列表，使用Promise异步回调。 |
| [getAccessibilityExtensionList](arkts-accessibility-getaccessibilityextensionlist-f.md#getaccessibilityextensionlist-1) | 查询辅助应用列表，使用Promise异步回调。 |
| [getAccessibilityExtensionList](arkts-accessibility-getaccessibilityextensionlist-f.md#getaccessibilityextensionlist-2) | 查询辅助应用列表，使用callback异步回调。 |
| [getAccessibilityExtensionListSync](arkts-accessibility-getaccessibilityextensionlistsync-f.md#getaccessibilityextensionlistsync-1) | 查询当前系统内辅助应用列表，支持按条件查询。 |
| [sendEvent](arkts-accessibility-sendevent-f.md#sendevent-1) | 发送无障碍事件，使用callback异步回调。 |
| [sendEvent](arkts-accessibility-sendevent-f.md#sendevent-2) | 发送无障碍事件，使用Promise异步回调。 |
| [sendAccessibilityEvent](arkts-accessibility-sendaccessibilityevent-f.md#sendaccessibilityevent-1) | 发送无障碍事件，使用callback异步回调。 |
| [sendAccessibilityEvent](arkts-accessibility-sendaccessibilityevent-f.md#sendaccessibilityevent-2) | 发送无障碍事件，使用Promise异步回调。 |
| [on](arkts-accessibility-on-f.md#on-1) | 监听辅助应用启用状态变化事件，使用callback异步回调。如需获取系统内辅助应用信息，推荐使用[accessibility.getAccessibilityExtensionListSync](arkts-accessibility-getaccessibilityextensionlistsync-f.md#getaccessibilityextensionlistsync-1)。@link accessibility.off(type: 'accessibilityStateChange', callback?: Callback&lt;boolean&gt;)}&gt; 取消监听，否则可能会导致崩溃。 |
| [on](arkts-accessibility-on-f.md#on-2) | 监听触摸浏览功能启用状态变化事件，使用callback异步回调。如需获取系统内辅助应用信息，推荐使用[accessibility.getAccessibilityExtensionListSync](arkts-accessibility-getaccessibilityextensionlistsync-f.md#getaccessibilityextensionlistsync-1)。@link accessibility.off(type: 'touchGuideStateChange', callback?: Callback&lt;boolean&gt;)}&gt; 取消监听，否则可能会导致崩溃。 |
| [off](arkts-accessibility-off-f.md#off-1) | 取消监听辅助应用启用状态变化事件，使用callback异步回调。 |
| [off](arkts-accessibility-off-f.md#off-2) | 取消监听触摸浏览启用状态变化事件，使用callback异步回调。 |
| [getCaptionsManager](arkts-accessibility-getcaptionsmanager-f.md#getcaptionsmanager-1) | 获取无障碍字幕配置管理实例。 |
| [isScreenReaderOpenSync](arkts-accessibility-isscreenreaderopensync-f.md#isscreenreaderopensync-1) | 是否开启了屏幕朗读模式。 |
| [on](arkts-accessibility-on-f.md#on-3) | 监听屏幕朗读功能启用状态变化事件，使用callback异步回调。@link accessibility.off(type: 'screenReaderStateChange', callback?: Callback&lt;boolean&gt;)}&gt; 取消监听，否则可能会导致崩溃。 |
| [off](arkts-accessibility-off-f.md#off-3) | 取消监听屏幕朗读启用状态变化事件，使用callback异步回调。 |
| [on](arkts-accessibility-on-f.md#on-4) | 监听触摸浏览功能下的单击/双击操作模式变化事件，使用callback异步回调。@link accessibility.off(type: 'touchModeChange', callback?: Callback&lt;string&gt;)}&gt; 取消监听，否则可能会导致崩溃。 |
| [off](arkts-accessibility-off-f.md#off-4) | 取消监听触摸浏览功能下的单击/双击操作模式变化事件，使用callback异步回调。 |
| [getTouchModeSync](arkts-accessibility-gettouchmodesync-f.md#gettouchmodesync-1) | 查询触摸浏览功能下的单击/双击操作模式。 |
| [onAnimationReduceStateChange](arkts-accessibility-onanimationreducestatechange-f.md#onanimationreducestatechange-1) | 监听减弱动效功能启用状态变化事件。使用callback异步回调。@link accessibility.offAnimationReduceStateChange(callback?: Callback&lt;boolean&gt;)}&gt; 取消监听，否则可能会导致崩溃。 |
| [offAnimationReduceStateChange](arkts-accessibility-offanimationreducestatechange-f.md#offanimationreducestatechange-1) | 取消监听减弱动效模式变化事件。使用callback异步回调。 |
| [isAnimationReduceEnabledSync](arkts-accessibility-isanimationreduceenabledsync-f.md#isanimationreduceenabledsync-1) | 使用同步方法判断减弱动效模式是否开启。 |
| [isAnimationReduceEnabled](arkts-accessibility-isanimationreduceenabled-f.md#isanimationreduceenabled-1) | 判断减弱动效模式是否开启。使用Promise异步回调。 |
| [onFlashReminderStateChange](arkts-accessibility-onflashreminderstatechange-f.md#onflashreminderstatechange-1) | 监听闪烁提醒功能启用状态变化事件。使用callback异步回调。@link accessibility.offFlashReminderStateChange(callback?: Callback&lt;boolean&gt;)}&gt; 取消监听，否则可能会导致崩溃。 |
| [offFlashReminderStateChange](arkts-accessibility-offflashreminderstatechange-f.md#offflashreminderstatechange-1) | 取消监听闪烁提醒模式变化事件。使用callback异步回调。 |
| [isFlashReminderEnabledSync](arkts-accessibility-isflashreminderenabledsync-f.md#isflashreminderenabledsync-1) | 使用同步方法判断闪烁提醒模式是否开启。 |
| [isFlashReminderEnabled](arkts-accessibility-isflashreminderenabled-f.md#isflashreminderenabled-1) | 判断闪烁提醒模式是否开启。使用Promise异步回调。 |
| [onAudioMonoStateChange](arkts-accessibility-onaudiomonostatechange-f.md#onaudiomonostatechange-1) | 监听单声道音频功能启用状态变化事件。使用callback异步回调。@link accessibility.offAudioMonoStateChange(callback?: Callback&lt;boolean&gt;)}&gt; 取消监听，否则可能会导致崩溃。 |
| [offAudioMonoStateChange](arkts-accessibility-offaudiomonostatechange-f.md#offaudiomonostatechange-1) | 取消监听单声道音频模式变化事件。使用callback异步回调。 |
| [isAudioMonoEnabledSync](arkts-accessibility-isaudiomonoenabledsync-f.md#isaudiomonoenabledsync-1) | 使用同步方法判断单声道音频模式是否开启。 |
| [isAudioMonoEnabled](arkts-accessibility-isaudiomonoenabled-f.md#isaudiomonoenabled-1) | 判断单声道音频模式是否开启。使用Promise异步回调。 |
| [onSeniorModeStateChange](arkts-accessibility-onseniormodestatechange-f.md#onseniormodestatechange-1) | 监听关怀模式启用状态变化事件。使用callback异步回调。@link accessibility.offSeniorModeStateChange(callback?: Callback&lt;boolean&gt;)}&gt; 取消监听，否则可能会导致崩溃。 |
| [offSeniorModeStateChange](arkts-accessibility-offseniormodestatechange-f.md#offseniormodestatechange-1) | 取消监听关怀模式变化事件。使用callback异步回调。 |
| [isSeniorModeEnabled](arkts-accessibility-isseniormodeenabled-f.md#isseniormodeenabled-1) | 判断关怀模式是否开启。使用Promise异步回调。 |
| [onSeniorModeStateChangeForSelf](arkts-accessibility-onseniormodestatechangeforself-f.md#onseniormodestatechangeforself-1) | Register an observer for this application's senior mode state changes. |
| [offSeniorModeStateChangeForSelf](arkts-accessibility-offseniormodestatechangeforself-f.md#offseniormodestatechangeforself-1) | Unregister the observer for this application's senior mode state changes. |
| [getSeniorModeStateForSelf](arkts-accessibility-getseniormodestateforself-f.md#getseniormodestateforself-1) | Check if this application's senior mode is enabled. |
| [setSeniorModeStateForSelf](arkts-accessibility-setseniormodestateforself-f.md#setseniormodestateforself-1) | Set this application's senior mode. |

### 类

| 名称 | 说明 |
| --- | --- |
| [EventInfo](arkts-accessibility-eventinfo-c.md) | 界面变更事件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CaptionsManager](arkts-accessibility-captionsmanager-i.md) | 字幕配置管理，在调用CaptionsManager的方法前，需要先通过 [accessibility.getCaptionsManager()](arkts-accessibility-getcaptionsmanager-f.md#getcaptionsmanager-1)获取 CaptionsManager实例。 |
| [CaptionsStyle](arkts-accessibility-captionsstyle-i.md) | 字幕风格。 |
| [AccessibilityAbilityInfo](arkts-accessibility-accessibilityabilityinfo-i.md) | 辅助应用信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityType](arkts-accessibility-abilitytype-t.md) | 无障碍辅助应用类型。 |
| [Action](arkts-accessibility-action-t.md) | 应用所支持的目标动作，需要配置参数的目标动作已在描述中标明。 |
| [EventType](arkts-accessibility-eventtype-t.md) | 无障碍事件类型。 |
| [WindowUpdateType](arkts-accessibility-windowupdatetype-t.md) | 窗口变化类型。 |
| [AbilityState](arkts-accessibility-abilitystate-t.md) | 辅助应用状态类型。 |
| [Capability](arkts-accessibility-capability-t.md) | 辅助应用能力类型。 |
| [TextMoveUnit](arkts-accessibility-textmoveunit-t.md) | 文本无障碍导航移动粒度。 |
| [CaptionsFontEdgeType](arkts-accessibility-captionsfontedgetype-t.md) | 字幕字体边缘类型。 |
| [CaptionsFontFamily](arkts-accessibility-captionsfontfamily-t.md) | 字幕字体。 |

