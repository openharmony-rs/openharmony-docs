# RemoteWindow (System API)

远程控制窗口组件，可以通过此组件控制应用窗口，提供启动退出过程中控件动画和应用窗口联动动画的能力。

## 子组件

不可以包含子组件

## RemoteWindow

```TypeScript
RemoteWindow(target: WindowAnimationTarget)
```

通过窗口动画对象创建组件。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | [WindowAnimationTarget](arkts-arkui-remotewindow-comp-windowanimationtarget-i-sys.md) | 是 | 需要控制的动画窗口的描述。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [RRect](arkts-arkui-remotewindow-comp-rrect-i-sys.md) | 圆角矩形。 |
| [WindowAnimationTarget](arkts-arkui-remotewindow-comp-windowanimationtarget-i-sys.md) | 目标窗口，用来远程控制实现动画。 |

## 示例

RemoteWindow需要接收由windowAnimationManager设置的WindowAnimationController对象传入对应窗口WindowAnimationTarget对象，可以创建一个RemoteWindowExample.ets作为示例组件将RemoteWindow组件和传入的WindowAnimationTarget对象关联封装起来。

由于RemoteWindow只能用于系统应用程序Launcher中，可以将RemoteWindowExample组件放置于Launcher的EntryView.ets页面的build函数中，编译Launcher，然后推送Launcher安装包到设备系统中运行。

```TypeScript
// WindowAnimationControllerImpl.ets 文件
import { windowAnimationManager } from '@kit.ArkUI';

export default class WindowAnimationControllerImpl implements windowAnimationManager.WindowAnimationController {
  private callback: (target: windowAnimationManager.WindowAnimationTarget) => void = () => {}

  OnTargetUpdate(callback: (target: windowAnimationManager.WindowAnimationTarget) => void)
  {
    this.callback = callback;
  }

  private NotifyTargetUpdate(target: windowAnimationManager.WindowAnimationTarget)
  {
    this.callback(target);
  }

  onStartAppFromLauncher(startingWindowTarget: windowAnimationManager.WindowAnimationTarget,
                         finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void
  {
    console.info(`remote window animation onStartAppFromLauncher`);
    this.NotifyTargetUpdate(startingWindowTarget);
    finishedCallback.onAnimationFinish();
  }

  onStartAppFromRecent(startingWindowTarget: windowAnimationManager.WindowAnimationTarget,
                       finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
    console.info(`remote window animation onStartAppFromRecent`);
    this.NotifyTargetUpdate(startingWindowTarget);
    finishedCallback.onAnimationFinish();
  }

  onStartAppFromOther(startingWindowTarget: windowAnimationManager.WindowAnimationTarget,
                      finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
    console.info(`remote window animation onStartAppFromOther`);
    this.NotifyTargetUpdate(startingWindowTarget);
    finishedCallback.onAnimationFinish();
  }

  onAppTransition(fromWindowTarget: windowAnimationManager.WindowAnimationTarget,
                  toWindowTarget: windowAnimationManager.WindowAnimationTarget,
                  finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void{
    console.info(`remote window animation onAppTransition`);
    this.NotifyTargetUpdate(fromWindowTarget);
    finishedCallback.onAnimationFinish();
  }

  onMinimizeWindow(minimizingWindowTarget: windowAnimationManager.WindowAnimationTarget,
                   finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
    console.info(`remote window animation onMinimizeWindow`);
    this.NotifyTargetUpdate(minimizingWindowTarget);
    finishedCallback.onAnimationFinish();
  }

  onCloseWindow(closingWindowTarget: windowAnimationManager.WindowAnimationTarget,
                finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
    console.info(`remote window animation onCloseWindow`);
    this.NotifyTargetUpdate(closingWindowTarget);
    finishedCallback.onAnimationFinish();
  }

  onScreenUnlock(finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
    console.info(`remote window animation onScreenUnlock`);
    finishedCallback.onAnimationFinish();
  }

  onWindowAnimationTargetsUpdate(fullScreenWindowTarget: windowAnimationManager.WindowAnimationTarget, 
                              floatingWindowTargets: Array<windowAnimationManager.WindowAnimationTarget>): void {
    console.info('onWindowAnimationTargetsUpdate, the fullScreenWindowTarget is: ' + fullScreenWindowTarget);
    console.info('onWindowAnimationTargetsUpdate, the floatingWindowTargets are: ' + floatingWindowTargets);
  }
}
```

```TypeScript
// RemoteWindowExample.ets 文件
import { windowAnimationManager } from '@kit.ArkUI';
import WindowAnimationControllerImpl from './WindowAnimationControllerImpl';

@Entry
@Component
export default struct RemoteWindowExample {
  @State target:WindowAnimationTarget | undefined = undefined // 通过windowAnimationManager获取

  aboutToAppear(): void {
    let controller: WindowAnimationControllerImpl = new WindowAnimationControllerImpl();
    windowAnimationManager.setController(controller);
    controller.OnTargetUpdate((target: windowAnimationManager.WindowAnimationTarget) => {
      this.target = target;
    });
  }

  build() {
    Column() {
      if(this.target){
        RemoteWindow(this.target)
          .scale({ x: 0.5, y: 0.5 }) // 仅用于可见效果的演示目的，正常使用须 .scale({ x: 1, y: 1 })
          .position({ x: this.getUIContext().px2vp(this.target?.windowBounds.left), y: this.getUIContext().px2vp(this.target?.windowBounds.top) })
          .width(this.getUIContext().px2vp(this.target?.windowBounds.width))
          .height(this.getUIContext().px2vp(this.target?.windowBounds.height))
      }
     }
  }
}
```
