# SmartGestureShortcutOptions

智慧手势响应行为配置对象。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface SmartGestureShortcutOptions--><!--Device-unnamed-declare interface SmartGestureShortcutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action?: GestureShortcut
```

智慧手势响应优先级。当前仅支持GestureShortcut.PRIMARY。

当未显式传入该参数或参数异常时，会清空当前组件的智慧手势响应行为配置。

**类型：** GestureShortcut

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SmartGestureShortcutOptions-action?: GestureShortcut--><!--Device-SmartGestureShortcutOptions-action?: GestureShortcut-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

当前组件是否响应智慧手势。

true表示组件响应智慧手势，false表示组件不响应智慧手势。

默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SmartGestureShortcutOptions-enabled?: boolean--><!--Device-SmartGestureShortcutOptions-enabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectable

```TypeScript
selectable?: boolean
```

组件被智慧手势操作选中后是否展示并保留选中态。

true表示显示选中框，false表示不显示选中框。

当enabled为true时，默认值为true；当enabled为false时，默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SmartGestureShortcutOptions-selectable?: boolean--><!--Device-SmartGestureShortcutOptions-selectable?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

