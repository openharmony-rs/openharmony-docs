# PatternLock

图案密码锁组件，以九宫格图案的方式输入密码，用于密码验证场景。手指在PatternLock组件区域按下时开始进入输入状态，手指离开屏幕时结束输入状态完成密码输入。

> **说明：**

> - 如果开发者有其他功能需求，可以使用[自定义组件](docroot://ui/state-management/arkts-create-custom-components.md)。例如自定义组件<!--RP1-->
> [CustomPatternLock](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/UI/CustomPatternLock)
> <!--RP1End-->，通过[Canvas]{@link canvas}组件实现了图案密码锁功能，开发者可在此基础上自行进行功能扩展。

## 子组件

无

## PatternLock

```TypeScript
PatternLock(controller?: PatternLockController)
```

创建图案密码锁组件。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockInterface-(controller?: PatternLockController): PatternLockAttribute--><!--Device-PatternLockInterface-(controller?: PatternLockController): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | PatternLockController | 否 | 设置PatternLock组件控制器，可用于控制组件状态重置。 |

## 汇总

- [CircleStyleOptions](arkts-arkui-patternlock-circlestyleoptions-i.md)
- [PatternLockChallengeResult](arkts-arkui-patternlock-patternlockchallengeresult-e.md)
