# 窗口开发术语
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## WindowStage

**WindowStage**是OpenHarmony中的窗口管理器，负责管理一个UIAbility所对应的主窗口。

## Window

**Window**是OpenHarmony中的窗口实例。每个Window实例代表一个独立的窗口。

## 悬浮窗

悬浮窗分为智慧多窗悬浮窗、全局悬浮窗和[标准悬浮窗](../reference/apis-arkui/js-apis-floatView.md)。

- 智慧多窗悬浮窗是指设备屏幕上悬浮的、非全屏的应用窗口。

  一般用于在已有全屏任务运行的基础上，临时处理另一个任务，或短时间多任务并行使用。如浏览网页的同时回复消息。

  相关参考：[智慧多窗简介](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/multi-window-intro)、[智慧多窗最佳实践](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-multi-window-practice)。

- 全局悬浮窗是指一种特殊的应用辅助窗口，具备在应用主窗口和对应Ability退至后台后仍然可以在前台显示的能力。

  全局悬浮窗可以用于应用退至后台后，使用小窗继续显示UI，例如音乐应用用于显示桌面歌词等。

  应用在创建全局悬浮窗前，需要申请对应的权限。
  
  相关参考：[全局悬浮窗开发指导](global-floating-window-guide.md)。

## 自由窗口

自由窗口是一种允许用户在同一屏幕上以自由大小、位置显示的窗口状态。自由窗口支持拖拽、缩放和分屏组合，从而实现多任务处理。

自由窗口按照打开或者获取焦点的顺序在Z轴层叠排布。当自由窗口被点击或触摸时，将导致其Z轴高度提升，并获取焦点。

启动新的自由窗口时，默认以一定间距在上一个窗口的右下方层叠显示。

每个自由窗口默认会在窗口上方显示窗口标题栏，标题栏左侧显示应用图标，右侧显示三键控制按钮（窗口最大化/还原、窗口最小化和关闭窗口），且窗口标题栏支持额外的[沉浸式配置](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-multi-device-window-immersive#section359241062916)。

自由窗口可以通过拖动窗口边缘调节窗口大小，可以通过拖动标题栏移动窗口位置。

![freeformWindow](figures/freeformWindow.png)

当前设备支持情况：

-  **2in1设备**：2in1设备上的窗口，默认为自由窗口。
-  **Tablet设备**：部分Tablet设备，支持开启[自由多窗模式](#自由多窗模式)（通过下拉控制中心，点击“自由多窗”按钮开启），开启此模式后，应用窗口默认为自由窗口。
-  **Phone设备**：部分Phone设备，支持开启[自由多窗模式](#自由多窗模式)（通过下拉控制中心，点击“自由多窗”按钮开启），开启此模式后，应用窗口默认为自由窗口。

### 自由多窗模式

自由多窗模式是一种支持用户在移动设备上进行多任务处理的交互方式。

自由多窗下，允许用户在一块屏幕上同时显示多个应用窗口。此时的应用窗口为[自由窗口](#自由窗口)。

部分Tablet设备上，可通过下拉控制中心，点击“自由多窗”按钮开启自由多窗。

部分Phone设备上，可通过下拉控制中心，点击“自由多窗”按钮开启自由多窗。

![freeWindows](figures/freeWindows.png)

### 电脑模式

电脑模式是一种支持用户在移动设备上进行多任务处理的交互方式。

电脑模式下，允许用户在一块屏幕上同时显示多个应用窗口。此时的应用窗口为[自由窗口](#自由窗口)。

部分Tablet设备上，可通过下拉控制中心，点击“电脑模式”按钮开启电脑模式。

## 全局坐标系

全局坐标系是指在设备连接[扩展屏](../displaymanager/display-terminology.md#扩展屏)（多物理屏幕）的场景下，以主屏幕左上角为原点(0, 0)，屏幕右侧为x轴正方向，屏幕下侧为y轴正方向，对窗口、指针等对象的位置进行统一描述的坐标体系。

在该坐标系中，所有物理屏幕被映射到同一连续的虚拟坐标空间内，各类窗口操作、坐标转换及窗口矩形变化事件均基于该坐标空间进行计算和回调。

![global-coordinate-system](figures/global-coordinate-system.png)

使用场景：

- 窗口跨屏移动：调用基于全局坐标系的接口移动窗口，无需传递具体屏幕ID参数，即可实现窗口在多屏之间移动。
- 窗口位置变化监听：基于全局坐标系监听窗口矩形变化事件，统一获取窗口在多屏环境中的位置与尺寸变化信息。