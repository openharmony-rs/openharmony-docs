# WindowAnimationController（系统接口）

窗口动画控制器。在创建一个WindowAnimationController对象时，需要实现其中的所有回调函数。

**起始版本：** 9

<!--Device-windowAnimationManager-export interface WindowAnimationController--><!--Device-windowAnimationManager-export interface WindowAnimationController-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { windowAnimationManager } from '@kit.ArkUI';
```

<a id="onapptransition"></a>
## onAppTransition

```TypeScript
onAppTransition(fromWindowTarget: WindowAnimationTarget, toWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

应用转场时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onAppTransition(fromWindowTarget: WindowAnimationTarget, toWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void--><!--Device-WindowAnimationController-onAppTransition(fromWindowTarget: WindowAnimationTarget, toWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fromWindowTarget | [WindowAnimationTarget](../arkts-components/arkts-arkui-windowanimationtarget-i-sys.md) | 是 | 转场前的动画窗口。 |
| toWindowTarget | [WindowAnimationTarget](../arkts-components/arkts-arkui-windowanimationtarget-i-sys.md) | 是 | 转场后的动画窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调。 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

<a id="onclosewindow"></a>
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
| closingWindowTarget | [WindowAnimationTarget](../arkts-components/arkts-arkui-windowanimationtarget-i-sys.md) | 是 | 动画目标窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调。 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

<a id="onminimizewindow"></a>
## onMinimizeWindow

```TypeScript
onMinimizeWindow(minimizingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

最小化窗口时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onMinimizeWindow(minimizingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void--><!--Device-WindowAnimationController-onMinimizeWindow(minimizingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minimizingWindowTarget | [WindowAnimationTarget](../arkts-components/arkts-arkui-windowanimationtarget-i-sys.md) | 是 | 动画目标窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调。 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

<a id="onscreenunlock"></a>
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

<a id="onstartappfromlauncher"></a>
## onStartAppFromLauncher

```TypeScript
onStartAppFromLauncher(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

从桌面启动应用时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onStartAppFromLauncher(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void--><!--Device-WindowAnimationController-onStartAppFromLauncher(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startingWindowTarget | [WindowAnimationTarget](../arkts-components/arkts-arkui-windowanimationtarget-i-sys.md) | 是 | 动画目标窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调。 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

<a id="onstartappfromother"></a>
## onStartAppFromOther

```TypeScript
onStartAppFromOther(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

从除了桌面和最近任务列表以外其他地方启动应用时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onStartAppFromOther(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void--><!--Device-WindowAnimationController-onStartAppFromOther(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startingWindowTarget | [WindowAnimationTarget](../arkts-components/arkts-arkui-windowanimationtarget-i-sys.md) | 是 | 动画目标窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

<a id="onstartappfromrecent"></a>
## onStartAppFromRecent

```TypeScript
onStartAppFromRecent(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void
```

从最近任务列表启动应用时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onStartAppFromRecent(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void--><!--Device-WindowAnimationController-onStartAppFromRecent(startingWindowTarget: WindowAnimationTarget,
      finishCallback: WindowAnimationFinishedCallback): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startingWindowTarget | [WindowAnimationTarget](../arkts-components/arkts-arkui-windowanimationtarget-i-sys.md) | 是 | 动画目标窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调。 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

<a id="onwindowanimationtargetsupdate"></a>
## onWindowAnimationTargetsUpdate

```TypeScript
onWindowAnimationTargetsUpdate(fullScreenWindowTarget: WindowAnimationTarget,
      floatingWindowTargets: Array<WindowAnimationTarget>): void
```

动画目标窗口更新时的回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowAnimationController-onWindowAnimationTargetsUpdate(fullScreenWindowTarget: WindowAnimationTarget,
      floatingWindowTargets: Array<WindowAnimationTarget>): void--><!--Device-WindowAnimationController-onWindowAnimationTargetsUpdate(fullScreenWindowTarget: WindowAnimationTarget,
      floatingWindowTargets: Array<WindowAnimationTarget>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullScreenWindowTarget | [WindowAnimationTarget](../arkts-components/arkts-arkui-windowanimationtarget-i-sys.md) | 是 | 全屏状态的动画目标窗口。 |
| floatingWindowTargets | Array&lt;WindowAnimationTarget&gt; | 是 | 悬浮状态的动画目标窗口。 |

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

