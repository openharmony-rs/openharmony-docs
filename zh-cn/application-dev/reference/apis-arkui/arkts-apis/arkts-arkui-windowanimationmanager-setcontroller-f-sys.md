# setController（系统接口）

## 导入模块

```TypeScript
import { windowAnimationManager } from '@kit.ArkUI';
```

<a id="setcontroller"></a>
## setController

```TypeScript
function setController(controller: WindowAnimationController): void
```

设置窗口动画控制器。窗口动画控制器的说明请参考[WindowAnimationController](arkts-arkui-windowanimationmanager-windowanimationcontroller-i-sys.md)。

在使用windowAnimationManager的其他接口前，需要预先调用本接口设置窗口动画控制器。

**起始版本：** 9

<!--Device-windowAnimationManager-function setController(controller: WindowAnimationController): void--><!--Device-windowAnimationManager-function setController(controller: WindowAnimationController): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | [WindowAnimationController](arkts-arkui-windowanimationmanager-windowanimationcontroller-i-sys.md) | 是 | 窗口动画的控制器。 |

**示例：**

```TypeScript
let controller: windowAnimationManager.WindowAnimationController = {
    onStartAppFromLauncher(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onStartAppFromLauncher, the startingWindowTarget is: ' + startingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onStartAppFromRecent(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onStartAppFromRecent, the startingWindowTarget is: ' + startingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onStartAppFromOther(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onStartAppFromOther, the startingWindowTarget is: ' + startingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onAppTransition(fromWindowTarget: windowAnimationManager.WindowAnimationTarget, toWindowTarget: WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onAppTransition, the fromWindowTarget is: ' + fromWindowTarget);
        console.info('onAppTransition, the toWindowTarget is: ' + toWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onMinimizeWindow(minimizingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onMinimizeWindow, the minimizingWindowTarget is: ' + minimizingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onCloseWindow(closingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onCloseWindow, the closingWindowTarget is: ' + closingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onScreenUnlock(finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onScreenUnlock called');
        finishCallback.onAnimationFinish();
    },
    onWindowAnimationTargetsUpdate(fullScreenWindowTarget: windowAnimationManager.WindowAnimationTarget, floatingWindowTargets: Array<windowAnimationManager.WindowAnimationTarget>): void {
        console.info('onWindowAnimationTargetsUpdate, the fullScreenWindowTarget is: ' + fullScreenWindowTarget);
        console.info('onWindowAnimationTargetsUpdate, the floatingWindowTargets are: ' + floatingWindowTargets);
    }
}

windowAnimationManager.setController(controller);

```

