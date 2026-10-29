# WindowLifeCycleCallback（系统接口）

```TypeScript
type WindowLifeCycleCallback = (winObj: window.Window) => void
```

接收生命周期已结束的window对象的回调

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type WindowLifeCycleCallback = (winObj: window.Window) => void--><!--Device-unnamed-type WindowLifeCycleCallback = (winObj: window.Window) => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| winObj | [window.Window](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md) | 是 | 已销毁的窗口对象。 |
