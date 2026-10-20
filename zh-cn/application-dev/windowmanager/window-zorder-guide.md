# 窗口层级

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->

## 场景介绍

**窗口层级**是指多个窗口在屏幕上的堆叠顺序，决定窗口的前后显示关系，通常称为**Z序（ZOrder）**。

ZOrder值越大，窗口越靠前显示，能够覆盖ZOrder值较小的窗口；反之，ZOrder值较小的窗口则可能被其他窗口遮挡。

对于三方应用，无法直接修改窗口的ZOrder，但可以通过控制**zLevel**属性来间接影响子窗口的显示层级。

系统通过管理ZOrder和zLevel实现对用户界面可见性与交互优先级的控制。

本节将从基本概念、层级规则、父子窗口关系、TopMost窗口机制以及相关接口示例五个方面，系统化阐述窗口层级管理机制。

## 基本概念与层级规则

### ZOrder与zLevel

**ZOrder**表示系统内部维护的窗口堆叠顺序。数值越大，窗口越靠前。三方应用不可直接修改ZOrder。

**zLevel**表示三方应用可控制的应用内子窗口之间的相对层级，仅针对非模态子窗口有效。zLevel取值范围为[-10000, 10000]，默认值为0。zLevel越高，对应的ZOrder越大，窗口越靠前。

### 窗口zLevel层级规则

- **不同zLevel的子窗口**

  - zLevel高的窗口始终覆盖zLevel低的窗口，即使点击zLevel较低的窗口，也不会将其抬升至zLevel更高的窗口之上。

- **相同zLevel的子窗口**

  - 默认后创建的窗口层级更高。

  - 用户点击某个子窗口时，该窗口的ZOrder会被提升至同zLevel中的最高位置，实现“点击置顶”。

  - 若调用[setRaiseByClickEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setraisebyclickenabled14)接口传入false，则禁用点击抬升功能，点击时层级保持不变。

### 窗口类型层级规则

- **所有窗口类型的层级**

  系统中所有类型的窗口自上而下的层级关系如下表所示（层级由高到低）：

  | 层级（由高到低） | 窗口类别 | 说明 |
  | -------- | -------- | -------- |
  | 1 | 系统特殊窗口 | 截图、语音助手、拖拽特效、系统Toast、鼠标指针、开机动画、屏幕冻结、屏幕控制等，由系统使用，始终位于所有窗口之上。 |
  | 2 | 锁屏之上窗口 | 具备锁屏之上显示能力的窗口（如锁屏场景下的输入法窗口）。 |
  | 3 | 锁屏 | 锁屏窗口，是锁屏之上窗口与普通窗口的分界线。 |
  | 4 | 系统UI窗口 | 状态栏、导航条、面板、音量条等系统界面。 |
  | 5 | 输入法窗口 | 输入法窗口，层级动态位于触发其弹出的窗口之上。 |
  | 6 | 全局悬浮窗 | 系统悬浮窗、全局搜索、悬浮相机等，需系统权限，位于所有应用窗口之上。 |
  | 7 | 系统提醒窗口 | 来电、搜索栏、系统告警窗等。 |
  | 8 | 桌面功能窗口 | 应用启动窗、最近任务、Launcher Dock等。 |
  | 9 | 应用模态子窗 | 子窗口中层级最高的类型，遮蔽当前应用的所有窗口，仅自由多窗模式下支持。 |
  | 10 | Toast子窗 | 应用内Toast。 |
  | 11 | 文本菜单子窗 | 长按、右键等文本菜单。 |
  | 12 | Dialog子窗、模态子窗 | 窗口级模态层级，遮蔽并拦截所属主窗口的交互。 |
  | 13 | 画中画窗口、应用内悬浮窗 | 挂载在主窗口体系内的应用系统窗口，位于普通子窗之上。 |
  | 14 | 普通子窗 | 默认子窗，可通过zLevel在同应用内调节层级。 |
  | 15 | 视频子窗 | 唯一叠放在主窗口内容之下的子窗。 |
  | 16 | 应用主窗口 | 普通主窗口按激活顺序叠放；置顶主窗口（TopMost）位于其他应用主窗口之上，但仍低于系统窗口。 |
  | 17 | 桌面 | Launcher桌面窗口。 |
  | 18 | 壁纸 | 壁纸窗口，位于最底层。 |

  各层级的具体数值在不同设备形态（PC/手机/Pad）及系统版本上存在差异，上表仅描述相对层级关系。

- **相同类型窗口的层级调整**

  同类型窗口（多个主窗口、多个普通子窗）之间可通过点击或快捷键（如Alt+Tab）调整层级。

