# AppStartCallback（系统接口）

```TypeScript
type AppStartCallback = (startingWindowTarget: WindowAnimationTarget,
    finishCallback: WindowAnimationFinishedCallback) => void
```

应用启动时的回调。

**起始版本：** 23

<!--Device-windowAnimationManager-type AppStartCallback = (startingWindowTarget: WindowAnimationTarget,    finishCallback: WindowAnimationFinishedCallback) => void--><!--Device-windowAnimationManager-type AppStartCallback = (startingWindowTarget: WindowAnimationTarget,    finishCallback: WindowAnimationFinishedCallback) => void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| startingWindowTarget | WindowAnimationTarget | 是 | 动画目标窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调。 |

