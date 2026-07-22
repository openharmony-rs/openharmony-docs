# @ohos.inputMethod

**@ohos.inputMethod**模块是面向普通前台应用（如备忘录、短信、设置等系统应用）的输入法客户端模块，提供输入法控制和管理能力。

本模块是输入法框架的客户端接口，为编辑框应用提供与输入法服务的交互能力，包括输入法绑定/解绑、软键盘显示/隐藏、输入法切换、输入法列表查询、编辑框属性与光标更新、文本选择与操作事件监听、自定义消息通信等。

本模块提供两大核心能力集：1）通过`InputMethodController`实现编辑框应用与输入法之间的绑定、交互和事件监听——编辑框应用绑定输入法后可控制键盘显隐、更新光标和编辑属性、监听输入法发出的文本操作事件（插入、删除、选中文本、移动光标、发送功能键和扩展动作等），以及通过自定义消息通道与输入法应用双向通信；2）通过`InputMethodSetting`实现输入法管理——获取输入法列表、查询当前输入法及子类型、订阅输入法切换事件、切换输入法及子类型、查询面板显示状态等。

当开发带有文本编辑框的应用（需要与输入法交互）或系统应用（需要管理输入法）时使用本模块。典型场景包括：应用中编辑框获取焦点时绑定输入法并显示键盘、编辑框失去焦点时解绑输入法并隐藏键盘、系统设置应用中切换和配置输入法等。

本模块是IME Kit（输入法框架Kit）中的客户端控制模块，与IME Kit中的其他模块协同工作：

- **@ohos.inputMethodEngine**：面向输入法应用的服务端模块，提供软键盘窗口创建、文本插入/删除、监听物理按键等能力。本模块（@ohos.inputMethod）发出的请求（如显示键盘、切换输入法）最终由@ohos.inputMethodEngine侧的输入法应用响应和处理。  
- **@ohos.inputMethodList**：提供输入法列表选择对话框的显示与管理能力。  
- **@ohos.inputMethod.Panel**：定义输入法面板类型与状态信息，用于查询面板可见性等。

典型的客户端应用（如备忘录、设置）与输入法交互的调用序列如下：

1. 通过`inputMethod.getController()`获取客户端控制器实例`InputMethodController`。2. 通过`InputMethodController.attach()`绑定输入法（对于自绘控件场景），或依赖系统原生编辑框自动绑定。3. 通过`InputMethodController.showTextInput()`拉起软键盘，进入文本编辑状态。4. 在编辑过程中，通过`updateCursor`、`changeSelection`、`updateAttribute`等接口向输入法同步编辑框状态。5. 通过`InputMethodController.hideTextInput()`隐藏软键盘，退出编辑状态。6. 通过`InputMethodController.detach()`解除与输入法的绑定。

**配对约束：**

- `attach`与`detach`必须配对使用，未detach而直接退出可能导致资源泄漏。  
- `showTextInput`与`hideTextInput`必须配对使用，避免输入法状态不一致。

本模块的核心开放能力由以下关键Interface承载：

| Interface | 说明 |  
|---|---|  
| **InputMethodController** | 输入法控制器，编辑框应用与输入法交互的核心对象。提供绑定/解绑输入法（attach/detach）、显示/隐藏键盘（showTextInput/hideTextInput/showSoftKeyboard/hideSoftKeyboard）、更新光标和编辑属性（updateCursor/updateAttribute/changeSelection）、监听输入法操作事件（insertText/deleteLeft/deleteRight/selectByRange/selectByMovement/moveCursor/sendFunctionKey/sendKeyboardStatus/handleExtendAction/setPreviewText/finishTextPreview）、自定义消息通信（sendMessage/recvMessage）、停止输入会话等能力。通过`getController()`获取实例。 |  
| **InputMethodSetting** | 输入法设置管理对象，提供输入法查询和管理能力。包括获取已启用/已禁用/全部输入法列表（getInputMethods/getAllInputMethods）、查询指定输入法的子类型列表（listInputMethodSubtype）、获取当前输入法及子类型、订阅输入法切换事件（on('imeChange')）、订阅面板显隐事件（on('imeShow')/on('imeHide')）、查询面板显示状态（isPanelShown）、启用/禁用输入法（enableInputMethod）、获取输入法自身启用状态（getInputMethodState）等。通过`getSetting()`获取实例。 |

