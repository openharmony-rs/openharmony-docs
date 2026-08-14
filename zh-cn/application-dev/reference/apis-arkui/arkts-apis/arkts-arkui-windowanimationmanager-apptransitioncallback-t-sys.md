# AppTransitionCallback（系统接口）

```TypeScript
type AppTransitionCallback = (fromWindowTarget: WindowAnimationTarget, toWindowTarget: WindowAnimationTarget,
    finishCallback: WindowAnimationFinishedCallback) => void
```

应用转场时的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-windowAnimationManager-type AppTransitionCallback = (fromWindowTarget: WindowAnimationTarget, toWindowTarget: WindowAnimationTarget,    finishCallback: WindowAnimationFinishedCallback) => void--><!--Device-windowAnimationManager-type AppTransitionCallback = (fromWindowTarget: WindowAnimationTarget, toWindowTarget: WindowAnimationTarget,    finishCallback: WindowAnimationFinishedCallback) => void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fromWindowTarget | WindowAnimationTarget | 是 | 转场前的动画窗口。 |
| toWindowTarget | WindowAnimationTarget | 是 | 转场后的动画窗口。 |
| finishCallback | [WindowAnimationFinishedCallback](arkts-arkui-windowanimationmanager-windowanimationfinishedcallback-i-sys.md) | 是 | 动画完成后的回调。 |

