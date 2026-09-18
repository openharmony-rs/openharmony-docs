# @ohos.multimodalInput.inputConsumer(全局快捷键)

全局快捷键订阅模块，用于处理组合按键的订阅，本模块也支持音量键拦截监听能力。

**起始版本：** 14

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

## 导入模块

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getAllSystemHotkeys](arkts-input-inputconsumer-getallsystemhotkeys-f.md) | 获取所有系统快捷键，使用Promise异步回调。 |
| [off](arkts-input-inputconsumer-off-f.md#offhotkeychange) | 取消订阅应用快捷键。使用callback异步回调。 |
| [off](arkts-input-inputconsumer-off-f.md#offkeypressed) | 取消对'keyPressed'事件的订阅，使用callback异步回调。调用该方法后，被屏蔽的系统按键默认行为将恢复，即系统对音量调节等默认响应将恢复。 |
| [on](arkts-input-inputconsumer-on-f.md#onhotkeychange) | 订阅应用快捷键。获取满足条件的组合按键输入事件，使用callback异步回调。 |
| [on](arkts-input-inputconsumer-on-f.md#onkeypressed) | 订阅按键按下事件。若当前应用窗口为前台焦点窗口，用户按下指定按键，会触发回调。使用callback异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getShieldStatus](arkts-input-inputconsumer-getshieldstatus-f-sys.md) | 获取系统快捷键屏蔽类型。 |
| [off](arkts-input-inputconsumer-off-f-sys.md#offkey) | 取消订阅系统快捷键。使用callback异步回调。 |
| [offKey](arkts-input-inputconsumer-offkey-f-sys.md) | 取消订阅系统快捷键。使用callback异步回调。 |
| [on](arkts-input-inputconsumer-on-f-sys.md#onkey) | 订阅系统快捷键，使用callback异步回调。 |
| [onKey](arkts-input-inputconsumer-onkey-f-sys.md) | 订阅组合按键（按键命令模式），支持通过triggerType指定不同的触发模式。当满足条件的组合按键输入事件发生时，使用callback异步回调。 |
| [setShieldStatus](arkts-input-inputconsumer-setshieldstatus-f-sys.md) | 设置系统快捷键屏蔽类型。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [HotkeyOptions](arkts-input-inputconsumer-hotkeyoptions-i.md) | 快捷键选项。 |
| [KeyPressedConfig](arkts-input-inputconsumer-keypressedconfig-i.md) | 按键事件消费设置。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [KeyOptions](arkts-input-inputconsumer-keyoptions-i-sys.md) | 组合键选项。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [KeyCommandTriggerType](arkts-input-inputconsumer-keycommandtriggertype-e-sys.md) | 按键命令触发类型枚举，用于指定组合按键的触发时机。 |
| [ShieldMode](arkts-input-inputconsumer-shieldmode-e-sys.md) | 系统快捷键屏蔽类型。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [KeyCommandCallback](arkts-input-inputconsumer-keycommandcallback-t-sys.md) | 按键命令回调函数类型，当快捷键注册条件满足时触发的回调。 |
<!--DelEnd-->