- **应用内子窗口类型的默认层级**

  系统为不同类型的子窗口分配了默认层级。优先级由高到低如下所示：

  | 窗口类型     | 创建方式 |
  | -------- | -------- |
  | 模应用子窗   | 调用[createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-Window.md#createsubwindowwithoptions12)接口，并设置子窗口参数[SubWindowOptions](../reference/apis-arkui/arkts-apis-window-i.md#subwindowoptions11)中的isModal为true，modalityType为APPLICATION_MODALITY。 |
  | Toast子窗  | 调用[showToast()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showtoast)接口，并设置showMode为TOP_MOST。 |
  | 文本菜单子窗   | 调用[showActionMenu()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#showactionmenu)接口，并设置showInSubWindow为true。 |
  | Dialog子窗 | 调用[openCustomDialog()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog12)传入dialogContent、options参数，并设置showInSubWindow为true。<br>调用[openCustomDialog()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialog12-1)传入options参数，并设置showInSubWindow为true。<br>调用[openCustomDialogWithController()](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#opencustomdialogwithcontroller18)，并设置showInSubWindow为true。 |
  | 模态子窗     | 调用[createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-Window.md#createsubwindowwithoptions12)接口，并设置子窗口参数[SubWindowOptions](../reference/apis-arkui/arkts-apis-window-i.md#subwindowoptions11)中的isModal为true，modalityType为WINDOW_MODALITY。 |
  | 普通子窗     | 调用[createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-Window.md#createsubwindowwithoptions12)接口创建的默认子窗。 |

  不同类型窗口之间不能通过点击或API调整跨越层级范围。

### 父子窗口层级规则

- 当父窗口被抬升时，其所有子窗口也会随之抬升；当子窗口被抬升时，其父窗口也会随之抬升。
- 子窗口的层级始终高于其父窗口。
- 窗口抬升可通过调用[raiseToAppTop()](../reference/apis-arkui/arkts-apis-window-Window.md#raisetoapptop14)接口或点击窗口实现。

### TopMost置顶窗口层级规则

- 在[自由窗口](window-terminology.md#freeform-window自由窗口)状态下，应用主窗口可通过调用[setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14)接口传入true将自身置于其他应用窗口之上，以实现“不被遮挡”的常驻显示效果，需合理使用，避免影响用户体验。

- 使用该接口需要申请权限ohos.permission.WINDOW_TOPMOST。

## 窗口层级控制机制汇总表


| 特性/操作 | 控制方式 | 生效范围 | 适用场景 |
| -------- | -------- | -------- | -------- |
| ZOrder | 系统管理 | 可跨应用生效 | 内部渲染顺序管理 |
| zLevel | setSubWindowZLevel()/创建窗口时设置 | 仅同应用内生效 | 子窗口层级管理 |
| 窗口置顶 | setWindowTopmost() | 可跨应用生效 | 视频、导航等常驻窗口 |
| 点击抬升 | setRaiseByClickEnabled() | 同应用内同类型子窗口之间 | 防误触、固定布局 |

## 层级相关开发场景

| 功能 | 典型场景 | 对应接口 |
| -------- | -------- | -------- |
| 设置主窗口置顶 | 用于实现将窗口置于其他应用窗口之上不被遮挡。如视频通话、导航等场景。 | [setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14) |
| 提升子窗口到顶层 | 将子窗口提升至当前应用内同类型子窗口的最顶层，只在当前应用同一个父窗口下相同zLevel值的子窗范围内生效。<br>例如，视频会议中的悬浮工具栏，主窗口是视频画面，子窗口包括聊天框、共享控制栏等。点击聊天框时，可调用raiseToAppTop()将其提升到顶层，避免被其他子窗口遮挡。 | [raiseToAppTop()](../reference/apis-arkui/arkts-apis-window-Window.md#raisetoapptop14) |
| 禁止/使能子窗点击抬升功能 | 可用于固定布局的工具面板，防止用户误操作导致层级混乱。 | [setRaiseByClickEnabled()](../reference/apis-arkui/arkts-apis-window-Window.md#setraisebyclickenabled14) |
| 获取当前应用内层级最高的窗口 | 可判断当前最前显示的窗口（可能是主窗口或子窗口），用于日志记录或状态同步等场景。 | [getLastWindow()](../reference/apis-arkui/arkts-apis-window-f.md#windowgetlastwindow9-1) |

> **说明：**
>
> - 合理设置zLevel，避免层级冲突。
>
> - TopMost功能谨慎使用，避免干扰系统多窗口体验。
>
> - 对于需要高优先级显示的关键界面，可通过[raiseToAppTop()](../reference/apis-arkui/arkts-apis-window-Window.md#raisetoapptop14)确保可见性，使用此接口前，需确保该窗口已调用showWindow()类接口（[showWindow()](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow9-1)/[showWindow(options: ShowWindowOptions)](../reference/apis-arkui/arkts-apis-window-Window.md#showwindow20)）并执行完毕。
>
> - [setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14)仅在[自由窗口](window-terminology.md#freeform-window自由窗口)状态下生效。开发者可通过[isInFreeWindowMode()](../reference/apis-arkui/arkts-apis-window-Window.md#isinfreewindowmode22)查询当前窗口是否处于自由窗口，并结合[on('freeWindowModeChange')](../reference/apis-arkui/arkts-apis-window-Window.md#onfreewindowmodechange22)事件监听器实时监听窗口模式的变化，从而准确判断何时可以安全调用[setWindowTopmost()](../reference/apis-arkui/arkts-apis-window-Window.md#setwindowtopmost14)。

## 相关实践

### 模态

### 实现应用多窗口置顶


