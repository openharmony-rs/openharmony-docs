# @ohos.selectionInput.selectionManager

本模块提供划词管理能力，包括创建窗口、显示窗口、移动窗口、隐藏窗口、销毁窗口、监听鼠标划词事件、获取选中文本等。

> **说明：**
> - 本模块仅支持PC/2in1设备。
> - 仅支持集成了划词扩展的应用调用。

**起始版本：** 24

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createPanel](arkts-basicservices-createpanel-f-sys.md#createpanel-1) | 创建划词面板。使用Promise异步回调。单个划词应用仅允许创建一个[MENU_PANEL](arkts-selectioninput-selectionpanel.md)和一个[MAIN_PANEL](arkts-selectioninput-selectionpanel.md)。 |
| [destroyPanel](arkts-basicservices-destroypanel-f-sys.md#destroypanel-1) | 销毁划词面板。使用Promise异步回调。 |
| [getSelectionContent](arkts-basicservices-getselectioncontent-f-sys.md#getselectioncontent-1) | 获取选中文本的内容。使用Promise异步回调。 |
| [off](arkts-basicservices-off-f-sys.md#off-1) | 取消订阅划词完成事件。使用callback异步回调。 |
| [on](arkts-basicservices-on-f-sys.md#on-1) | 订阅划词完成事件。使用callback异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [Panel](arkts-basicservices-panel-i.md) | 划词面板。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Panel](arkts-basicservices-panel-i-sys.md) | 划词面板。 |
| [SelectionInfo](arkts-basicservices-selectioninfo-i-sys.md) | 划词事件信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SelectionType](arkts-basicservices-selectiontype-e-sys.md) | 定义触发划词的类型枚举。 |
<!--DelEnd-->

