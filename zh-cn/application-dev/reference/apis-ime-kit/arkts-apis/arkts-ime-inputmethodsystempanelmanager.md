# @ohos.inputMethodSystemPanelManager(输入法系统面板管理器(系统接口))

@ohos.inputMethodSystemPanelManager模块是面向系统应用的输入法系统面板管理模块，用于输入法系统面板与系统预置输入法应用之间的通信和状态同步。<br> <br>本模块是一个系统接口模块，提供输入法系统面板（系统级面板组件）与系统预置输入法应用之间的双向通信通道。系统面板通过本模块可以感知输入法状态变化、接收输入法应用发送的私有命令，也可向输入法应用发送私有命令。<br> <br>本模块提供三大核心能力：1）通过`connectSystemChannel`建立系统面板与输入法应用之间的通信通道；2）通过`onSystemPanelStatusChange`订阅系统面板状态变化（包括输入类型、面板标志、面板升起状态、功能按钮需求），系统面板据此自适应调整自身布局；3）通过`onSystemPrivateCommand`/`sendPrivateCommand`实现系统面板与输入法应用之间的私有数据双向通信，用于传递自定义指令和配置数据。<br> <br>当开发输入法系统面板（系统级面板组件）时使用本模块。系统面板需要与系统预置输入法应用协同工作时，须先调用`connectSystemChannel`建立通道，再订阅状态变化和私有命令事件。<br> <br>本模块的核心开放能力由以下关键类型承载：<br>

| Interface/Enum | 说明 |  
|---|---|  
| SystemPanelStatus | 系统面板状态信息，描述当前系统面板的输入类型（InputMethodInputType）、面板标志（PanelFlag）、面板升起状态和功能按钮需求。当输入法状态变化时，系统面板通过订阅此状态调整自身布局。 |  
| InputMethodInputType | 输入类型枚举，标识系统面板支持的输入模式，包括无输入、相机输入、安全输入、语音输入和悬浮语音输入五种类型，对应不同的输入场景和面板布局。 |  
| CommandDataType | 私有数据类型联合类型（number、string 、boolean），用于私有命令通信中参数的具体类型定义。 |<br> <br>本模块的核心功能通过命名空间级函数直接提供，无需获取实例对象：<br> <br>- 私有数据命令通信：系统面板与输入法应用之间的双向自定义数据传输。系统面板可通过sendPrivateCommand向输入法应用发送私有命令，通过[onSystemPrivateCommand](arkts-ime-inputmethodsystempanelmanager-onsystemprivatecommand-f-sys.md)接收输入法应用发送的私有命令。私有数据通道常用于设备级厂商在特定设备上实现自定义的输入法功能。<br>- 面板状态同步：系统面板通过[onSystemPanelStatusChange](arkts-ime-inputmethodsystempanelmanager-onsystempanelstatuschange-f-sys.md)订阅并获取面板状态变化通知，包括输入类型、面板标志、底部抬高状态和功能按钮需求等。<br> <br>本模块与输入法框架其他模块的关系如下：<br> <br>- [@ohos.inputMethodEngine](arkts-ime-inputmethodengine.md)：面向输入法应用，提供输入法服务端能力。输入法应用侧通过inputMethodEngine.on('privateCommand')接收系统面板发送的私有命令，通过inputMethodEngine.sendPrivateCommand（TextInputClient方法）向文本框或系统组件发送私有命令。<br>- [@ohos.inputMethod.Panel](arkts-ime-inputmethod-panel.md)：定义面板属性类型PanelFlag和PanelType，本模块的SystemPanelStatus中引用了PanelFlag类型。<br>- @ohos.inputMethodSystemPanelManager（本模块）：面向系统面板，提供系统面板与输入法应用之间的通信和状态同步能力。<br> <br>典型调用流程：[connectSystemChannel](arkts-ime-inputmethodsystempanelmanager-connectsystemchannel-f-sys.md)（建立通信通道）→ [onSystemPrivateCommand](arkts-ime-inputmethodsystempanelmanager-onsystemprivatecommand-f-sys.md) / [onSystemPanelStatusChange](arkts-ime-inputmethodsystempanelmanager-onsystempanelstatuschange-f-sys.md)（订阅事件）→ sendPrivateCommand（发送私有命令）。在使用本模块的通信和订阅接口前，需先调用connectSystemChannel建立系统通道连接。<br> <br>使用本模块需要多个API组合配合：先调用`connectSystemChannel`建立通信通道 -> 再订阅状态变化和私有命令事件 -> 在事件回调中处理状态数据和私有命令 -> 可通过`sendPrivateCommand`向输入法应用发送命令。<br> <br>```javascript <br>// 以下为阐述调用逻辑的伪代码<br> <br>// 1. 连接系统通道（必须在其他操作之前调用）<br>inputMethodSystemPanelManager.connectSystemChannel(); <br> <br>// 2. 订阅系统面板状态变化事件<br>inputMethodSystemPanelManager.onSystemPanelStatusChange((status) =&gt; {<br> // 根据status.inputType调整面板布局（相机/安全/语音等）<br> // 根据status.panelFlag切换面板状态（固定态/悬浮态/候选态）<br> // 根据status.isPanelRaised决定是否底部抬高<br> // 根据status.needFuncButton决定是否显示功能按钮<br>}); <br> <br>// 3. 订阅输入法应用发送的私有命令<br>inputMethodSystemPanelManager.onSystemPrivateCommand((commandData) =&gt; {<br> // 处理输入法应用发来的自定义指令<br>}); <br> <br>// 4. 向输入法应用发送私有命令<br>inputMethodSystemPanelManager.sendPrivateCommand({ 'key1': 1, 'key2': 'value' }); <br> <br>// 5. 不再需要时取消订阅CommandDataType <br>inputMethodSystemPanelManager.offSystemPanelStatusChange(); <br>inputMethodSystemPanelManager.offSystemPrivateCommand(); <br>``` <br> <br>

