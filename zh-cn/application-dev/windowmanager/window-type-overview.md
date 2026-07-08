# 窗口类型开发概述

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4; @qinliwen0417-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

窗口分为系统窗口、应用窗口两种类型。

## 系统窗口

系统窗口指完成系统特定功能的窗口。如音量条、壁纸、通知栏、状态栏、导航栏等。<!--Del-->具体可见[WindowType](../reference/apis-arkui/js-apis-window-sys.md#windowtype7)。<!--DelEnd-->

## 应用窗口

应用窗口区别于系统窗口，指与应用显示相关的窗口，用来显示应用的内容。根据管理方式和用途的不同，应用窗口又可以分为主窗口、辅助窗口两种。

### 主窗口

主窗口由UIAbility创建时默认创建，会在“任务管理界面”中以一个独立的任务卡片显示，用于显示应用UIAbility主界面。

### 辅助窗口

辅助窗口由应用自行管理创建和销毁，不会在“任务管理界面”中以一个独立的任务卡片显示，可以用于显示应用的辅助内容，例如弹窗等。

辅助窗口包括：

- 子窗口  

  Stage模型下通过[createSubWindow()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#createsubwindow9-1)或[createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#createsubwindowwithoptions11)接口创建。具体可见[子窗口开发指导](subwindow-guide.md)。

  当使用[createSubWindowWithOptions()](../reference/apis-arkui/arkts-apis-window-WindowStage.md#createsubwindowwithoptions11)接口配置zLevelAboveParentLoosened属性为true时，创建得到的子窗称为独立子窗。

- 全局悬浮窗（即WindowType.TYPE_FLOAT），具体可见[全局悬浮窗开发指导](global-floating-window-guide.md)。

- 模态窗口（即WindowType.TYPE_DIALOG），具体可见[模态窗口开发指导](dialog-window-guide.md)。

- [画中画](../reference/apis-arkui/js-apis-pipWindow.md)

- [闪控球](../reference/apis-arkui/js-apis-floatingBall.md)

- [闪控窗](../reference/apis-arkui/js-apis-floatView.md)