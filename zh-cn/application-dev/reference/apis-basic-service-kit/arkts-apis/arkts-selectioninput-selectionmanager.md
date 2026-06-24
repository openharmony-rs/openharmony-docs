# @ohos.selectionInput.selectionManager

本模块提供划词管理能力，包括创建窗口、显示窗口、移动窗口、隐藏窗口、销毁窗口、监听鼠标划词事件、获取选中文本等。

> **说明：**
> - 本模块仅支持PC/2in1设备。
> - 仅支持集成了划词扩展的应用调用。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel-1) | 创建划词面板。使用Promise异步回调。<br/>单个划词应用仅允许创建一个[MENU_PANEL](arkts-selectioninput-selectionpanel.md)和一个<br/>[MAIN_PANEL](arkts-selectioninput-selectionpanel.md)。<br/> |
| <!--DelRow-->[destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f-sys.md#destroyPanel-1) | 销毁划词面板。使用Promise异步回调。<br/> |
| <!--DelRow-->[getSelectionContent](arkts-basicservices-selectionmanager-getselectioncontent-f-sys.md#getSelectionContent-1) | 获取选中文本的内容。使用Promise异步回调。<br/> |
| <!--DelRow-->[off](arkts-basicservices-selectionmanager-off-f-sys.md#off-1) | 取消订阅划词完成事件。使用callback异步回调。<br/> |
| <!--DelRow-->[on](arkts-basicservices-selectionmanager-on-f-sys.md#on-1) | 订阅划词完成事件。使用callback异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Panel](arkts-basicservices-selectionmanager-panel-i.md) | 划词面板。<br/> |
| <!--DelRow-->[Panel](arkts-basicservices-selectionmanager-panel-i-sys.md) | 划词面板。<br/> |
| <!--DelRow-->[SelectionInfo](arkts-basicservices-selectionmanager-selectioninfo-i-sys.md) | 划词事件信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[SelectionType](arkts-basicservices-selectionmanager-selectiontype-e-sys.md) | 定义触发划词的类型枚举。<br/> |

