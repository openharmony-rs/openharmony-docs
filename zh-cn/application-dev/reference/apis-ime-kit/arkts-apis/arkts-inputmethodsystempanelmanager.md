# @ohos.inputMethodSystemPanelManager

输入法系统面板管理器。

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
| [connectSystemChannel](arkts-ime-inputmethodsystempanelmanager-connectsystemchannel-f-sys.md) | 连接面板和输入法之间的系统通道。 |
| [offSystemPanelStatusChange](arkts-ime-inputmethodsystempanelmanager-offsystempanelstatuschange-f-sys.md) | 取消订阅系统面板状态改变事件。 |
| [offSystemPrivateCommand](arkts-ime-inputmethodsystempanelmanager-offsystemprivatecommand-f-sys.md) | 取消订阅输入法应用发送私有数据命令的事件。 |
| [onSystemPanelStatusChange](arkts-ime-inputmethodsystempanelmanager-onsystempanelstatuschange-f-sys.md) | 订阅系统面板状态改变事件。 |
| [onSystemPrivateCommand](arkts-ime-inputmethodsystempanelmanager-onsystemprivatecommand-f-sys.md) | 订阅输入法应用发送私有数据命令的事件。 |
| [sendPrivateCommand](arkts-ime-inputmethodsystempanelmanager-sendprivatecommand-f-sys.md) | 发送私有命令。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SystemPanelStatus](arkts-ime-inputmethodsystempanelmanager-systempanelstatus-i-sys.md) | 系统面板状态。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [InputMethodInputType](arkts-ime-inputmethodsystempanelmanager-inputmethodinputtype-e-sys.md) | 定义输入类型。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CommandDataType](arkts-ime-inputmethodsystempanelmanager-commanddatatype-t-sys.md) | 表示命令的数据类型。 |
<!--DelEnd-->

