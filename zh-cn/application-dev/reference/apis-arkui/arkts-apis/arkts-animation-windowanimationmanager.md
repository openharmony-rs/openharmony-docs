# @ohos.animation.windowAnimationManager

窗口动画管理器，可以监听应用启动退出时应用的动画窗口，提供启动退出过程中控件动画和应用窗口联动动画能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace windowAnimationManager--><!--Device-unnamed-declare namespace windowAnimationManager-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [minimizeWindowWithAnimation](arkts-arkui-windowanimationmanager-minimizewindowwithanimation-f-sys.md#minimizeWindowWithAnimation) | 最小化动画目标窗口，并返回动画完成的回调。使用callback异步回调。 |
| [minimizeWindowWithAnimation](arkts-arkui-windowanimationmanager-minimizewindowwithanimation-f-sys.md#minimizeWindowWithAnimation（系统接口）) | 最小化动画目标窗口，并返回动画完成的回调。使用Promise异步回调。 |
| [setController](arkts-arkui-windowanimationmanager-setcontroller-f-sys.md#setController) | 设置窗口动画控制器。窗口动画控制器的说明请参考[WindowAnimationController](arkts-arkui-windowanimationmanager-windowanimationcontroller-i-sys.md#WindowAnimationController（系统接口）)。 在使用windowAnimationManager的其他接口前，需要预先调用本接口设置窗口动画控制器。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [RRect](arkts-arkui-windowanimationmanager-rrect-i-sys.md) | 圆角矩形。 |
| [WindowAnimationController](arkts-arkui-windowanimationmanager-windowanimationcontroller-i-sys.md) | 窗口动画控制器。在创建一个WindowAnimationController对象时，需要实现其中的所有回调函数。 |
| [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 动画完成后的回调。 |
| [WindowAnimationTarget](arkts-arkui-windowanimationmanager-windowanimationtarget-i-sys.md) | 动画目标窗口，用来实现动画。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AppStartCallback](arkts-arkui-windowanimationmanager-appstartcallback-t-sys.md) | 应用启动时的回调。 |
| [AppTransitionCallback](arkts-arkui-windowanimationmanager-apptransitioncallback-t-sys.md) | 应用转场时的回调。 |
| [ScreenUnlockCallback](arkts-arkui-windowanimationmanager-screenunlockcallback-t-sys.md) | 屏幕解锁时的回调。 |
| [WindowAnimationTargetsUpdationCallback](arkts-arkui-windowanimationmanager-windowanimationtargetsupdationcallback-t-sys.md) | 动画目标窗口更新时的回调。 |
| [WindowCloseCallback](arkts-arkui-windowanimationmanager-windowclosecallback-t-sys.md) | 关闭窗口时的回调。 |
| [WindowMinimizationCallback](arkts-arkui-windowanimationmanager-windowminimizationcallback-t-sys.md) | 最小化窗口时的回调。 |
<!--DelEnd-->

