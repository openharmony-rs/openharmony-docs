# @ohos.animation.windowAnimationManager

窗口动画管理器，可以监听应用启动退出时应用的动画窗口，提供启动退出过程中控件动画和应用窗口联动动画能力。

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [minimizeWindowWithAnimation](arkts-arkui-minimizewindowwithanimation-f-sys.md#minimizewindowwithanimation-1) | 最小化动画目标窗口，并返回动画完成的回调。使用callback异步回调。 |
| [minimizeWindowWithAnimation](arkts-arkui-minimizewindowwithanimation-f-sys.md#minimizewindowwithanimation-2) | 最小化动画目标窗口，并返回动画完成的回调。使用Promise异步回调。 |
| [setController](arkts-arkui-setcontroller-f-sys.md#setcontroller-1) | 设置窗口动画控制器。窗口动画控制器的说明请参考[WindowAnimationController](arkts-arkui-windowanimationcontroller-i-sys.md)。在使用windowAnimationManager的其他接口前，需要预先调用本接口设置窗口动画控制器。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [RRect](arkts-arkui-rrect-i-sys.md) | 圆角矩形。 |
| [WindowAnimationController](arkts-arkui-windowanimationcontroller-i-sys.md) | 窗口动画控制器。在创建一个WindowAnimationController对象时，需要实现其中的所有回调函数。 |
| [WindowAnimationFinishedCallback](arkts-arkui-windowanimationfinishedcallback-i-sys.md) | 动画完成后的回调。 |
| [WindowAnimationTarget](arkts-arkui-windowanimationtarget-i-sys.md) | 动画目标窗口，用来实现动画。 |
<!--DelEnd-->

