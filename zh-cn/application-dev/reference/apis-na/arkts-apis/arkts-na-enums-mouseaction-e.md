# MouseAction

定义鼠标操作的动作类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare enum MouseAction--><!--Device-unnamed-export declare enum MouseAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Press

```TypeScript
Press = 1
```

鼠标按键按下。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseAction-Press = 1--><!--Device-MouseAction-Press = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Release

```TypeScript
Release = 2
```

鼠标按键释放。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseAction-Release = 2--><!--Device-MouseAction-Release = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Move

```TypeScript
Move = 3
```

鼠标移动。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseAction-Move = 3--><!--Device-MouseAction-Move = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Hover

```TypeScript
Hover = 4
```

鼠标悬浮。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseAction-Hover = 4--><!--Device-MouseAction-Hover = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ENTER_WINDOW

```TypeScript
ENTER_WINDOW = 4
```

鼠标进入窗口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseAction-ENTER_WINDOW = 4--><!--Device-MouseAction-ENTER_WINDOW = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LEAVE_WINDOW

```TypeScript
LEAVE_WINDOW = 5
```

鼠标离开窗口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseAction-LEAVE_WINDOW = 5--><!--Device-MouseAction-LEAVE_WINDOW = 5-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CANCEL

```TypeScript
CANCEL = 13
```

鼠标按键取消。通常在以下场景触发： 1. 组件失去焦点：当前持有焦点的组件因系统事件（如弹窗打断、应用切换）失去焦点时，会触发该动作。 2. 事件中断：鼠标操作过程中发生更高优先级事件（如系统级手势或强制回收事件流），导致当前鼠标操作被强制终止。 3. 异常状态退出：如组件销毁、渲染环境异常等场景下，未完成的鼠标事件会被标记为取消。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MouseAction-CANCEL = 13--><!--Device-MouseAction-CANCEL = 13-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

