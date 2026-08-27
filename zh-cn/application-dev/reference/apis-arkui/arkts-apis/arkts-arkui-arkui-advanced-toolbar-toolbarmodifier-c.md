# ToolBarModifier

ToolBarModifier提供设置工具栏高度(height)、背景色(backgroundColor)、左右内边距（padding，仅在子项数量小于5个时生效）、是否显示按压态（stateEffect）的方法。

**起始版本：** 13

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ItemState, ToolBar, ToolBarOption, ToolBarOptions, ToolBarModifier } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor(backgroundColor: ResourceColor): ToolBarModifier
```

设置工具栏背景色的接口。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| backgroundColor | [ResourceColor](arkts-arkui-resourcecolor-t.md) | 是 | 工具栏背景色。默认背景色为\\$r('sys.color.ohos_id_color_toolbar_bg')。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ToolBarModifier](arkts-arkui-arkui-advanced-toolbar-toolbarmodifier-c.md) | 返回当前的ToolBarModifier对象，支持链式调用。 |

## height

```TypeScript
height(height: LengthMetrics): ToolBarModifier
```

设置工具栏高度的接口，此高度不包含分割线高度。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | 是 | 工具栏高度。工具栏高度默认为56vp（不包含分割线）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ToolBarModifier](arkts-arkui-arkui-advanced-toolbar-toolbarmodifier-c.md) | 返回当前的ToolBarModifier对象，支持链式调用。 |

## padding

```TypeScript
padding(padding: LengthMetrics): ToolBarModifier
```

设置工具栏左右内边距的接口。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| padding | [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md) | 是 | 工具栏左右内边距，仅在子项数量小于5个时生效。工具栏默认在子项数量小于5个时padding为24vp，大于等于5个时为0vp。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ToolBarModifier](arkts-arkui-arkui-advanced-toolbar-toolbarmodifier-c.md) | 返回当前的ToolBarModifier对象，支持链式调用。 |

## stateEffect

```TypeScript
stateEffect(stateEffect: boolean): ToolBarModifier
```

设置是否显示按压态效果的接口。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| stateEffect | boolean | 是 | 工具栏是否显示按压态效果。true为显示按压态效果，false为移除按压态效果，默认为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ToolBarModifier](arkts-arkui-arkui-advanced-toolbar-toolbarmodifier-c.md) | 返回当前的ToolBarModifier对象，支持链式调用。 |
