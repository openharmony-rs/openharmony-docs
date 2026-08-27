# @ohos.selectionInput.selectionManager(划词管理)

本模块提供划词管理能力，包括创建面板、显示面板、移动面板、隐藏面板、销毁面板、监听鼠标/触控板划词事件、获取选中文本等。典型使用流程如下：
1. 调用[on('selectionCompleted')](arkts-basicservices-selectionmanager-on-f.md#onselectioncompleted)订阅划词完成事件。
2. 在回调中调用[getSelectionContent](arkts-basicservices-selectionmanager-getselectioncontent-f.md)获取选中文本。
3. 调用[createPanel](arkts-basicservices-selectionmanager-createpanel-f.md)创建划词面板。
4. 调用[setUiContent](arkts-basicservices-selectionmanager-panel-i.md#setuicontent)加载页面内容。
5. 调用[moveToGlobalDisplay](arkts-basicservices-selectionmanager-panel-i.md#movetoglobaldisplay)移动面板到指定位置。
6. 调用[show](arkts-basicservices-selectionmanager-panel-i.md#show)显示面板。
7. 调用[destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f.md)销毁面板。
8. 调用[off('selectionCompleted')](arkts-basicservices-selectionmanager-off-f.md#offselectioncompleted)取消订阅划词完成事件。

> **说明：**
> 
> - 本模块仅支持PC/2in1设备。开发者可通过canIUse('SystemCapability.SelectionInput.Selection')判断当前设备是否支持该功能。
> - 仅支持集成了划词扩展的应用调用，划词扩展的实现请参见
> [SelectionExtensionAbility](arkts-basicservices-selectioninput-selectionextensionability-selectionextensionability-c.md)。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.SelectionInput.Selection

## 导入模块

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createPanel(划词管理)](arkts-basicservices-selectionmanager-createpanel-f.md) | 创建划词面板，用于向用户展示业务相关的操作界面或文本处理结果，使用完毕后需调用[destroyPanel](arkts-basicservices-selectionmanager-destroypanel-f.md)销毁面板释放资源。使用Promise异步回调。单个划词应用仅允许创建一个[MENU_PANEL](arkts-basicservices-selectioninput-selectionpanel-paneltype-e.md)和一个 [MAIN_PANEL](arkts-basicservices-selectioninput-selectionpanel-paneltype-e.md)。 |
| [destroyPanel(划词管理)](arkts-basicservices-selectionmanager-destroypanel-f.md) | 销毁划词面板。与[createPanel](arkts-basicservices-selectionmanager-createpanel-f.md)搭配使用，用于销毁由createPanel()创建的面板对象。使用Promise异步回调。 |
| [getSelectionContent(划词管理)](arkts-basicservices-selectionmanager-getselectioncontent-f.md) | 获取选中文本的内容。使用Promise异步回调。需在 on('selectionCompleted') 回调中调用，且仅在划词完成事件触发后有效。 |
| [off(划词管理)](arkts-basicservices-selectionmanager-off-f.md#offselectioncompleted) | 取消订阅划词完成事件，与 on('selectionCompleted') 搭配使用。 |
| [on(划词管理)](arkts-basicservices-selectionmanager-on-f.md#onselectioncompleted) | 订阅划词完成事件，与 off('selectionCompleted') 搭配使用取消订阅。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Panel(划词管理)](arkts-basicservices-selectionmanager-panel-i.md) | 划词面板对象，通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f.md)创建，提供面板内容设置、显示、隐藏、移动及事件订阅等管理能力，适用于在划词完成后向用户展示自定义操作界面的场景。 |
| [SelectionInfo(划词管理)](arkts-basicservices-selectionmanager-selectioninfo-i.md) | 划词事件信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Panel(划词管理)](arkts-basicservices-selectionmanager-panel-i-sys.md) | 划词面板对象，通过[createPanel](arkts-basicservices-selectionmanager-createpanel-f.md)创建，提供面板内容设置、显示、隐藏、移动及事件订阅等管理能力，适用于在划词完成后向用户展示自定义操作界面的场景。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SelectionType(划词管理)](arkts-basicservices-selectionmanager-selectiontype-e.md) | 定义划词方式枚举值。  \| 名称 \| 值 \| 说明 \| \| ------------ \| -- \| ------------------ \| \| MOUSE_MOVE \| 1 \| 鼠标或触控板滑动划词。 \| \| DOUBLE_CLICK \| 2 \| 鼠标或触控板双击划词。 \| \| TRIPLE_CLICK \| 3 \| 鼠标或触控板三击划词。 \| |
