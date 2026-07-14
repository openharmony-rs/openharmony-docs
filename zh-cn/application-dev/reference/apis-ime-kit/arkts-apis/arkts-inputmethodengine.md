# @ohos.inputMethodEngine

**@ohos.inputMethodEngine**模块是面向输入法应用（包括系统输入法和第三方输入法）的服务端API模块，提供了输入法应用与系统输入法框架之间的交互能力。

本模块是输入法应用的服务端接口，定义了输入法应用在运行期间所需的全部开放能力，包括输入法生命周期管理、软键盘面板的创建与控制、文本编辑操作（插入、删除、选中文本）、光标控制、物理键盘事件监听、安全模式管理、私有数据通信等。

输入法应用通过本模块可以：1）订阅输入法绑定/解绑事件，感知编辑框的连接与断开；2）创建和管理软键盘面板（固定态、悬浮态、候选态）及状态栏面板，控制面板的显示、隐藏、大小调整、位置移动、沉浸模式等；3）通过InputClient对编辑
框进行文本插入、删除、选中文本、移动光标、发送功能键和扩展编辑动作等操作；4）通过KeyboardDelegate监听物理键盘按键事件、光标位置变化、文本选择变化、文本内容变化、编辑框属性变化等；5）管理安全模式（基础模式/完全访问模
式），支持隐私面板设置；6）与编辑框应用进行私有数据通信和自定义消息通信。

当开发输入法应用时使用本模块。本模块需在InputMethodExtensionAbility中使用，适用于系统输入法开发、第三方输入法开发、自定义键盘布局等场景。

本模块的核心开放能力由以下关键Interface承载：

| Interface/Class | 说明 |
|---|---|
| **InputMethodAbility** | 输入法能力对象，是输入法应用的核心入口。提供输入法生命周期事件订阅（绑定/解绑/键盘显示隐藏/子类型切换/安全模式变化等）、面板创建与销毁、安全模式获取等能力。通过`getInputMethodAbility()`获取实例。 |
| **KeyboardDelegate** | 键盘代理对象，提供物理键盘按键事件监听、光标位置变化监听、文本选择变化监听、文本内容变化监听、编辑框属性变化监听等能力。通过`getKeyboardDelegate()`获取实例。 |
| **InputClient** | 输入客户端对象，提供对编辑框的文本操作能力，包括插入文本、删除文本（前删/后删）、获取光标前后文本、移动光标、选中文本、发送功能键和扩展编辑动作、设置预览文本、发送私有数据、自定义消息通信等。通过订阅`inputStart`事件在回调中获取实例。 |
| **KeyboardController** | 键盘控制器对象，提供隐藏键盘、退出当前输入类型等能力。通过订阅`inputStart`事件在回调中获取实例。 |
| **Panel** | 输入法面板对象，提供面板页面内容加载、大小调整、位置移动、显示/隐藏、面板状态切换、隐私模式设置、沉浸模式与效果设置、面板矩形区域预设置、热区更新等能力。通过`createPanel()`获取实例。 |
| **MessageHandler** | 自定义通信对象，用于接收编辑框应用发送的自定义通信数据，并提供终止通知回调。通过`InputClient.recvMessage()`注册。 |

输入法应用的典型使用流程涉及多个API的组合调用，核心流程为：获取InputMethodAbility实例 -> 订阅inputStart事件 -> 在回调中获取KeyboardController和InputClient -> 创建
Panel -> 加载面板页面内容 -> 通过InputClient操作编辑框文本 -> 通过KeyboardController控制键盘显隐。

