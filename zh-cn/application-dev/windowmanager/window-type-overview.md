# 窗口类型开发概述

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4; @qinliwen0417-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

窗口分为系统窗口、应用窗口两种类型。

## 系统窗口

系统窗口指完成系统特定功能的窗口。如音量条、壁纸、通知栏、状态栏、导航栏等。<!--Del-->具体可见WindowType。<!--DelEnd-->

## 应用窗口

应用窗口区别于系统窗口，指与应用显示相关的窗口，用来显示应用的内容。根据管理方式和用途的不同，应用窗口又可以分为主窗口、辅助窗口两种。

### 主窗口

主窗口由UIAbility创建时默认创建，会在“任务管理界面”中以一个独立的任务卡片显示，用于显示应用UIAbility主界面。

### 辅助窗口

辅助窗口由应用自行管理创建和销毁，不会在“任务管理界面”中以一个独立的任务卡片显示，可以用于显示应用的辅助内容，例如弹窗等。

辅助窗口包括：

- 子窗口  

  Stage模型下通过createSubWindow()或createSubWindowWithOptions()接口创建。具体可见子窗口开发指导。

  当使用createSubWindowWithOptions()接口配置zLevelAboveParentLoosened属性为true时，创建得到的子窗称为独立子窗。

- 全局悬浮窗（即WindowType.TYPE_FLOAT），具体可见全局悬浮窗开发指导。

- 模态窗口（即WindowType.TYPE_DIALOG），具体可见模态窗口开发指导。

- 画中画

- 闪控球

- 闪控窗