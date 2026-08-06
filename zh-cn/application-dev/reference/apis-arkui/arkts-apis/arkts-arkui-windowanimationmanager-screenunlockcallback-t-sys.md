# ScreenUnlockCallback（系统接口）

```TypeScript
type ScreenUnlockCallback = (finishCallback: WindowAnimationFinishedCallback) => void
```

屏幕解锁时的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-windowAnimationManager-type ScreenUnlockCallback = (finishCallback: WindowAnimationFinishedCallback) => void--><!--Device-windowAnimationManager-type ScreenUnlockCallback = (finishCallback: WindowAnimationFinishedCallback) => void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| finishCallback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 动画完成后的回调。  |

