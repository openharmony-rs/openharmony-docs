# @ohos.animation.windowAnimationManager (窗口动画管理)(系统接口)

窗口动画管理器，可以监听应用启动退出时应用的动画窗口，提供启动退出过程中控件动画和应用窗口联动动画能力。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本模块接口为系统接口。

## 导入模块

```ts
import { windowAnimationManager } from '@kit.ArkUI';
```

## windowAnimationManager.setController

setController(controller: WindowAnimationController): void

设置窗口动画控制器。窗口动画控制器的说明请参考[WindowAnimationController](#windowanimationcontroller)。

在使用windowAnimationManager的其他接口前，需要预先调用本接口设置窗口动画控制器。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| controller | [WindowAnimationController](#windowanimationcontroller) | 是 | 窗口动画的控制器。|

**示例：**

```ts
let controller: windowAnimationManager.WindowAnimationController = {
    onStartAppFromLauncher(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onStartAppFromLauncher, the startingWindowTarget is: ' + startingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onStartAppFromRecent(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onStartAppFromRecent, the startingWindowTarget is: ' + startingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onStartAppFromOther(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onStartAppFromOther, the startingWindowTarget is: ' + startingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onAppTransition(fromWindowTarget: windowAnimationManager.WindowAnimationTarget, toWindowTarget: WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onAppTransition, the fromWindowTarget is: ' + fromWindowTarget);
        console.log('onAppTransition, the toWindowTarget is: ' + toWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onMinimizeWindow(minimizingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onMinimizeWindow, the minimizingWindowTarget is: ' + minimizingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onCloseWindow(closingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onCloseWindow, the closingWindowTarget is: ' + closingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onScreenUnlock(finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onScreenUnlock called');
        finishCallback.onAnimationFinish();
    },
    onWindowAnimationTargetsUpdate(fullScreenWindowTarget: windowAnimationManager.WindowAnimationTarget, floatingWindowTargets: Array<windowAnimationManager.WindowAnimationTarget>): void {
        console.log('onWindowAnimationTargetsUpdate, the fullScreenWindowTarget is: ' + fullScreenWindowTarget);
        console.log('onWindowAnimationTargetsUpdate, the floatingWindowTargets are: ' + floatingWindowTargets);
    }
}

windowAnimationManager.setController(controller);
```

## windowAnimationManager.minimizeWindowWithAnimation

minimizeWindowWithAnimation(windowTarget: WindowAnimationTarget, callback: AsyncCallback&lt;WindowAnimationFinishedCallback&gt;): void

最小化动画目标窗口，并返回动画完成的回调。使用callback异步回调。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| windowTarget | [WindowAnimationTarget](#windowanimationtarget) | 是 | 动画目标窗口。|
| callback | AsyncCallback&lt;[WindowAnimationFinishedCallback](#windowanimationfinishedcallback)&gt; | 是 | 回调函数。当最小化动画目标窗口成功，err为undefined，data为获取到的WindowAnimationFinishedCallback；否则返回err.code为-1，data为undefined。|

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let target: windowAnimationManager.WindowAnimationTarget | null = null;
let controller: windowAnimationManager.WindowAnimationController = {
    onStartAppFromLauncher(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onStartAppFromLauncher, the startingWindowTarget is: ' + startingWindowTarget);
        target = startingWindowTarget;
        finishCallback.onAnimationFinish();
    },
    onStartAppFromRecent(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onStartAppFromRecent, the startingWindowTarget is: ' + startingWindowTarget);
        target = startingWindowTarget;
        finishCallback.onAnimationFinish();
    },
    onStartAppFromOther(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onStartAppFromOther, the startingWindowTarget is: ' + startingWindowTarget);
        target = startingWindowTarget;
        finishCallback.onAnimationFinish();
    },
    onAppTransition(fromWindowTarget: windowAnimationManager.WindowAnimationTarget, toWindowTarget: WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onAppTransition, the fromWindowTarget is: ' + fromWindowTarget);
        console.log('onAppTransition, the toWindowTarget is: ' + toWindowTarget);
        target = toWindowTarget;
        finishCallback.onAnimationFinish();
    },
    onMinimizeWindow(minimizingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onMinimizeWindow, the minimizingWindowTarget is: ' + minimizingWindowTarget);
        target = minimizingWindowTarget;
        finishCallback.onAnimationFinish();
    },
    onCloseWindow(closingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onCloseWindow, the closingWindowTarget is: ' + closingWindowTarget);
        target = closingWindowTarget;
        finishCallback.onAnimationFinish();
    },
    onScreenUnlock(finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onScreenUnlock called');
        finishCallback.onAnimationFinish();
    },
    onWindowAnimationTargetsUpdate(fullScreenWindowTarget: windowAnimationManager.WindowAnimationTarget, floatingWindowTargets: Array<windowAnimationManager.WindowAnimationTarget>): void {
        console.log('onWindowAnimationTargetsUpdate, the fullScreenWindowTarget is: ' + fullScreenWindowTarget);
        console.log('onWindowAnimationTargetsUpdate, the floatingWindowTargets are: ' + floatingWindowTargets);
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

## windowAnimationManager.minimizeWindowWithAnimation

minimizeWindowWithAnimation(windowTarget: WindowAnimationTarget): Promise&lt;WindowAnimationFinishedCallback&gt;

最小化动画目标窗口，并返回动画完成的回调。使用Promise异步回调。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| windowTarget | [WindowAnimationTarget](#windowanimationtarget) | 是 | 动画目标窗口。|

**返回值：**

| 类型                             | 说明                                    |
| -------------------------------- | --------------------------------------- |
| Promise&lt;[WindowAnimationFinishedCallback](#windowanimationfinishedcallback)&gt; | Promise对象，返回动画完成的回调。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let target: windowAnimationManager.WindowAnimationTarget | null  = null;
let controller: windowAnimationManager.WindowAnimationController = {
    onStartAppFromLauncher(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onStartAppFromLauncher, the startingWindowTarget is: ' + startingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onStartAppFromRecent(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onStartAppFromRecent, the startingWindowTarget is: ' + startingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onStartAppFromOther(startingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onStartAppFromOther, the startingWindowTarget is: ' + startingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onAppTransition(fromWindowTarget: windowAnimationManager.WindowAnimationTarget, toWindowTarget: WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onAppTransition, the fromWindowTarget is: ' + fromWindowTarget);
        console.log('onAppTransition, the toWindowTarget is: ' + toWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onMinimizeWindow(minimizingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onMinimizeWindow, the minimizingWindowTarget is: ' + minimizingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onCloseWindow(closingWindowTarget: windowAnimationManager.WindowAnimationTarget, finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onCloseWindow, the closingWindowTarget is: ' + closingWindowTarget);
        finishCallback.onAnimationFinish();
    },
    onScreenUnlock(finishCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
        console.log('onScreenUnlock called');
        finishCallback.onAnimationFinish();
    },
    onWindowAnimationTargetsUpdate(fullScreenWindowTarget: windowAnimationManager.WindowAnimationTarget, floatingWindowTargets: Array<windowAnimationManager.WindowAnimationTarget>): void {
        console.log('onWindowAnimationTargetsUpdate, the fullScreenWindowTarget is: ' + fullScreenWindowTarget);
        console.log('onWindowAnimationTargetsUpdate, the floatingWindowTargets are: ' + floatingWindowTargets);
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

## WindowAnimationController

窗口动画控制器。在创建一个WindowAnimationController对象时，需要实现其中的所有回调函数。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 22

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ------ | ------ | ------ | ------ | ------ |
| onStartAppFromLauncher | [AppStartCallback](#appstartcallback) | 否 | 是 | 从桌面启动应用时的回调。不填该参数则无桌面启动应用动效。 |
| onStartAppFromRecent | [AppStartCallback](#appstartcallback) | 否 | 是 | 从最近任务列表启动应用时的回调。不填该参数则无最近任务列表启动应用动效。 |
| onStartAppFromOther | [AppStartCallback](#appstartcallback) | 否 | 是 | 从除了桌面和最近任务列表以外其他地方启动应用时的回调。不填该参数则无对应场景动效。 |
| onAppTransition | [AppTransitionCallback](#apptransitioncallback) | 否 | 是 | 应用转场时的回调。不填该参数则无应用间转场动效。 |
| onMinimizeWindow | [WindowMinimizationCallback](#windowminimizationcallback) | 否 | 是 | 最小化窗口时的回调。不填该参数则无最小化窗口动效。 |
| onCloseWindow | [WindowCloseCallback](#windowclosecallback) | 否 | 是 | 关闭窗口时的回调。不填该参数则无关闭窗口动效。 |
| onScreenUnlock | [ScreenUnlockCallback](#screenunlockcallback) | 否 | 是 | 屏幕解锁时的回调。不填该参数则无屏幕解锁动效。 |
| onWindowAnimationTargetsUpdate | [WindowAnimationTargetsUpdationCallback](#windowanimationtargetsupdationcallback) | 否 | 是 | 动画目标窗口更新时的回调。不填该参数则无动画目标窗口更新动效。 |

## AppStartCallback<sup>22+</sup>

type AppStartCallback = (startingWindowTarget: WindowAnimationTarget, finishCallback: WindowAnimationFinishedCallback) => void

应用启动时的回调。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名               | 类型                                                         | 必填 | 说明               |
| -------------------- | ------------------------------------------------------------ | ---- | ------------------ |
| startingWindowTarget | [WindowAnimationTarget](#windowanimationtarget)              | 是   | 动画目标窗口。     |
| finishCallback       | [WindowAnimationFinishedCallback](#windowanimationfinishedcallback) | 是   | 动画完成后的回调。 |

## AppTransitionCallback<sup>22+</sup>

type AppTransitionCallback = (fromWindowTarget: WindowAnimationTarget, toWindowTarget: WindowAnimationTarget, finishCallback: WindowAnimationFinishedCallback) => void

应用间转场时的回调。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名               | 类型                            | 必填 | 说明             |
| -------------------- | ------------------------------- | ---- | ---------------- |
| fromWindowTarget | [WindowAnimationTarget](#windowanimationtarget)           | 是   | 转场前的动画窗口。 |
| toWindowTarget       | [WindowAnimationTarget](#windowanimationtarget) | 是   | 转场后的动画窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](#windowanimationfinishedcallback) | 是   | 动画完成后的回调。 |

## WindowMinimizationCallback<sup>22+</sup>

type WindowMinimizationCallback = (minimizingWindowTarget: WindowAnimationTarget, finishCallback: WindowAnimationFinishedCallback) => void

最小化窗口时的回调。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名               | 类型                            | 必填 | 说明             |
| -------------------- | ------------------------------- | ---- | ---------------- |
| minimizingWindowTarget | [WindowAnimationTarget](#windowanimationtarget)           | 是   | 动画目标窗口。    |
| finishCallback       | [WindowAnimationFinishedCallback](#windowanimationfinishedcallback) | 是   | 动画完成后的回调。 |

## WindowCloseCallback<sup>22+</sup>

type WindowCloseCallback = (closingWindowTarget: WindowAnimationTarget, finishCallback: WindowAnimationFinishedCallback) => void

关闭窗口时的回调。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名               | 类型                            | 必填 | 说明             |
| -------------------- | ------------------------------- | ---- | ---------------- |
| closingWindowTarget | [WindowAnimationTarget](#windowanimationtarget)           | 是   | 动画目标窗口。    |
| finishCallback       | [WindowAnimationFinishedCallback](#windowanimationfinishedcallback) | 是   | 动画完成后的回调。 |

## ScreenUnlockCallback<sup>22+</sup>

type ScreenUnlockCallback = (finishCallback: WindowAnimationFinishedCallback) => void

屏幕解锁时的回调。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名         | 类型                                                         | 必填 | 说明               |
| -------------- | ------------------------------------------------------------ | ---- | ------------------ |
| finishCallback | [WindowAnimationFinishedCallback](#windowanimationfinishedcallback) | 是   | 动画完成后的回调。 |

## WindowAnimationTargetsUpdationCallback<sup>22+</sup>

type WindowAnimationTargetsUpdationCallback = (fullScreenWindowTarget: WindowAnimationTarget, floatingWindowTargets: Array&lt;WindowAnimationTarget&gt;) => void

动画目标窗口更新时的回调。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名               | 类型                            | 必填 | 说明             |
| -------------------- | ------------------------------- | ---- | ---------------- |
| fullScreenWindowTarget | [WindowAnimationTarget](#windowanimationtarget) | 是   | 全屏状态的动画目标窗口。|
| floatingWindowTargets| Array&lt;[WindowAnimationTarget](#windowanimationtarget)&gt; | 是   | 悬浮状态的动画目标窗口。 |

## WindowAnimationFinishedCallback

动画完成后的回调。

### onAnimationFinish

onAnimationFinish(): void

结束本次动画。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

**示例：**

请参考[windowAnimationManager.setController](#windowanimationmanagersetcontroller)的示例代码。

## WindowAnimationTarget

动画目标窗口，用来实现动画。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

| 名称      | 类型     | 只读 | 可选 | 说明 |
| ------- | ------ | ------ |  ------ |----------------------- |
| bundleName  | string | 是 | 否 | 动画目标窗口所对应的包名。 |
| abilityName | string | 是 | 否 | 动画目标窗口所对应的Ability名称。 |
| windowBounds | [RRect](#rrect) | 是 | 否 | 动画目标窗口所对应的实际大小。 |
| missionId  | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 否 | 任务ID，多任务中用于与ability进行匹配。|

## RRect

圆角矩形。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 20

| 名称      | 类型     | 只读 | 可选 | 说明 |
| ------- | ------ | ------ | ------ |----------------------- |
| left  | ArkTS-Dyn: number<br>ArkTS-Sta: double | 否 | 否 | 动画目标窗口左上角相对于屏幕的横坐标。 |
| top | ArkTS-Dyn: number<br>ArkTS-Sta: double | 否 | 否 | 动画目标窗口左上角相对于屏幕的纵坐标。 |
| width | ArkTS-Dyn: number<br>ArkTS-Sta: double | 否 | 否 | 动画目标窗口的宽度大小。 |
| height | ArkTS-Dyn: number<br>ArkTS-Sta: double | 否 | 否 | 动画目标窗口的高度大小。 |
| radius | ArkTS-Dyn: number<br>ArkTS-Sta: double | 否 | 否 | 动画目标窗口的圆角大小。 |