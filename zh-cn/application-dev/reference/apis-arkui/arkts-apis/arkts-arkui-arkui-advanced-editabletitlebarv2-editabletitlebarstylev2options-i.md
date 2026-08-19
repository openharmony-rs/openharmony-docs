# EditableTitleBarStyleV2Options

标题栏样式配置选项接口。

**起始版本：** 26.0.0

<!--Device-unnamed-export declare interface EditableTitleBarStyleV2Options--><!--Device-unnamed-export declare interface EditableTitleBarStyleV2Options-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

标题栏背景模糊样式。 默认值：BlurStyle.NONE，表示无模糊效果。

**类型：** BlurStyle

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditableTitleBarStyleV2Options-backgroundBlurStyle?: BlurStyle--><!--Device-EditableTitleBarStyleV2Options-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

标题栏背景色。 默认值：'#00000000'，表示背景透明。

**类型：** ResourceColor

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditableTitleBarStyleV2Options-backgroundColor?: ResourceColor--><!--Device-EditableTitleBarStyleV2Options-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentMargin

```TypeScript
contentMargin?: LocalizedMargin
```

标题栏外边距，不支持设置负数。 默认值： { start: LengthMetrics.resource(\$r('sys.float.margin_left')), end: LengthMetrics.resource(\$r('sys.float.margin_right')) }。

**类型：** LocalizedMargin

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditableTitleBarStyleV2Options-contentMargin?: LocalizedMargin--><!--Device-EditableTitleBarStyleV2Options-contentMargin?: LocalizedMargin-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## safeAreaEdges

```TypeScript
safeAreaEdges?: Array<SafeAreaEdge>
```

扩展安全区域的方向。 默认值：[SafeAreaEdge.TOP]。

**类型：** Array&lt;SafeAreaEdge&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditableTitleBarStyleV2Options-safeAreaEdges?: Array<SafeAreaEdge>--><!--Device-EditableTitleBarStyleV2Options-safeAreaEdges?: Array<SafeAreaEdge>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## safeAreaTypes

```TypeScript
safeAreaTypes?: Array<SafeAreaType>
```

扩展安全区域的类型。 默认值：[SafeAreaType.SYSTEM]。

**类型：** Array&lt;SafeAreaType&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditableTitleBarStyleV2Options-safeAreaTypes?: Array<SafeAreaType>--><!--Device-EditableTitleBarStyleV2Options-safeAreaTypes?: Array<SafeAreaType>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

