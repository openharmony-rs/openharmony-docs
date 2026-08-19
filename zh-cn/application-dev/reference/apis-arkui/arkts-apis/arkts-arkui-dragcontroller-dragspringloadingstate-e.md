# DragSpringLoadingState

定义拖拽的悬停检测状态的枚举类型。 默认系统配置下，如果没有触发CANCEL，状态报告如下： 保持Hover-->500ms-->BEGIN-->100ms-->UPDATE-->100ms-->UPDATE-->100ms-->UPDATE-->100ms-->END

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-dragController-export const enum DragSpringLoadingState--><!--Device-dragController-export const enum DragSpringLoadingState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BEGIN

```TypeScript
BEGIN = 0
```

拖拽进入组件范围静止一段时间，被识别为悬停状态。此时允许进行一些悬停检测的准备操作。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragSpringLoadingState-BEGIN = 0--><!--Device-DragSpringLoadingState-BEGIN = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## UPDATE

```TypeScript
UPDATE = 1
```

拖拽已处于悬停状态，如果继续静止会定期触发UPDATE通知，以检查悬停状态。此时允许UI效果刷新以突出悬停状态。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragSpringLoadingState-UPDATE = 1--><!--Device-DragSpringLoadingState-UPDATE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## END

```TypeScript
END = 2
```

如果最后一次UPDATE通知后拖拽继续静止会进入END，整个悬停检测结束。进入END后拖拽需要移出组件范围后再次进入组件或移入组件内子组件才会重新开始悬停检测。此时应用程序可进行清理、导航或视图切换操作。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragSpringLoadingState-END = 2--><!--Device-DragSpringLoadingState-END = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CANCEL

```TypeScript
CANCEL = 3
```

拖拽进入BEGIN后，在手指/鼠标抬起、切换窗口、息屏、移出组件范围、移入组件内子组件或组件内移动超过检测阈值等场景会触发CANCEL通知，悬停检测中断。应用程序将恢复UI样式，并取消待定的导航及视图切换操作。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragSpringLoadingState-CANCEL = 3--><!--Device-DragSpringLoadingState-CANCEL = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

