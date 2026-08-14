# WindowInfoOptions

窗口布局信息过滤选项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-window-interface WindowInfoOptions--><!--Device-window-interface WindowInfoOptions-End-->

**系统能力：** SystemCapability.Window.SessionManager

## excludeSystemWindows

```TypeScript
excludeSystemWindows?: boolean
```

是否排除系统窗口。true表示需要排除，false表示不排除，默认为false。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WindowInfoOptions-excludeSystemWindows?: boolean--><!--Device-WindowInfoOptions-excludeSystemWindows?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

## foregroundAboveWindow

```TypeScript
foregroundAboveWindow?: int
```

需要过滤掉的不高于此窗口层级的窗口的ID。表示只返回层级高于这个窗口的窗口信息。默认值是0，表示忽略本选项；如果值小于0，返回1300016错误码；如果指定的窗口不存在，则与设置为0等价。

**类型：** int

**默认值：** 0

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WindowInfoOptions-foregroundAboveWindow?: int--><!--Device-WindowInfoOptions-foregroundAboveWindow?: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

## foregroundBelowWindow

```TypeScript
foregroundBelowWindow?: int
```

需要过滤掉的不低于此窗口层级的窗口的ID。表示只返回层级低于这个窗口的窗口信息。默认值是0，表示忽略本选项；如果值小于0，返回1300016错误码；如果指定的窗口不存在，则与设置为0等价。若同时指定 foregroundBelowWindow和foregroundAboveWindow，且两者都是有效的窗口ID，但foregroundBelowWindow指定的窗口的层级未高于foregroundAboveWindow指定 的窗口，则返回空数组。

**类型：** int

**默认值：** 0

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WindowInfoOptions-foregroundBelowWindow?: int--><!--Device-WindowInfoOptions-foregroundBelowWindow?: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

