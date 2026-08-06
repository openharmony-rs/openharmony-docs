# @ohos.selectionInput.selectionManager

本模块提供划词管理能力，包括创建窗口、显示窗口、移动窗口、隐藏窗口、销毁窗口、监听鼠标划词事件、获取选中文本等。 > **说明：** > - 本模块仅支持PC/2in1设备。 > - 仅支持集成了划词扩展的应用调用。

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为24。

<!--Device-unnamed-declare namespace selectionManager--><!--Device-unnamed-declare namespace selectionManager-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createPanel](arkts-basicservices-selectionmanager-createpanel-f.md#createpanel) | 创建划词面板。使用Promise异步回调。 单个划词应用仅允许创建一个[MENU\_\_\_ESCAPED\_UNDERSCORE\_\_\_PANEL]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_和一个 [MAIN\_\_\_ESCAPED\_UNDERSCORE\_\_\_PANEL]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f.md#destroypanel) | 销毁划词面板。使用Promise异步回调。 |
| [getSelectionContent](arkts-basicservices-selectionmanager-getselectioncontent-f.md#getselectioncontent) | 获取选中文本的内容。使用Promise异步回调。 |
| [off](arkts-basicservices-selectionmanager-off-f.md#off) | 取消订阅划词完成事件。使用callback异步回调。 |
| [offSelectionComplete](arkts-basicservices-selectionmanager-offselectioncomplete-f.md#offselectioncomplete) | 取消订阅划词完成事件。使用callback异步回调。 |
| [on](arkts-basicservices-selectionmanager-on-f.md#on) | 订阅划词完成事件。使用callback异步回调。 |
| [onSelectionComplete](arkts-basicservices-selectionmanager-onselectioncomplete-f.md#onselectioncomplete) | 订阅划词完成事件。使用callback异步回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Panel](arkts-basicservices-selectionmanager-panel-i.md) | 划词面板。 |
| [SelectionInfo](arkts-basicservices-selectionmanager-selectioninfo-i.md) | 划词事件信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SelectionType](arkts-basicservices-selectionmanager-selectiontype-e.md) | 定义触发划词的类型枚举。 |

