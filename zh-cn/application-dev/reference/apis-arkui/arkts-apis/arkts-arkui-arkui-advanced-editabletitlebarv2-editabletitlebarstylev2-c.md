# EditableTitleBarStyleV2

标题栏样式配置类，使用@ObservedV2装饰器，支持状态观察。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: EditableTitleBarStyleV2Options)
```

EditableTitleBarStyleV2的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EditableTitleBarStyleV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarstylev2options-i.md) | 否 | 标题栏样式配置选项。 |

## backgroundBlurStyle

```TypeScript
public backgroundBlurStyle?: BlurStyle
```

标题栏背景模糊样式。默认值：BlurStyle.NONE。

**类型：** BlurStyle

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
public backgroundColor?: ResourceColor
```

标题栏背景色。默认值：'#00000000'。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentMargin

```TypeScript
public contentMargin?: LocalizedMargin
```

标题栏外边距，不支持设置负数。默认值：{start: LengthMetrics.resource(\$r('sys.float.margin_left')),end: LengthMetrics.resource(\$r('sys.float.margin_right'))}。

**类型：** [LocalizedMargin](arkts-arkui-localizedmargin-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## safeAreaEdges

```TypeScript
public safeAreaEdges?: Array<SafeAreaEdge>
```

扩展安全区域的方向。默认值：[SafeAreaEdge.TOP]。

**类型：** Array&lt;[SafeAreaEdge](../arkts-components/arkts-arkui-safeareaedge-e.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## safeAreaTypes

```TypeScript
public safeAreaTypes?: Array<SafeAreaType>
```

扩展安全区域的类型。默认值：[SafeAreaType.SYSTEM]。

**类型：** Array&lt;[SafeAreaType](../arkts-components/arkts-arkui-safeareatype-e.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
