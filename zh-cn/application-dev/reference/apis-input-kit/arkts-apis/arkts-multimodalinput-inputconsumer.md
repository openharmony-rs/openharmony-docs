# @ohos.multimodalInput.inputConsumer

全局快捷键订阅模块，用于处理组合按键的订阅，本模块也支持音量键拦截监听能力。

> **说明：**
>
> - 全局快捷键指由系统或应用定义的组合按键，系统快捷键指由系统定义的全局快捷键，应用快捷键指由应用定义的全局快捷键。

**起始版本：** 14

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAllSystemHotkeys](arkts-input-getallsystemhotkeys-f.md#getallsystemhotkeys-1) | 获取所有系统快捷键，使用Promise异步回调。 |
| [off](arkts-input-off-f.md#off-2) | 取消订阅应用快捷键。使用callback异步回调。 |
| [off](arkts-input-off-f.md#off-3) | 取消对'keyPressed'事件的订阅，使用callback异步回调。调用该方法后，被屏蔽的系统按键默认行为将恢复，即系统对音量调节等默认响应将恢复。 |
| [on](arkts-input-on-f.md#on-2) | 订阅应用快捷键。获取满足条件的组合按键输入事件，使用callback异步回调。 |
| [on](arkts-input-on-f.md#on-3) | 订阅按键按下事件。若当前应用窗口为前台焦点窗口，用户按下指定按键，会触发回调。使用callback异步回调。订阅成功后，该按键事件的系统默认行为将被屏蔽，即不会再触发系统级的响应，如音量调节。要恢复系统响应，请使用[off](arkts-input-off-f.md#off-3)方法取消订阅。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getShieldStatus](arkts-input-getshieldstatus-f-sys.md#getshieldstatus-1) | 获取系统快捷键屏蔽类型。 |
| [off](arkts-input-off-f-sys.md#off-1) | 取消订阅系统快捷键。使用callback异步回调。 |
| [offKey](arkts-input-offkey-f-sys.md#offkey-1) | 取消订阅系统快捷键。使用callback异步回调。 |
| [on](arkts-input-on-f-sys.md#on-1) | 订阅系统快捷键，使用callback异步回调。 |
| [onKey](arkts-input-onkey-f-sys.md#onkey-1) | 订阅组合按键（按键命令模式），支持通过triggerType指定不同的触发模式。当满足条件的组合按键输入事件发生时，使用callback异步回调。与 [inputConsumer.on('key')](arkts-input-on-f-sys.md#on-1)现有接口的区别：- 本接口的keyOptions支持triggerType参数，可选择按键按下触发、重复按下触发、重复按下或抬起均会触发等模式。- 本接口回调参数为KeyCommandCallback类型，同时接收KeyOptions和KeyEvent对象。- 本接口采用事件消费机制，可通过事件消费阻止按键事件向后传递。 |
| [setShieldStatus](arkts-input-setshieldstatus-f-sys.md#setshieldstatus-1) | 设置系统快捷键屏蔽类型。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [HotkeyOptions](arkts-input-hotkeyoptions-i.md) | 快捷键选项。 |
| [KeyPressedConfig](arkts-input-keypressedconfig-i.md) | 按键事件消费设置。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [KeyOptions](arkts-input-keyoptions-i-sys.md) | 组合键选项。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [KeyCommandTriggerType](arkts-input-keycommandtriggertype-e-sys.md) | 按键命令触发类型枚举，用于指定组合按键的触发时机。 |
| [ShieldMode](arkts-input-shieldmode-e-sys.md) | 系统快捷键屏蔽类型。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [KeyCommandCallback](arkts-input-keycommandcallback-t-sys.md) | 按键命令回调函数类型，当快捷键注册条件满足时触发的回调。 |
<!--DelEnd-->