**起始版本：** 8

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createKeyboardDelegate](arkts-ime-createkeyboarddelegate-f.md#createkeyboarddelegate-1) | 获取客户端编辑事件监听代理实例[KeyboardDelegate](arkts-ime-keyboarddelegate-i.md)。输入法应用获取该实例后，可订阅物理键盘按键事件、选中文本变化事件等。 |
| [getInputMethodAbility](arkts-ime-getinputmethodability-f.md#getinputmethodability-1) | 获取输入法应用客户端实例[InputMethodAbility](arkts-ime-inputmethodability-i.md)（输入法能力对象），仅支持输入法应用调用。输入法应用获取该实例后，可订阅软键盘显示/隐藏请求事件、创建/销毁输入法面板等。 |
| [getInputMethodEngine](arkts-ime-getinputmethodengine-f.md#getinputmethodengine-1) | 获取输入法应用客户端实例[InputMethodEngine](arkts-ime-inputmethodengine-i.md)（输入法引擎）。输入法应用获取该实例后，可订阅软键盘显示/隐藏请求事件等。 |
| [getKeyboardDelegate](arkts-ime-getkeyboarddelegate-f.md#getkeyboarddelegate-1) | 获取客户端编辑事件监听代理实例[KeyboardDelegate](arkts-ime-keyboarddelegate-i.md)（键盘代理对象）。输入法应用获取该实例后，可订阅物理键盘按键事件、选中文本变化事件等。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AttachOptions](arkts-ime-attachoptions-i.md) | 绑定输入法时的附加选项。 |
| [EditorAttribute](arkts-ime-editorattribute-i.md) | 编辑框属性值。 |
| [EnhancedPanelRect](arkts-ime-enhancedpanelrect-i.md) | 增强的输入法面板位置、大小信息，包含自定义避让区域、自定义热区。 |
| [ImmersiveEffect](arkts-ime-immersiveeffect-i.md) | 沉浸效果。 |
| [InputClient](arkts-ime-inputclient-i.md) | InputClient是输入法客户端对象，代表当前绑定到输入法应用的编辑框客户端。InputClient实例通过InputMethodAbility的[on('inputStart')](arkts-ime-inputmethodability-i.md#on-1)事件回调获取，每个绑定事件对应一个InputClient实例，输入法应用通过该实例与编辑框进行文本交互。**核心功能概述：**- **文本获取**：通过[getForward](arkts-ime-inputclient-i.md#getforward-1)/[getForwardSync](arkts-ime-inputclient-i.md#getforwardsync-1)获取光标前的文本，通过[getBackward](arkts-ime-inputclient-i.md#getbackward-1)/[getBackwardSync](arkts-ime-inputclient-i.md#getbackwardsync-1)获取光标后的文本，用于分析已输入内容并提供智能补全。- **文本编辑**：通过[insertText](arkts-ime-inputclient-i.md#inserttext-1)/[insertTextSync](arkts-ime-inputclient-i.md#inserttextsync-1)插入文本，通过[deleteForward](arkts-ime-inputclient-i.md#deleteforward-1)/[deleteForwardSync](arkts-ime-inputclient-i.md#deleteforwardsync-1)删除光标前的文本，通过[deleteBackward](arkts-ime-inputclient-i.md#deletebackward-1)/[deleteBackwardSync](arkts-ime-inputclient-i.md#deletebackwardsync-1)删除光标后的文本。- **功能键与光标**：通过[sendKeyFunction](arkts-ime-inputclient-i.md#sendkeyfunction-1)发送功能键（如回车键），通过[moveCursor](arkts-ime-inputclient-i.md#movecursor-1)/[moveCursorSync](arkts-ime-inputclient-i.md#movecursorsync-1)移动光标。- **选区操作**：通过[selectByRange](arkts-ime-inputclient-i.md#selectbyrange-1)/[selectByRangeSync](arkts-ime-inputclient-i.md#selectbyrangesync-1)按范围选中文本，通过[selectByMovement](arkts-ime-inputclient-i.md#selectbymovement-1)/[selectByMovementSync](arkts-ime-inputclient-i.md#selectbymovementsync-1)按方向选中文本。- **编辑框属性**：通过[getEditorAttribute](arkts-ime-inputclient-i.md#geteditorattribute-1)/[getEditorAttributeSync](arkts-ime-inputclient-i.md#geteditorattributesync-1)获取编辑框属性信息（输入类型、回车键类型等），据此调整键盘布局。- **文本预览**：通过[setPreviewText](arkts-ime-inputclient-i.md#setpreviewtext-1)/[setPreviewTextSync](arkts-ime-inputclient-i.md#setpreviewtextsync-1)设置预览文本，通过[finishTextPreview](arkts-ime-inputclient-i.md#finishtextpreview-1)/[finishTextPreviewSync](arkts-ime-inputclient-i.md#finishtextpreviewsync-1)结束文本预览。- **私有通信**：通过[sendPrivateCommand](arkts-ime-inputclient-i.md#sendprivatecommand-1)向应用发送私有命令，通过[sendMessage](arkts-ime-inputclient-i.md#sendmessage-1)/[recvMessage](arkts-ime-inputclient-i.md#recvmessage-1)进行消息通信。下列API均需使用[on('inputStart')](arkts-ime-inputmethodability-i.md#on-1)获取到InputClient实例后，通过实例调用。 |
| [InputMethodAbility](arkts-ime-inputmethodability-i.md) | InputMethodAbility是输入法应用的核心能力对象，提供输入法生命周期管理、面板创建与销毁、事件订阅等功能。输入法应用通过[getInputMethodAbility](arkts-ime-getinputmethodability-f.md#getinputmethodability-1)获取该实例。下列API均需使用[getInputMethodAbility](arkts-ime-getinputmethodability-f.md#getinputmethodability-1)获取到InputMethodAbility实例后，通过实例调用。 |
| [InputMethodEngine](arkts-ime-inputmethodengine-i.md) | 下列API均需使用[getInputMethodEngine](arkts-ime-getinputmethodengine-f.md#getinputmethodengine-1)获取到InputMethodEngine实例后，通过实例调用。 |
| [KeyEvent](arkts-ime-keyevent-i.md) | 按键属性值。 |
| [KeyboardArea](arkts-ime-keyboardarea-i.md) | 面板中的键盘区域。 |
| [KeyboardController](arkts-ime-keyboardcontroller-i.md) | 下列API均需使用[on('inputStart')](arkts-ime-inputmethodability-i.md#on-1)获取到KeyboardController实例后，通过实例调用。 |
| [KeyboardDelegate](arkts-ime-keyboarddelegate-i.md) | KeyboardDelegate是键盘事件监听代理对象，用于输入法应用监听物理键盘按键事件和编辑框文本/光标/选区变化事件。输入法应用通过[getKeyboardDelegate](arkts-ime-getkeyboarddelegate-f.md#getkeyboarddelegate-1)获取该实例。**核心功能概述：**- **物理键盘按键事件**：通过on('keyDown'\|'keyUp')订阅物理按键的按下/抬起事件，通过on('keyEvent')订阅更完整的按键事件（含组合键信息）。callback返回true表示按键事件被消费，返回false表示不消费。- **光标与选区变化事件**：通过on('cursorContextChange')订阅光标位置变化事件，通过on('selectionChange')订阅文本选区变化事件。输入法应用可根据这些事件调整候选词位置或输入策略。- **文本变化事件**：通过on('textChange')订阅编辑框文本内容变化事件，输入法应用可据此更新候选词或输入建议。- **编辑框属性变化事件**：通过on('editorAttributeChanged')订阅编辑框属性变化事件，输入法应用可根据编辑框属性变化动态调整键盘布局。**使用场景：**- 开发物理键盘快捷键处理功能时，订阅on('keyDown'\|'keyUp')或on('keyEvent')事件拦截特定按键。- 需要根据编辑框实时状态（光标、选区、文本、属性）调整输入法行为时，订阅对应的on事件。下列API均需使用[getKeyboardDelegate](arkts-ime-getkeyboarddelegate-f.md#getkeyboarddelegate-1)获取到KeyboardDelegate实例后，通过实例调用。 |
| [MessageHandler](arkts-ime-messagehandler-i.md) | 自定义通信对象。 |
| [Movement](arkts-ime-movement-i.md) | 选中文本时，光标移动的方向 |
| [Panel](arkts-ime-panel-i.md) | Panel是输入法面板对象，提供面板页面加载、显示/隐藏、尺寸调整、位置移动、模式切换等功能。Panel实例通过InputMethodAbility的[createPanel](arkts-ime-inputmethodability-i.md#createpanel-1)接口获取，使用完毕后需调用[destroyPanel](arkts-ime-inputmethodability-i.md#destroypanel-1)销毁以释放资源。createPanel与destroyPanel必须配对调用。**核心功能概述：**- **页面加载**：通过[setUiContent](arkts-ime-panel-i.md#setuicontent-1)为面板加载键盘页面内容，支持加载普通页面和与LocalStorage关联的页面。- **显示与隐藏**：通过[show](arkts-ime-panel-i.md#show-1)显示面板，通过[hide](arkts-ime-panel-i.md#hide-1)隐藏面板。面板的显示/隐藏也可通过订阅on('show')/on('hide')事件监听状态变化。- **尺寸与位置调整**：通过[resize](arkts-ime-panel-i.md#resize-1)调整面板尺寸，通过[moveTo](arkts-ime-panel-i.md#moveto-1)移动面板位置，通过[startMoving](arkts-ime-panel-i.md#startmoving-1)拖拽移动面板，通过[adjustPanelRect](arkts-ime-panel-i.md#adjustpanelrect-1)/[updatePanelRect](arkts-ime-panel-i.md#updatepanelrect-1)/[updateRegion](arkts-ime-panel-i.md#updateregion-1)调整面板区域。- **模式设置**：通过[changeFlag](arkts-ime-panel-i.md#changeflag-1)切换面板固定态/浮动态，通过[setPrivacyMode](arkts-ime-panel-i.md#setprivacymode-1)设置隐私模式，通过[setImmersiveMode](arkts-ime-panel-i.md#setimmersivemode-1)/[getImmersiveMode](arkts-ime-panel-i.md#getimmersivemode-1)设置/获取沉浸模式。- **事件监听**：通过on('show')/on('hide')/on('sizeChange')监听面板状态变化事件。**面板生命周期：**1. 在InputMethodAbility的[createPanel](arkts-ime-inputmethodability-i.md#createpanel-1)中创建Panel实例并指定面板类型和标志位。2. 调用[setUiContent](arkts-ime-panel-i.md#setuicontent-1)加载键盘页面内容。3. 调用[show](arkts-ime-panel-i.md#show-1)显示面板，用户可交互。4. 根据需要调用resize、moveTo、changeFlag等接口动态调整面板。5. 使用完毕后调用[destroyPanel](arkts-ime-inputmethodability-i.md#destroypanel-1)销毁面板，释放资源。下列API均需使用[createPanel](arkts-ime-inputmethodability-i.md#createpanel-1)获取到Panel实例后，通过实例调用。 |
| [PanelInfo](arkts-ime-panelinfo-i.md) | 输入法面板属性。 |
| [PanelRect](arkts-ime-panelrect-i.md) | 输入法面板位置大小信息。 |
| [Range](arkts-ime-range-i.md) | 选中的文本范围。 |
| [TextInputClient](arkts-ime-textinputclient-i.md) | 下列API示例中都需使用[on('inputStart')](arkts-ime-inputmethodengine-i.md#on-1)回调获取到TextInputClient实例，再通过此实例调用对应方法。 |
| [WindowInfo](arkts-ime-windowinfo-i.md) | 窗口信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EditorAttribute](arkts-ime-editorattribute-i-sys.md) | 编辑框属性值。 |
| [ImmersiveEffect](arkts-ime-immersiveeffect-i-sys.md) | 沉浸效果。 |
| [Panel](arkts-ime-panel-i-sys.md) | Panel是输入法面板对象，提供面板页面加载、显示/隐藏、尺寸调整、位置移动、模式切换等功能。Panel实例通过InputMethodAbility的[createPanel](arkts-ime-inputmethodability-i.md#createpanel-1)接口获取，使用完毕后需调用[destroyPanel](arkts-ime-inputmethodability-i.md#destroypanel-1)销毁以释放资源。createPanel与destroyPanel必须配对调用。**核心功能概述：**- **页面加载**：通过[setUiContent](arkts-ime-panel-i.md#setuicontent-1)为面板加载键盘页面内容，支持加载普通页面和与LocalStorage关联的页面。- **显示与隐藏**：通过[show](arkts-ime-panel-i.md#show-1)显示面板，通过[hide](arkts-ime-panel-i.md#hide-1)隐藏面板。面板的显示/隐藏也可通过订阅on('show')/on('hide')事件监听状态变化。- **尺寸与位置调整**：通过[resize](arkts-ime-panel-i.md#resize-1)调整面板尺寸，通过[moveTo](arkts-ime-panel-i.md#moveto-1)移动面板位置，通过[startMoving](arkts-ime-panel-i.md#startmoving-1)拖拽移动面板，通过[adjustPanelRect](arkts-ime-panel-i.md#adjustpanelrect-1)/[updatePanelRect](arkts-ime-panel-i.md#updatepanelrect-1)/[updateRegion](arkts-ime-panel-i.md#updateregion-1)调整面板区域。- **模式设置**：通过[changeFlag](arkts-ime-panel-i.md#changeflag-1)切换面板固定态/浮动态，通过[setPrivacyMode](arkts-ime-panel-i.md#setprivacymode-1)设置隐私模式，通过[setImmersiveMode](arkts-ime-panel-i.md#setimmersivemode-1)/[getImmersiveMode](arkts-ime-panel-i.md#getimmersivemode-1)设置/获取沉浸模式。- **事件监听**：通过on('show')/on('hide')/on('sizeChange')监听面板状态变化事件。**面板生命周期：**1. 在InputMethodAbility的[createPanel](arkts-ime-inputmethodability-i.md#createpanel-1)中创建Panel实例并指定面板类型和标志位。2. 调用[setUiContent](arkts-ime-panel-i.md#setuicontent-1)加载键盘页面内容。3. 调用[show](arkts-ime-panel-i.md#show-1)显示面板，用户可交互。4. 根据需要调用resize、moveTo、changeFlag等接口动态调整面板。5. 使用完毕后调用[destroyPanel](arkts-ime-inputmethodability-i.md#destroypanel-1)销毁面板，释放资源。下列API均需使用[createPanel](arkts-ime-inputmethodability-i.md#createpanel-1)获取到Panel实例后，通过实例调用。 |
| [SystemPanelInsets](arkts-ime-systempanelinsets-i.md) | 输入法软键盘相对系统面板的偏移区域。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CapitalizeMode](arkts-ime-capitalizemode-e.md) | 枚举，定义了文本首字母大写的不同模式。\| 名称 \| 值 \| 说明 \|\| -------- \| -- \| -------- \|\| NONE \| 0 \| 不进行任何首字母大写处理。\|\| SENTENCES \| 1 \| 每个句子的首字母大写。\|\| WORDS \| 2 \| 每个单词的首字母大写。\|\| CHARACTERS \| 3 \| 每个字母都大写。\| |
| [Direction](arkts-ime-direction-e.md) | 光标的移动方向。 |
| [ExtendAction](arkts-ime-extendaction-e.md) | 编辑框中文本的扩展编辑操作类型，如剪切、复制等。 |
| [GradientMode](arkts-ime-gradientmode-e.md) | 枚举，输入法渐变模式。\| 名称 \| 值 \| 说明 \|\| ------------ \| -- \| ------------------ \|\| NONE \| 0 \| 不使用渐变模式。 \|\| LINEAR_GRADIENT \| 1 \| 线性渐变。 \| |
| [ImmersiveMode](arkts-ime-immersivemode-e.md) | 枚举，输入法沉浸模式。\| 名称 \| 值 \| 说明 \|\| ------------ \| -- \| ------------------ \|\| NONE_IMMERSIVE \| 0 \| 不使用沉浸模式。 \|\| IMMERSIVE \| 1 \| 沉浸模式，由输入法应用确定沉浸模式类型。 \|\| LIGHT_IMMERSIVE \| 2 \| 浅色沉浸模式。 \|\| DARK_IMMERSIVE \| 3 \| 深色沉浸模式。 \| |
| [PanelFlag](arkts-ime-panelflag-e.md) | 输入法面板状态类型枚举。\| 名称 \| 值 \| 说明 \|\| ------------ \| -- \| ------------------ \|\| FLG_FIXED \| 0 \| 固定态面板类型。 \|\| FLG_FLOATING \| 1 \| 悬浮态面板类型。 \|\| FLAG_CANDIDATE&lt;sup&gt;15+&lt;/sup&gt; \| 2 \| 候选词态面板类型。 \| |
| [PanelType](arkts-ime-paneltype-e.md) | 输入法面板类型枚举。\| 名称 \| 值 \| 说明 \|\| ------------ \| -- \| ------------------ \|\| SOFT_KEYBOARD \| 0 \| 软键盘类型。 \|\| STATUS_BAR \| 1 \| 状态栏类型。 \| |
| [RequestKeyboardReason](arkts-ime-requestkeyboardreason-e.md) | 枚举，请求键盘输入的原因。\| 名称 \| 值 \| 说明 \|\| ------------ \| -- \| ------------------ \|\| NONE \| 0 \| 表示没有特定的原因触发键盘请求。 \|\| MOUSE \| 1 \| 表示键盘请求是由鼠标操作触发的。 \|\| TOUCH \| 2 \| 表示键盘请求是由触摸操作触发的。 \|\| OTHER \| 20 \| 表示键盘请求是由其他原因触发的。 \| |
| [SecurityMode](arkts-ime-securitymode-e.md) | 输入法的安全模式，如BASIC或FULL。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FluidLightMode](arkts-ime-fluidlightmode-e-sys.md) | 枚举，输入法流光模式。\| 名称 \| 值 \| 说明 \|\| ------------ \| -- \| ------------------ \|\| NONE \| 0 \| 不使用流光模式。 \|\| BACKGROUND_FLUID_LIGHT \| 1 \| 开启背景流光模式。系统面板变为透明，流光效果由编辑框宿主应用实现。 \| |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [CommandDataType](arkts-ime-commanddatatype-t.md) | 表示私有数据类型，接口参数具体类型根据其功能而定。 |
| [SizeChangeCallback](arkts-ime-sizechangecallback-t.md) | 当输入法面板大小变化时触发的回调。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SizeUpdateCallback](arkts-ime-sizeupdatecallback-t-sys.md) | 当输入法面板大小变化时触发的回调。 |
<!--DelEnd-->

### 常量

| 名称 | 说明 |
| --- | --- |
| [CURSOR_DOWN](arkts-ime-inputmethodengine-con.md#cursor_down) | 光标下移。 |
| [CURSOR_LEFT](arkts-ime-inputmethodengine-con.md#cursor_left) | 光标左移。 |
| [CURSOR_RIGHT](arkts-ime-inputmethodengine-con.md#cursor_right) | 光标右移。 |
| [CURSOR_UP](arkts-ime-inputmethodengine-con.md#cursor_up) | 光标上移。 |
| [DISPLAY_MODE_FULL](arkts-ime-inputmethodengine-con.md#display_mode_full) | 编辑框显示为全屏。 |
| [DISPLAY_MODE_PART](arkts-ime-inputmethodengine-con.md#display_mode_part) | 编辑框显示为半屏。 |
| [ENTER_KEY_TYPE_DONE](arkts-ime-inputmethodengine-con.md#enter_key_type_done) | “回车”功能键。 |
| [ENTER_KEY_TYPE_GO](arkts-ime-inputmethodengine-con.md#enter_key_type_go) | “前往”功能键。 |
| [ENTER_KEY_TYPE_NEWLINE](arkts-ime-inputmethodengine-con.md#enter_key_type_newline) | “换行”功能键。 |
| [ENTER_KEY_TYPE_NEXT](arkts-ime-inputmethodengine-con.md#enter_key_type_next) | “下一个”功能键。 |
| [ENTER_KEY_TYPE_PREVIOUS](arkts-ime-inputmethodengine-con.md#enter_key_type_previous) | “前一个”功能键。 |
| [ENTER_KEY_TYPE_SEARCH](arkts-ime-inputmethodengine-con.md#enter_key_type_search) | “搜索”功能键。 |
| [ENTER_KEY_TYPE_SEND](arkts-ime-inputmethodengine-con.md#enter_key_type_send) | “发送”功能键。 |
| [ENTER_KEY_TYPE_UNSPECIFIED](arkts-ime-inputmethodengine-con.md#enter_key_type_unspecified) | 无功能键。 |
| [FLAG_SELECTING](arkts-ime-inputmethodengine-con.md#flag_selecting) | 编辑框处于选择状态。 |
| [FLAG_SINGLE_LINE](arkts-ime-inputmethodengine-con.md#flag_single_line) | 编辑框为单行。 |
| [OPTION_ASCII](arkts-ime-inputmethodengine-con.md#option_ascii) | 允许输入ASCII值。 |
| [OPTION_AUTO_CAP_CHARACTERS](arkts-ime-inputmethodengine-con.md#option_auto_cap_characters) | 允许输入字符。 |
| [OPTION_AUTO_CAP_SENTENCES](arkts-ime-inputmethodengine-con.md#option_auto_cap_sentences) | 允许输入句子。 |
| [OPTION_AUTO_WORDS](arkts-ime-inputmethodengine-con.md#option_auto_words) | 允许输入单词。 |
| [OPTION_MULTI_LINE](arkts-ime-inputmethodengine-con.md#option_multi_line) | 允许输入多行。 |
| [OPTION_NONE](arkts-ime-inputmethodengine-con.md#option_none) | 不指定编辑框输入属性。 |
| [OPTION_NO_FULLSCREEN](arkts-ime-inputmethodengine-con.md#option_no_fullscreen) | 半屏样式。 |
| [PATTERN_DATETIME](arkts-ime-inputmethodengine-con.md#pattern_datetime) | 日期编辑框。 |
| [PATTERN_EMAIL](arkts-ime-inputmethodengine-con.md#pattern_email) | 邮件编辑框。 |
| [PATTERN_NEW_PASSWORD](arkts-ime-inputmethodengine-con.md#pattern_new_password) | 新密码编辑框。 |
| [PATTERN_NULL](arkts-ime-inputmethodengine-con.md#pattern_null) | 无特殊性编辑框。 |
| [PATTERN_NUMBER](arkts-ime-inputmethodengine-con.md#pattern_number) | 数字编辑框。 |
| [PATTERN_NUMBER_DECIMAL](arkts-ime-inputmethodengine-con.md#pattern_number_decimal) | 带小数点的数字编辑框。 |
| [PATTERN_ONE_TIME_CODE](arkts-ime-inputmethodengine-con.md#pattern_one_time_code) | 验证码编辑框。 |
| [PATTERN_PASSWORD](arkts-ime-inputmethodengine-con.md#pattern_password) | 密码编辑框。 |
| [PATTERN_PASSWORD_NUMBER](arkts-ime-inputmethodengine-con.md#pattern_password_number) | 数字密码编辑框。 |
| [PATTERN_PASSWORD_SCREEN_LOCK](arkts-ime-inputmethodengine-con.md#pattern_password_screen_lock) | 锁屏密码编辑框。 |
| [PATTERN_PHONE](arkts-ime-inputmethodengine-con.md#pattern_phone) | 电话号码编辑框。 |
| [PATTERN_TEXT](arkts-ime-inputmethodengine-con.md#pattern_text) | 文本编辑框。 |
| [PATTERN_URI](arkts-ime-inputmethodengine-con.md#pattern_uri) | 超链接编辑框。 |
| [PATTERN_USER_NAME](arkts-ime-inputmethodengine-con.md#pattern_user_name) | 用户名编辑框。 |
| [WINDOW_TYPE_INPUT_METHOD_FLOAT](arkts-ime-inputmethodengine-con.md#window_type_input_method_float) | 输入法应用窗口风格标识。 |