> **说明：** <br>
> <br>
> `connectSystemChannel`必须在订阅事件和发送命令之前调用，否则相关操作将因通道未连接而返回错误码12800026。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace inputMethodSystemPanelManager--><!--Device-unnamed-declare namespace inputMethodSystemPanelManager-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [connectSystemChannel](arkts-ime-inputmethodsystempanelmanager-connectsystemchannel-f-sys.md#connectsystemchannel-1) | 连接系统通道，用于建立输入法系统面板和系统预置输入法应用之间的通信连接。仅允许系统预置输入法面板调用。<br> <br>含义/功能：建立系统面板与系统预置输入法应用之间的通信通道，为后续的私有命令收发和面板状态同步提供连接基础。<br> <br>使用场景：当系统面板需要与系统预置输入法应用进行私有命令通信或面板状态同步时，必须先调用此接口建立通信通道。<br> <br>使用后效果：连接成功后，系统面板与输入法应用之间的通信通道建立，后续可调用sendPrivateCommand、[onSystemPrivateCommand](arkts-ime-inputmethodsystempanelmanager-onsystemprivatecommand-f-sys.md)和[onSystemPanelStatusChange](arkts-ime-inputmethodsystempanelmanager-onsystempanelstatuschange-f-sys.md)等接口进行数据通信和状态同步。<br> <br>前提条件：需具有ohos.permission.CONNECT_IME_ABILITY权限，且调用者必须是系统应用和系统预置输入法面板。<br> <br>相关接口间的配合/制约关系：本接口是使用本模块其他通信接口的前提，必须先调用connectSystemChannel建立通道后，才能使用sendPrivateCommand、[onSystemPrivateCommand](arkts-ime-inputmethodsystempanelmanager-onsystemprivatecommand-f-sys.md)和[onSystemPanelStatusChange](arkts-ime-inputmethodsystempanelmanager-onsystempanelstatuschange-f-sys.md)等接口。 |
| [offSystemPanelStatusChange](arkts-ime-inputmethodsystempanelmanager-offsystempanelstatuschange-f-sys.md#offsystempanelstatuschange-1) | 取消订阅系统面板状态变化事件。<br> <br>使用场景：当系统面板不再需要接收面板状态变化通知时使用此接口，如面板关闭或退出时。<br> <br>相关接口间的配合/制约关系：取消订阅后，之前通过[onSystemPanelStatusChange](arkts-ime-inputmethodsystempanelmanager-onsystempanelstatuschange-f-sys.md)注册的回调将不再被触发。 |
| [offSystemPrivateCommand](arkts-ime-inputmethodsystempanelmanager-offsystemprivatecommand-f-sys.md#offsystemprivatecommand-1) | 取消订阅系统预置输入法应用发送私有数据命令的事件。<br> <br>使用场景：当系统面板不再需要接收来自输入法应用的私有命令通知时使用此接口，如面板关闭或退出时。<br> <br>相关接口间的配合/制约关系：取消订阅后，之前通过[onSystemPrivateCommand](arkts-ime-inputmethodsystempanelmanager-onsystemprivatecommand-f-sys.md)注册的回调将不再被触发。 |
| [onSystemPanelStatusChange](arkts-ime-inputmethodsystempanelmanager-onsystempanelstatuschange-f-sys.md#onsystempanelstatuschange-1) | 订阅系统面板状态变化事件。当系统面板的输入类型、面板标志、底部抬高状态或功能按钮需求发生变化时，将触发回调通知。<br> <br>使用场景：当系统面板需要感知自身状态变化并做出相应调整（如根据输入类型切换面板布局、根据面板标志调整显示形态等）时使用此接口。<br> <br>使用后效果：订阅成功后，每当系统面板状态发生变化，系统将通过callback传入最新的[SystemPanelStatus](arkts-ime-inputmethodsystempanelmanager-systempanelstatus-i-sys.md)对象，包含当前输入类型、面板标志、底部抬高状态和功能按钮需求。<br> <br>前提条件：需先调用[connectSystemChannel](arkts-ime-inputmethodsystempanelmanager-connectsystemchannel-f-sys.md)建立系统通道连接。 |
| [onSystemPrivateCommand](arkts-ime-inputmethodsystempanelmanager-onsystemprivatecommand-f-sys.md#onsystemprivatecommand-1) | 订阅系统预置输入法应用发送私有数据命令的事件。当输入法应用通过inputMethodEngine.sendPrivateCommand（TextInputClient方法）向系统组件发送私有命令时，系统面板会通过此回调接收到该命令数据。<br> <br>使用场景：当系统面板需要接收来自输入法应用的私有数据命令（如自定义配置、状态通知等）时使用此接口。<br> <br>使用后效果：订阅成功后，每当输入法应用发送私有命令，系统面板将通过callback接收到Record<string, CommandDataType>格式的命令数据。<br> <br>前提条件：需先调用[connectSystemChannel](arkts-ime-inputmethodsystempanelmanager-connectsystemchannel-f-sys.md)建立系统通道连接。<br> <br>相关接口间的配合/制约关系：本接口是系统面板侧的私有命令接收接口，对应输入法应用侧的inputMethodEngine.sendPrivateCommand（发送端）和inputMethodEngine.on('privateCommand')（输入法应用侧接收端）。私有命令通信方向：输入法应用 → 系统面板。<br> <br> &#124; 参数名 &#124; 类型 &#124; 必填 &#124; 说明 &#124; |
| [sendPrivateCommand](arkts-ime-inputmethodsystempanelmanager-sendprivatecommand-f-sys.md#sendprivatecommand-1) | 发送私有命令给系统预置输入法应用。使用Promise异步回调。<br> <br>含义/功能：系统面板向系统预置输入法应用发送自定义私有数据命令，数据格式为键值对映射（Record<string, CommandDataType>）。<br> <br>使用场景：当系统面板需要向输入法应用发送自定义配置命令、状态通知等私有数据时使用此接口。私有数据通道是系统预置输入法应用与系统特定组件的通信机制，常用于设备级厂商在特定设备上实现自定义的输入法功能。<br> <br>使用后效果：调用后，私有命令数据将发送给当前系统预置输入法应用。输入法应用可通过inputMethodEngine.on('privateCommand')接收此命令数据。<br> <br>前提条件：需先调用[connectSystemChannel](arkts-ime-inputmethodsystempanelmanager-connectsystemchannel-f-sys.md)建立系统通道连接。<br> <br>相关接口间的配合/制约关系：本接口是系统面板侧的私有命令发送接口，对应输入法应用侧的inputMethodEngine.on('privateCommand')（接收端）。私有命令通信方向：系统面板 → 输入法应用。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SystemPanelStatus](arkts-ime-inputmethodsystempanelmanager-systempanelstatus-i-sys.md) | 系统面板状态信息，用于描述当前系统面板的输入类型、面板标志、升起状态和功能按钮需求。当系统面板状态发生变化时，会通过[onSystemPanelStatusChange](arkts-ime-inputmethodsystempanelmanager-onsystempanelstatuschange-f-sys.md)接口通知订阅者。<br> <br>&#124; 名称 &#124; 类型 &#124; 只读 &#124; 可选 &#124; 说明 &#124; |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CommandDataType](arkts-ime-inputmethodsystempanelmanager-commanddatatype-t-sys.md) | 表示私有数据命令中值的数据类型。接口参数具体类型根据其功能而定，key为命令名称（string类型），value为命令数据值（支持number、string或boolean类型）。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [InputMethodInputType](arkts-ime-inputmethodsystempanelmanager-inputmethodinputtype-e-sys.md) | 输入类型枚举，用于标识系统面板支持的输入模式。不同的输入类型对应不同的输入场景和面板布局。<br> <br>&#124; 名称 &#124; 值 &#124; 说明 &#124; |
<!--DelEnd-->