此外，本模块还定义了多个关键数据类型：

| 类型 | 说明 |  
|---|---|  
| **InputMethodProperty** | 输入法属性信息，描述一个输入法的名称、ID、标签、图标、启用状态等。 |  
| **InputMethodSubtype** | 输入法子类型，描述输入法的语言、模式等子类型属性。 |  
| **TextConfig** | 编辑框文本配置，包含输入属性（InputAttribute）、光标信息（CursorInfo）、选区信息、窗口ID等。 |  
| **InputAttribute** | 输入属性，定义文本输入类型（TextInputType）和回车键类型（EnterKeyType）。 |  
| **CursorInfo** | 光标信息，定义光标的位置和尺寸。 |  
| **MessageHandler** | 自定义消息处理器，用于接收输入法应用发送的消息并提供终止通知。 |

编辑框应用与输入法交互的典型流程涉及InputMethodController的多个API组合调用：获取控制器 -> 绑定输入法 -> 订阅输入法操作事件 -> 在回调中处理文本操作 -> 解绑输入法。

**起始版本：** 6

<!--Device-unnamed-declare namespace inputMethod--><!--Device-unnamed-declare namespace inputMethod-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getController](arkts-ime-inputmethod-getcontroller-f.md#getcontroller) | 获取客户端实例[InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md)。  **含义/功能**：获取当前应用的输入法客户端控制器实例，用于后续与输入法进行交互（绑定、显示/隐藏键盘、同步编辑框状态等）。  **使用场景：**当前台应用（如备忘录、聊天应用）需要控制输入法的显示/隐藏、绑定/解绑、同步编辑框信息时，必须先通过此接口获取InputMethodController实例。  **使用后效果**：返回一个InputMethodController实例，后续可通过该实例调用attach、showTextInput、hideTextInput、detach等一系列接口与输入法交互。 |
| [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f.md#getcurrentinputmethod) | 使用同步方法获取当前输入法。  **含义/功能**：获取当前正在使用的输入法属性信息。  **使用场景：**当应用需要知道当前活跃的输入法是哪个（如判断输入法名称、获取输入法id用于后续切换操作）时使用。  **使用后效果**：返回当前输入法的InputMethodProperty对象。 |
| [getCurrentInputMethodSubtype](arkts-ime-inputmethod-getcurrentinputmethodsubtype-f.md#getcurrentinputmethodsubtype) | 获取当前输入法的子类型。 |
| [getDefaultInputMethod](arkts-ime-inputmethod-getdefaultinputmethod-f.md#getdefaultinputmethod) | 获取默认输入法。 |
| [getInputMethodController](arkts-ime-inputmethod-getinputmethodcontroller-f.md#getinputmethodcontroller) | 获取客户端实例[InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md)。 |
| [getInputMethodSetting](arkts-ime-inputmethod-getinputmethodsetting-f.md#getinputmethodsetting) | 获取客户端设置实例[InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md)。 |
| [getSetting](arkts-ime-inputmethod-getsetting-f.md#getsetting) | 获取客户端设置实例[InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md)。  **含义/功能**：获取输入法设置实例，用于查询输入法列表、订阅输入法变化事件、查询面板可见性等配置管理操作。  **使用场景：**当应用需要查询已安装/已激活输入法列表、订阅输入法切换事件、或显示输入法选择对话框时，必须先通过此接口获取InputMethodSetting实例。  **使用后效果**：返回一个InputMethodSetting实例，后续可通过该实例调用getInputMethods、listInputMethodSubtype、on('imeChange')等接口。 |
| [getSystemInputMethodConfigAbility](arkts-ime-inputmethod-getsysteminputmethodconfigability-f.md#getsysteminputmethodconfigability) | 获取系统输入法设置界面Ability信息。 |
| [offAttachmentDidFail](arkts-ime-inputmethod-offattachmentdidfail-f.md#offattachmentdidfail) | 取消订阅绑定失败事件。使用callback异步回调。 |
| [onAttachmentDidFail](arkts-ime-inputmethod-onattachmentdidfail-f.md#onattachmentdidfail) | 订阅绑定失败事件。使用callback异步回调。 |
| [setSimpleKeyboardEnabled](arkts-ime-inputmethod-setsimplekeyboardenabled-f.md#setsimplekeyboardenabled) | 编辑框应用设置简单键盘标志。 |
| [switchCurrentInputMethodAndSubtype](arkts-ime-inputmethod-switchcurrentinputmethodandsubtype-f.md#switchcurrentinputmethodandsubtype) | 切换至指定输入法的指定子类型，适用于跨输入法切换子类型。使用callback异步回调。 |
| [switchCurrentInputMethodAndSubtype](arkts-ime-inputmethod-switchcurrentinputmethodandsubtype-f.md#switchcurrentinputmethodandsubtype-1) | 切换至指定输入法的指定子类型，适用于跨输入法切换子类型。使用promise异步回调。 |
| [switchCurrentInputMethodSubtype](arkts-ime-inputmethod-switchcurrentinputmethodsubtype-f.md#switchcurrentinputmethodsubtype) | 切换当前输入法的子类型。使用callback异步回调。 |
| [switchCurrentInputMethodSubtype](arkts-ime-inputmethod-switchcurrentinputmethodsubtype-f.md#switchcurrentinputmethodsubtype-1) | 切换当前输入法的子类型。使用promise异步回调。 |
| [switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f.md#switchinputmethod) | 切换输入法，使用callback异步回调。  **含义/功能**：将当前输入法切换为指定的目标输入法。  **使用场景：**当前输入法应用需要切换到另一个输入法时使用（如用户在输入法设置中选择了新的输入法）。  **使用后效果**：成功时系统将当前输入法切换为目标输入法，目标输入法成为新的当前输入法；失败时当前输入法不变。  **异步返回方式**：使用callback异步回调。成功时err为undefined，data为true；失败时返回BusinessError对象。 |
| [switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f.md#switchinputmethod-1) | 切换输入法，使用promise异步回调。  **含义/功能**：将当前输入法切换为指定的目标输入法。  **使用场景：**当前输入法应用需要切换到另一个输入法时使用。  **使用后效果**：成功时系统将当前输入法切换为目标输入法；失败时当前输入法不变。  **异步返回方式**：使用Promise异步回调。成功时返回true，失败时返回BusinessError对象。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getCurrentInputMethod](arkts-ime-inputmethod-getcurrentinputmethod-f-sys.md#getcurrentinputmethod-1) | 获取指定用户的当前输入法。 |
| [getCurrentInputMethodSubtype](arkts-ime-inputmethod-getcurrentinputmethodsubtype-f-sys.md#getcurrentinputmethodsubtype-1) | 获取指定用户的当前输入法子类型。 |
| [getDefaultInputMethod](arkts-ime-inputmethod-getdefaultinputmethod-f-sys.md#getdefaultinputmethod-1) | 获取指定用户的默认输入法。 |
| [getSystemInputMethodConfigAbility](arkts-ime-inputmethod-getsysteminputmethodconfigability-f-sys.md#getsysteminputmethodconfigability-1) | 获取指定用户的系统输入法设置界面Ability信息。用于启动系统输入法配置界面。 |
| [switchInputMethod](arkts-ime-inputmethod-switchinputmethod-f-sys.md#switchinputmethod-2) | 切换输入法，使用promise异步回调。 |
| [switchInputMethodWithUserId](arkts-ime-inputmethod-switchinputmethodwithuserid-f-sys.md#switchinputmethodwithuserid) | 切换输入法，使用promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AttachOptions](arkts-ime-inputmethod-attachoptions-i.md) | 绑定输入法的附加选项。 |
| [CursorInfo](arkts-ime-inputmethod-cursorinfo-i.md) | 光标信息。 |
| [FunctionKey](arkts-ime-inputmethod-functionkey-i.md) | 输入法功能键类型。 |
| [InputAttribute](arkts-ime-inputmethod-inputattribute-i.md) | 编辑框属性，包含文本输入类型和Enter键功能类型。 |
| [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md) | 下列API示例中都需使用[getController](arkts-ime-inputmethod-getcontroller-f.md#getcontroller)获取到InputMethodController实例，再通过实例调用对应方法。  InputMethodController是输入法客户端控制器，面向前台应用提供与输入法交互的核心能力。通过`inputMethod.getController()`获取实例后，可进行以下操作：  - **绑定管理**：通过[attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach)建立与输入法的绑定，通过[detach](arkts-ime-inputmethod-inputmethodcontroller-i.md#detach)解除绑定。attach和detach必须配对使用。  - **键盘控制**：通过[showTextInput](arkts-ime-inputmethod-inputmethodcontroller-i.md#showtextinput)拉起软键盘进入编辑状态，通过[hideTextInput](arkts-ime-inputmethod-inputmethodcontroller-i.md#hidetextinput)隐藏软键盘退出编辑状态。showTextInput和hideTextInput必须配对使用。  - **编辑框状态同步**：通过[updateCursor](arkts-ime-inputmethod-inputmethodcontroller-i.md#updatecursor)、[changeSelection](arkts-ime-inputmethod-inputmethodcontroller-i.md#changeselection)、[updateAttribute](arkts-ime-inputmethod-inputmethodcontroller-i.md#updateattribute)等接口向输入法同步光标、选区、属性等编辑框状态信息。  - **事件订阅**：通过on('insertText')、on('deleteLeft')等接口订阅输入法应用发送的文本操作事件。  典型调用序列：`getController()` → `attach()` → `showTextInput()`/`hideTextInput()` → `detach()` > **注意：**  >  > attach和detach必须配对使用，showTextInput和hideTextInput必须配对使用，否则可能导致资源泄漏或状态不一致。 |
| [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | 输入法应用属性。 |
| [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md) | InputMethodSetting提供输入法配置与查询能力，面向前台应用提供以下功能：  - **输入法变化订阅**：通过[on('imeChange')](inputMethod.InputMethodSetting.on( type: 'imeChange', callback: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void ))订阅输入法及子类型变化事件，当用户切换输入法时收到通知。  - **输入法列表查询**：通过[getInputMethods](arkts-ime-inputmethod-inputmethodsetting-i.md#getinputmethods)查询已激活/未激活输入法列表，通过[getAllInputMethods](arkts-ime-inputmethod-inputmethodsetting-i.md#getallinputmethods)查询所有已安装输入法列表，通过[listInputMethodSubtype](arkts-ime-inputmethod-inputmethodsetting-i.md#listinputmethodsubtype)查询指定输入法的子类型列表。  - **面板可见性查询**：通过isPanelShown查询输入法面板是否显示。  - **输入法选择对话框**：通过showOptionalInputMethods显示输入法选择对话框（已废弃，建议使用InputMethodListDialog）。  需通过[getSetting](arkts-ime-inputmethod-getsetting-f.md#getsetting)获取InputMethodSetting实例后使用。  下列API均需使用[getSetting](arkts-ime-inputmethod-getsetting-f.md#getsetting)获取到InputMethodSetting实例后，通过实例调用。 |
| [InputWindowInfo](arkts-ime-inputmethod-inputwindowinfo-i.md) | 输入法软键盘的窗口信息。 |
| [MessageHandler](arkts-ime-inputmethod-messagehandler-i.md) | 自定义通信对象。 |
| [Movement](arkts-ime-inputmethod-movement-i.md) | 选中文本时，光标移动的方向。 |
| [Range](arkts-ime-inputmethod-range-i.md) | 文本的选中范围。 |
| [TextConfig](arkts-ime-inputmethod-textconfig-i.md) | 编辑框的配置信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i-sys.md) | 下列API示例中都需使用[getController](arkts-ime-inputmethod-getcontroller-f.md#getcontroller)获取到InputMethodController实例，再通过实例调用对应方法。  InputMethodController是输入法客户端控制器，面向前台应用提供与输入法交互的核心能力。通过`inputMethod.getController()`获取实例后，可进行以下操作：  - **绑定管理**：通过[attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach)建立与输入法的绑定，通过[detach](arkts-ime-inputmethod-inputmethodcontroller-i.md#detach)解除绑定。attach和detach必须配对使用。  - **键盘控制**：通过[showTextInput](arkts-ime-inputmethod-inputmethodcontroller-i.md#showtextinput)拉起软键盘进入编辑状态，通过[hideTextInput](arkts-ime-inputmethod-inputmethodcontroller-i.md#hidetextinput)隐藏软键盘退出编辑状态。showTextInput和hideTextInput必须配对使用。  - **编辑框状态同步**：通过[updateCursor](arkts-ime-inputmethod-inputmethodcontroller-i.md#updatecursor)、[changeSelection](arkts-ime-inputmethod-inputmethodcontroller-i.md#changeselection)、[updateAttribute](arkts-ime-inputmethod-inputmethodcontroller-i.md#updateattribute)等接口向输入法同步光标、选区、属性等编辑框状态信息。  - **事件订阅**：通过on('insertText')、on('deleteLeft')等接口订阅输入法应用发送的文本操作事件。  典型调用序列：`getController()` → `attach()` → `showTextInput()`/`hideTextInput()` → `detach()` > **注意：**  >  > attach和detach必须配对使用，showTextInput和hideTextInput必须配对使用，否则可能导致资源泄漏或状态不一致。 |
| [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i-sys.md) | InputMethodSetting提供输入法配置与查询能力，面向前台应用提供以下功能：  - **输入法变化订阅**：通过[on('imeChange')](inputMethod.InputMethodSetting.on( type: 'imeChange', callback: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void ))订阅输入法及子类型变化事件，当用户切换输入法时收到通知。  - **输入法列表查询**：通过[getInputMethods](arkts-ime-inputmethod-inputmethodsetting-i.md#getinputmethods)查询已激活/未激活输入法列表，通过[getAllInputMethods](arkts-ime-inputmethod-inputmethodsetting-i.md#getallinputmethods)查询所有已安装输入法列表，通过[listInputMethodSubtype](arkts-ime-inputmethod-inputmethodsetting-i.md#listinputmethodsubtype)查询指定输入法的子类型列表。  - **面板可见性查询**：通过isPanelShown查询输入法面板是否显示。  - **输入法选择对话框**：通过showOptionalInputMethods显示输入法选择对话框（已废弃，建议使用InputMethodListDialog）。  需通过[getSetting](arkts-ime-inputmethod-getsetting-f.md#getsetting)获取InputMethodSetting实例后使用。  下列API均需使用[getSetting](arkts-ime-inputmethod-getsetting-f.md#getsetting)获取到InputMethodSetting实例后，通过实例调用。 |
| [InputWindowInfo](arkts-ime-inputmethod-inputwindowinfo-i-sys.md) | 输入法软键盘的窗口信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AttachFailureReason](arkts-ime-inputmethod-attachfailurereason-e.md) | 枚举，绑定失败的原因。 |
| [CapitalizeMode](arkts-ime-inputmethod-capitalizemode-e.md) | 枚举，定义了文本首字母大写的不同模式。  \| 名称 \| 值 \| 说明 \|  \| -------- \| -- \| -------- \|  \| NONE \| 0 \| 不进行任何首字母大写处理。  **使用场景：**适用于无需自动大写的输入框，如密码输入、验证码输入等。\|  \| SENTENCES \| 1 \| 每个句子的首字母大写。  **使用场景：**适用于普通文本输入框，如聊天、备忘录等，自动在句号等标点后将首字母大写。\|  \| WORDS \| 2 \| 每个单词首字母大写。  **使用场景：**适用于标题、人名等需要每个单词首字母大写的场景。\|  \| CHARACTERS \| 3 \| 每个字母都大写。  **使用场景：**适用于全大写输入场景，如缩写词输入（如URL中的域名部分）。\| |
| [Direction](arkts-ime-inputmethod-direction-e.md) | 光标移动方向。 |
| [EnabledState](arkts-ime-inputmethod-enabledstate-e.md) | 输入法启用状态。 |
| [EnterKeyType](arkts-ime-inputmethod-enterkeytype-e.md) | Enter键的功能类型。 |
| [ExtendAction](arkts-ime-inputmethod-extendaction-e.md) | 编辑框中文本的扩展编辑操作类型，如剪切、复制等。 |
| [KeyboardStatus](arkts-ime-inputmethod-keyboardstatus-e.md) | 输入法软键盘状态。 |
| [RequestKeyboardReason](arkts-ime-inputmethod-requestkeyboardreason-e.md) | 请求键盘输入的原因。 |
| [TextInputType](arkts-ime-inputmethod-textinputtype-e.md) | 文本输入类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [SetPreviewTextCallback](arkts-ime-inputmethod-setpreviewtextcallback-t.md) | 当输入法框架需要显示预览文本时触发的回调。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ImeChangeWithUserIdCallback](arkts-ime-inputmethod-imechangewithuseridcallback-t-sys.md) | 输入法变更事件回调，携带发生输入法变更的用户ID。 |
<!--DelEnd-->

### 常量

| 名称 | 说明 |
| --- | --- |
| [MAX_TYPE_NUM](arkts-ime-inputmethod-con.md#max_type_num) | 可支持的最大输入法个数。 |

