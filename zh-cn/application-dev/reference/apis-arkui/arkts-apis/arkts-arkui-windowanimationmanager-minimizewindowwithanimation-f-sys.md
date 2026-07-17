# minimizeWindowWithAnimation（系统接口）

## 导入模块

```TypeScript
import { windowAnimationManager } from '@kit.ArkUI';
```

## minimizeWindowWithAnimation

```TypeScript
function minimizeWindowWithAnimation(windowTarget: WindowAnimationTarget,
    callback: AsyncCallback<WindowAnimationFinishedCallback>): void
```

最小化动画目标窗口，并返回动画完成的回调。使用callback异步回调。

**起始版本：** 9

<!--Device-windowAnimationManager-function minimizeWindowWithAnimation(windowTarget: WindowAnimationTarget,
    callback: AsyncCallback<WindowAnimationFinishedCallback>): void--><!--Device-windowAnimationManager-function minimizeWindowWithAnimation(windowTarget: WindowAnimationTarget,
    callback: AsyncCallback<WindowAnimationFinishedCallback>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowTarget | [WindowAnimationTarget](../arkts-components/arkts-arkui-remote-window-windowanimationtarget-i-sys.md) | 是 | 动画目标窗口。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<WindowAnimationFinishedCallback> | 是 | 回调函数。当最小化动画目标窗口成功，err为undefined，data为获取到的WindowAnimationFinishedCallback；否则返回err.code为-1，data为undefined。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let target: windowAnimationManager.WindowAnimationTarget | null = null;
let controller: windowAnimationManager.WindowAnimationController = {
    onStartAppFromLauncher(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onStartAppFromLauncher, the startingWindowTarget is: ' + startingWindowTarget);
        target = startingWindowTarget;
        finishCallback.onAnimationFinish();
      },
    onStartAppFromRecent(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onStartAppFromRecent, the startingWindowTarget is: ' + startingWindowTarget);
        target = startingWindowTarget;
        finishCallback.onAnimationFinish();
    },
    onStartAppFromOther(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onStartAppFromOther, the startingWindowTarget is: ' + startingWindowTarget);
        target = startingWindowTarget;
        finishCallback.onAnimationFinish();
    },
    onAppTransition(fromWindowTarget: windowAnimationManager.WindowAnimationTarget, toWindowTarget: WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onAppTransition, the fromWindowTarget is: ' + fromWindowTarget);
        console.info('onAppTransition, the toWindowTarget is: ' + toWindowTarget);
        target = toWindowTarget;
        finishCallback.onAnimationFinish();
    },
    onMinimizeWindow(minimizingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onMinimizeWindow, the minimizingWindowTarget is: ' + minimizingWindowTarget);
        target = minimizingWindowTarget;
        finishCallback.onAnimationFinish();
    },
    onCloseWindow(closingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onCloseWindow, the closingWindowTarget is: ' + closingWindowTarget);
        target = closingWindowTarget;
        finishCallback.onAnimationFinish();
    },
    onScreenUnlock(finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.info('onScreenUnlock called');
        finishCallback.onAnimationFinish();
    },
    onWindowAnimationTargetsUpdate(fullScreenWindowTarget: windowAnimationManager.WindowAnimationTarget, floatingWindowTargets: Array<windowAnimationManager.WindowAnimationTarget>): void {
        console.info('onWindowAnimationTargetsUpdate, the fullScreenWindowTarget is: ' + fullScreenWindowTarget);
        console.info('onWindowAnimationTargetsUpdate, the floatingWindowTargets are: ' + floatingWindowTargets);
        target = fullScreenWindowTarget;
    }
}

windowAnimationManager.setController(controller);

let finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback;
windowAnimationManager.minimizeWindowWithAnimation(target, (err: BusinessError, data: windowAnimationManager.WindowAnimationFinishedCallback) => {
    if (err) {
        console.error('Failed to minimize the window target. Cause: ' + JSON.stringify(err));
        return;
    }
    finishedCallback = data;

    // 在收到回调后，需要开始进行窗口动画，在窗口动画结束后，调用onAnimationFinish回调
    finishedCallback.onAnimationFinish();
});

```


## minimizeWindowWithAnimation

```TypeScript
function minimizeWindowWithAnimation(windowTarget: WindowAnimationTarget): Promise<WindowAnimationFinishedCallback>
```

最小化动画目标窗口，并返回动画完成的回调。使用Promise异步回调。

**起始版本：** 9

<!--Device-windowAnimationManager-function minimizeWindowWithAnimation(windowTarget: WindowAnimationTarget): Promise<WindowAnimationFinishedCallback>--><!--Device-windowAnimationManager-function minimizeWindowWithAnimation(windowTarget: WindowAnimationTarget): Promise<WindowAnimationFinishedCallback>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowTarget | [WindowAnimationTarget](../arkts-components/arkts-arkui-remote-window-windowanimationtarget-i-sys.md) | 是 | 动画目标窗口。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<WindowAnimationFinishedCallback> | Promise对象，返回动画完成的回调。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let target: windowAnimationManager.WindowAnimationTarget | null  = null;
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

let promise: Promise<windowAnimationManager.WindowAnimationFinishedCallback> = windowAnimationManager.minimizeWindowWithAnimation(target);
promise.then((data: windowAnimationManager.WindowAnimationFinishedCallback) => {
    data.onAnimationFinish();
}).catch((err: BusinessError)=>{
    console.error('Failed to minimize the window target. Cause: ' + JSON.stringify(err));
    return;
});

```

