# @ohos.selectionInput.selectionManager

本模块提供划词管理能力，包括创建面板、显示面板、移动面板、隐藏面板、销毁面板、监听鼠标/触控板划词事件、获取选中文本等。典型使用流程如下： 1. 调用[on('selectionCompleted')](arkts-basicservices-selectionmanager-onselectioncompleted-f-sys.md#on_selectionCompleted)订阅划词完成事件。 2. 在回调中调用[getSelectionContent](arkts-basicservices-selectionmanager-getselectioncontent-f-sys.md#getSelectionContent（系统接口）)获取选中文本。 3. 调用[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)创建划词面板。 4. 调用[setUiContent](arkts-basicservices-selectionmanager-panel-i-sys.md#setUiContent)加载页面内容。 5. 调用[moveToGlobalDisplay](arkts-basicservices-selectionmanager-panel-i.md#moveToGlobalDisplay)移动面板到指定位置。 6. 调用[show](arkts-basicservices-selectionmanager-panel-i-sys.md#show)显示面板。 7. 调用[destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f-sys.md#destroyPanel（系统接口）)销毁面板。 8. 调用[off('selectionCompleted')](arkts-basicservices-selectionmanager-offselectioncompleted-f-sys.md#off_selectionCompleted)取消订阅划词完成事件。 > **说明：** > > - 本模块仅支持PC/2in1设备。开发者可通过canIUse('SystemCapability.SelectionInput.Selection')判断当前设备是否支持该功能。 > - 仅支持集成了划词扩展的应用调用，划词扩展的实现请参见 > [SelectionExtensionAbility](arkts-basicservices-selectioninput-selectionextensionability-selectionextensionability-c-sys.md#SelectionExtensionAbility（系统接口）)。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace selectionManager--><!--Device-unnamed-declare namespace selectionManager-End-->

**系统能力：** SystemCapability.SelectionInput.Selection

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offSelectionComplete](arkts-basicservices-selectionmanager-offselectioncomplete-f.md#offSelectionComplete) | 取消订阅划词完成事件，与[onSelectionComplete](arkts-basicservices-selectionmanager-onselectioncomplete-f.md#onSelectionComplete)搭配使 用。 |
| [onSelectionComplete](arkts-basicservices-selectionmanager-onselectioncomplete-f.md#onSelectionComplete) | 订阅划词完成事件，与[offSelectionComplete](arkts-basicservices-selectionmanager-offselectioncomplete-f.md#offSelectionComplete)搭配 使用取消订阅。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel) | 创建划词面板，用于向用户展示业务相关的操作界面或文本处理结果，使用完毕后需调用[destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f-sys.md#destroyPanel（系统接口）)销毁面板释放资源。使用Promise异步回调。 单个划词应用仅允许创建一个[MENU_PANEL](arkts-basicservices-selectioninput-selectionpanel-paneltype-e-sys.md#PanelType（系统接口）)和一个 [MAIN_PANEL](arkts-basicservices-selectioninput-selectionpanel-paneltype-e-sys.md#PanelType（系统接口）)。 |
| [destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f-sys.md#destroyPanel) | 销毁划词面板。与[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)搭配使用，用于销毁由createPanel()创建的面板对象。使用Promise异步回调。 |
| [getSelectionContent](arkts-basicservices-selectionmanager-getselectioncontent-f-sys.md#getSelectionContent) | 获取选中文本的内容。使用Promise异步回调。需在 [on('selectionCompleted')](arkts-basicservices-selectionmanager-onselectioncompleted-f-sys.md#on_selectionCompleted) 回调中调用，且仅在划词完成事件触发后有效。 |
| [off_selectionCompleted](arkts-basicservices-selectionmanager-offselectioncompleted-f-sys.md#off_selectionCompleted) | 取消订阅划词完成事件，与 [on('selectionCompleted')](arkts-basicservices-selectionmanager-onselectioncompleted-f-sys.md#on_selectionCompleted) 搭配使用。 |
| [on_selectionCompleted](arkts-basicservices-selectionmanager-onselectioncompleted-f-sys.md#on_selectionCompleted) | 订阅划词完成事件，与 [off('selectionCompleted')](arkts-basicservices-selectionmanager-offselectioncompleted-f-sys.md#off_selectionCompleted) 搭配使用取消订阅。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [Panel](arkts-basicservices-selectionmanager-panel-i.md) | 划词面板对象，通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)创建，提供面板内容设置、显示、隐藏、移动及事件订阅等管理能力，适用于在划词完成后向用户展示自定义操作界面的场景。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Panel](arkts-basicservices-selectionmanager-panel-i-sys.md) | 划词面板对象，通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f-sys.md#createPanel（系统接口）)创建，提供面板内容设置、显示、隐藏、移动及事件订阅等管理能力，适用于在划词完成后向用户展示自定义操作界面的场景。 |
| [SelectionInfo](arkts-basicservices-selectionmanager-selectioninfo-i-sys.md) | 划词事件信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SelectionType](arkts-basicservices-selectionmanager-selectiontype-e-sys.md) | 定义划词方式枚举值。 \| 名称 \| 值 \| 说明 \| \| ------------ \| -- \| ------------------ \| \| MOUSE_MOVE \| 1 \| 鼠标或触控板滑动划词。 \| \| DOUBLE_CLICK \| 2 \| 鼠标或触控板双击划词。 \| \| TRIPLE_CLICK \| 3 \| 鼠标或触控板三击划词。 \| |
<!--DelEnd-->

