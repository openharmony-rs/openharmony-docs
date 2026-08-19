# WindowAnimationController（系统接口）

窗口动画控制器。在创建一个WindowAnimationController对象时，需要实现其中的所有回调函数。

**起始版本：** 23

<!--Device-windowAnimationManager-export interface WindowAnimationController--><!--Device-windowAnimationManager-export interface WindowAnimationController-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { windowAnimationManager } from '@kit.ArkUI';
```

## onAppTransition

```TypeScript
onAppTransition(fromWindowTarget: WindowAnimationTarget, toWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

应用转场时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onAppTransition(fromWindowTarget: WindowAnimationTarget, toWindowTarget: WindowAnimationTarget,      finishCallback: WindowAnimationFinishedCallback): void--><!--Device-WindowAnimationController-onAppTransition(fromWindowTarget: WindowAnimationTarget, toWindowTarget: WindowAnimationTarget,      finishCallback: WindowAnimationFinishedCallback): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fromWindowTarget | WindowAnimationTarget | 是 | 转场前的动画窗口。 |
| toWindowTarget | WindowAnimationTarget | 是 | 转场后的动画窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调。 |

**示例**

请参考windowAnimationManager.setController的示例代码。

## onCloseWindow

```TypeScript
onCloseWindow(closingWindowTarget: WindowAnimationTarget, finishCallback: WindowAnimationFinishedCallback): void
```

关闭窗口时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onCloseWindow(closingWindowTarget: WindowAnimationTarget, finishCallback: WindowAnimationFinishedCallback): void--><!--Device-WindowAnimationController-onCloseWindow(closingWindowTarget: WindowAnimationTarget, finishCallback: WindowAnimationFinishedCallback): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| closingWindowTarget | WindowAnimationTarget | 是 | 动画目标窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调。 |

**示例**

请参考windowAnimationManager.setController的示例代码。

## onMinimizeWindow

```TypeScript
onMinimizeWindow(minimizingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

最小化窗口时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onMinimizeWindow(minimizingWindowTarget: WindowAnimationTarget,      finishCallback: WindowAnimationFinishedCallback): void--><!--Device-WindowAnimationController-onMinimizeWindow(minimizingWindowTarget: WindowAnimationTarget,      finishCallback: WindowAnimationFinishedCallback): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minimizingWindowTarget | WindowAnimationTarget | 是 | 动画目标窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调。 |

**示例**

请参考windowAnimationManager.setController的示例代码。

## onScreenUnlock

```TypeScript
onScreenUnlock(finishCallback: WindowAnimationFinishedCallback): void
```

屏幕解锁时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onScreenUnlock(finishCallback: WindowAnimationFinishedCallback): void--><!--Device-WindowAnimationController-onScreenUnlock(finishCallback: WindowAnimationFinishedCallback): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调。 |

## onStartAppFromLauncher

```TypeScript
onStartAppFromLauncher(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

从桌面启动应用时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onStartAppFromLauncher(startingWindowTarget: WindowAnimationTarget,      finishCallback: WindowAnimationFinishedCallback): void--><!--Device-WindowAnimationController-onStartAppFromLauncher(startingWindowTarget: WindowAnimationTarget,      finishCallback: WindowAnimationFinishedCallback): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startingWindowTarget | WindowAnimationTarget | 是 | 动画目标窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调。 |

**示例**

请参考windowAnimationManager.setController的示例代码。

## onStartAppFromOther

```TypeScript
onStartAppFromOther(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

从除了桌面和最近任务列表以外其他地方启动应用时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onStartAppFromOther(startingWindowTarget: WindowAnimationTarget,      finishCallback: WindowAnimationFinishedCallback): void--><!--Device-WindowAnimationController-onStartAppFromOther(startingWindowTarget: WindowAnimationTarget,      finishCallback: WindowAnimationFinishedCallback): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startingWindowTarget | WindowAnimationTarget | 是 | 动画目标窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调 |

**示例**

请参考windowAnimationManager.setController的示例代码。

## onStartAppFromRecent

```TypeScript
onStartAppFromRecent(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

从最近任务列表启动应用时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onStartAppFromRecent(startingWindowTarget: WindowAnimationTarget,      finishCallback: WindowAnimationFinishedCallback): void--><!--Device-WindowAnimationController-onStartAppFromRecent(startingWindowTarget: WindowAnimationTarget,      finishCallback: WindowAnimationFinishedCallback): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startingWindowTarget | WindowAnimationTarget | 是 | 动画目标窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调。 |

**示例**

请参考windowAnimationManager.setController的示例代码。

## onWindowAnimationTargetsUpdate

```TypeScript
onWindowAnimationTargetsUpdate(fullScreenWindowTarget: WindowAnimationTarget,
      floatingWindowTargets: Array<WindowAnimationTarget>): void
```

动画目标窗口更新时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onWindowAnimationTargetsUpdate(fullScreenWindowTarget: WindowAnimationTarget,      floatingWindowTargets: Array<WindowAnimationTarget>): void--><!--Device-WindowAnimationController-onWindowAnimationTargetsUpdate(fullScreenWindowTarget: WindowAnimationTarget,      floatingWindowTargets: Array<WindowAnimationTarget>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullScreenWindowTarget | WindowAnimationTarget | 是 | 全屏状态的动画目标窗口。 |
| floatingWindowTargets | Array&lt;WindowAnimationTarget&gt; | 是 | 悬浮状态的动画目标窗口。 |

**示例**

请参考windowAnimationManager.setController的示例代码。

## onAppTransition

```TypeScript
onAppTransition?: AppTransitionCallback
```

应用转场时的回调。

**类型：** [AppTransitionCallback](arkts-arkui-windowanimationmanager-apptransitioncallback-t-sys.md)

**起始版本：** 23

<!--Device-WindowAnimationController-onAppTransition?: AppTransitionCallback--><!--Device-WindowAnimationController-onAppTransition?: AppTransitionCallback-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## onCloseWindow

```TypeScript
onCloseWindow?: WindowCloseCallback
```

关闭窗口时的回调。

**类型：** [WindowCloseCallback](arkts-arkui-windowanimationmanager-windowclosecallback-t-sys.md)

**起始版本：** 23

<!--Device-WindowAnimationController-onCloseWindow?: WindowCloseCallback--><!--Device-WindowAnimationController-onCloseWindow?: WindowCloseCallback-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## onMinimizeWindow

```TypeScript
onMinimizeWindow?: WindowMinimizationCallback
```

最小化窗口时的回调。

**类型：** [WindowMinimizationCallback](arkts-arkui-windowanimationmanager-windowminimizationcallback-t-sys.md)

**起始版本：** 23

<!--Device-WindowAnimationController-onMinimizeWindow?: WindowMinimizationCallback--><!--Device-WindowAnimationController-onMinimizeWindow?: WindowMinimizationCallback-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## onScreenUnlock

```TypeScript
onScreenUnlock?: ScreenUnlockCallback
```

屏幕解锁时的回调。

**类型：** [ScreenUnlockCallback](arkts-arkui-windowanimationmanager-screenunlockcallback-t-sys.md)

**起始版本：** 23

<!--Device-WindowAnimationController-onScreenUnlock?: ScreenUnlockCallback--><!--Device-WindowAnimationController-onScreenUnlock?: ScreenUnlockCallback-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## onStartAppFromLauncher

```TypeScript
onStartAppFromLauncher?: AppStartCallback
```

从桌面启动应用时的回调。

**类型：** [AppStartCallback](arkts-arkui-windowanimationmanager-appstartcallback-t-sys.md)

**起始版本：** 23

<!--Device-WindowAnimationController-onStartAppFromLauncher?: AppStartCallback--><!--Device-WindowAnimationController-onStartAppFromLauncher?: AppStartCallback-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## onStartAppFromOther

```TypeScript
onStartAppFromOther?: AppStartCallback
```

从除了桌面和最近任务列表以外其他地方启动应用时的回调。

**类型：** [AppStartCallback](arkts-arkui-windowanimationmanager-appstartcallback-t-sys.md)

**起始版本：** 23

<!--Device-WindowAnimationController-onStartAppFromOther?: AppStartCallback--><!--Device-WindowAnimationController-onStartAppFromOther?: AppStartCallback-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## onStartAppFromRecent

```TypeScript
onStartAppFromRecent?: AppStartCallback
```

从最近任务列表启动应用时的回调。

**类型：** [AppStartCallback](arkts-arkui-windowanimationmanager-appstartcallback-t-sys.md)

**起始版本：** 23

<!--Device-WindowAnimationController-onStartAppFromRecent?: AppStartCallback--><!--Device-WindowAnimationController-onStartAppFromRecent?: AppStartCallback-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## onWindowAnimationTargetsUpdate

```TypeScript
onWindowAnimationTargetsUpdate?: WindowAnimationTargetsUpdationCallback
```

动画目标窗口更新时的回调。

**类型：** [WindowAnimationTargetsUpdationCallback](arkts-arkui-windowanimationmanager-windowanimationtargetsupdationcallback-t-sys.md)

**起始版本：** 23

<!--Device-WindowAnimationController-onWindowAnimationTargetsUpdate?: WindowAnimationTargetsUpdationCallback--><!--Device-WindowAnimationController-onWindowAnimationTargetsUpdate?: WindowAnimationTargetsUpdationCallback-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

