# ToolbarItemStatus

工具栏单个选项的状态。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum ToolbarItemStatus--><!--Device-unnamed-export declare enum ToolbarItemStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NORMAL

```TypeScript
NORMAL = 0
```

设置工具栏单个选项为NORMAL态，该选项显示默认样式，可以触发Hover，Press，Focus事件并显示对应的多态样式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolbarItemStatus-NORMAL = 0--><!--Device-ToolbarItemStatus-NORMAL = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISABLED

```TypeScript
DISABLED = 1
```

设置工具栏单个选项为DISABLED态， 该选项显示DISABLED态样式，并且不可交互。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolbarItemStatus-DISABLED = 1--><!--Device-ToolbarItemStatus-DISABLED = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ACTIVE

```TypeScript
ACTIVE = 2
```

设置工具栏单个选项为ACTIVE态， 该选项通过点击事件可以将icon图标更新为activeIcon对应的图片资源。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolbarItemStatus-ACTIVE = 2--><!--Device-ToolbarItemStatus-ACTIVE = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

