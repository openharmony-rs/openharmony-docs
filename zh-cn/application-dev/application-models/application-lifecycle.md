# 应用生命周期

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

## 概述

在应用开发过程中，理解组件生命周期、应用进程生命周期以及它们之间的关系对于构建稳定、高效的应用至关重要。本文档将帮助开发者理解：

- [组件与应用进程的前后台关系](#组件与应用进程前后台关系)
- [应用进程前后台切换的时机](#应用进程前后台切换时机)
- [如何监听应用进程状态变化](#监听应用进程状态变化)
- [组件销毁与应用进程销毁的关系](#组件销毁与应用进程销毁的关系)

通过掌握这些知识，开发者可以更好地进行资源管理、性能优化和多组件协同开发。

## 组件与应用进程前后台关系

[UIAbility组件生命周期](./uiability-lifecycle.md)的前后台回调与进程的前后台状态密切相关，但二者并非完全等同：

- UIAbility的[onForeground()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onforeground)回调表示该UIAbility实例切换至前台状态。
- 进程状态的前后台表示整个进程的前后台状态。
- 一个进程可能包含多个UIAbility，其中某个UIAbility的`onForeground()`不一定意味着进程状态发生改变（例如，进程可能已处于前台状态）。

UIAbility状态和进程状态的对应关系如下（假设进程内有两个UIAbility组件）：
| UIAbility状态 | 进程内窗口状态 | 进程状态 |
| --------- | --------- | ------------------------------ |
| 任一UIAbility处于前台状态 | 可见状态 | 前台状态 |
| 任一UIAbility处于前台状态 | 不可见状态 | 前台状态 |
| 所有UIAbility处于后台状态 | 可见状态 | 前台状态 |
| 所有UIAbility处于后台状态 | 不可见状态 | 后台状态 |

## 应用进程前后台切换时机

系统对后台进程施加了诸多限制，例如，后台状态下不允许启动UIAbility组件，且后台进程会被冻结。了解应用进程的前后台切换时机，有助于开发者更好地组织代码，避免被系统拦截。

### 切换到前台的时机

- 应用进程内首个UIAbility启动时，系统会将应用进程切换到前台状态。
- 在应用已处于后台状态前提下，用户从多任务界面点击任务将应用切换到前台状态。
- 用户从其他应用返回到已处于后台状态下的应用时，系统会将应用进程切换到前台状态。
- 解锁锁屏界面并返回到锁屏前显示的应用时，系统会将该应用进程切换到前台状态。

### 切换到后台的时机

- 用户从应用进程返回到桌面时，系统会将应用进程切换到后台状态。
- 用户切换到其他应用时，系统会将应用进程切换到后台状态。
- 屏幕锁屏时，系统会将正在显示的应用进程切换到后台状态。

> **说明：**
>
> 上述应用进程前后台的切换时机不包含2in1应用，2in1应用仅在启动时被系统切换到前台状态，退出时被系统切换到后台状态。

## 监听应用进程状态变化

系统提供了多种监听应用进程状态的接口，开发者可以根据需要监听应用的前后台状态、UIAbility组件生命周期、全部应用程序状态和指定应用程序状态变化。

### 监听应用前后台变化

使用`ApplicationContext`的[on('applicationStateChange')](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextonapplicationstatechange10)方法可以监听应用的前后台状态变化，详见[监听应用前后台变化](./application-context-stage.md#监听应用前后台变化)。

### 监听UIAbility组件生命周期变化

使用`ApplicationContext`的[on('abilityLifecycle')](../reference/apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextonabilitylifecycle)方法可以监听UIAbility的生命周期变化，详见[监听UIAbility生命周期变化](./application-context-stage.md#监听uiability生命周期变化)。

### 监听应用程序状态变化

使用[on('applicationState')](../reference/apis-ability-kit/js-apis-app-ability-appManager.md#appmanageronapplicationstate14)方法可以实现全部应用的状态监听；使用[on('applicationState')](../reference/apis-ability-kit/js-apis-app-ability-appManager.md#appmanageronapplicationstate14-1)方法可以实现指定应用的状态监听。通过实现`ApplicationStateObserver`接口，可以监听以下事件：

- [onForegroundApplicationChanged()](../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronforegroundapplicationchanged)：应用前后台状态变化。
- [onAbilityStateChanged()](../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronabilitystatechanged)：Ability状态变化。
- [onProcessCreated()](../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocesscreated)：进程创建。
- [onProcessDied()](../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocessdied)：进程销毁。
- [onProcessStateChanged()](../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocessstatechanged)：进程状态更新。

> **说明：**
>
> 上述的回调事件都是异步回调，并无严格的时序关系。

## 组件销毁与应用进程销毁的关系

进程内的所有Ability都退出后，进程才会进入销毁流程。

用户在多任务界面上滑销毁进程最后一个UIAbility时，进程会被销毁；所有UIAbility<!--Del-->、ServiceExtensionAbility、DataShareExtensionAbility<!--DelEnd-->都自动退出后，进程会被销毁。


下表展示了不同场景下组件和进程的行为：

| 场景 | 组件行为 | 进程行为 |
|------|---------|---------|
| 应用正常退出 | UIAbility.onDestroy被调用 | 进程销毁，onProcessDied被调用 |
| 用户在最近任务中滑动关闭 | UIAbility.onDestroy被调用 | 如果是最后一个UIAbility，进程会被销毁 |
| 应用切换到后台状态 | UIAbility.onBackground被调用 | 进程状态变为STATE_BACKGROUND |
| 应用返回前台状态 | UIAbility.onForeground被调用 | 进程状态变为STATE_FOREGROUND/STATE_ACTIVE |
| 多UIAbility应用关闭其中一个 | 只有被关闭的UIAbility.onDestroy被调用 | 进程不销毁（还有其他UIAbility） |
