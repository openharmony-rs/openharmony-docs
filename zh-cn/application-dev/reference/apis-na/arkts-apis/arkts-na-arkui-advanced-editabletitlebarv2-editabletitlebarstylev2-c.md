# EditableTitleBarStyleV2

标题栏样式配置类，使用@ObservedV2装饰器，支持状态观察。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class EditableTitleBarStyleV2--><!--Device-unnamed-export declare class EditableTitleBarStyleV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(options?: EditableTitleBarStyleV2Options)
```

EditableTitleBarStyleV2的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarStyleV2-constructor(options?: EditableTitleBarStyleV2Options)--><!--Device-EditableTitleBarStyleV2-constructor(options?: EditableTitleBarStyleV2Options)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EditableTitleBarStyleV2Options](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarstylev2options-i.md) | 否 | 标题栏样式配置选项。 |

## backgroundBlurStyle

```TypeScript
@Trace
  public backgroundBlurStyle?: BlurStyle
```

标题栏背景模糊样式。 默认值：BlurStyle.NONE，表示无模糊效果。

**类型：** BlurStyle

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarStyleV2-@Trace  public backgroundBlurStyle?: BlurStyle--><!--Device-EditableTitleBarStyleV2-@Trace  public backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
@Trace
  public backgroundColor?: ResourceColor
```

标题栏背景色。 默认值：'#00000000'，表示背景透明。

**类型：** ResourceColor

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarStyleV2-@Trace  public backgroundColor?: ResourceColor--><!--Device-EditableTitleBarStyleV2-@Trace  public backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentMargin

```TypeScript
@Trace
  public contentMargin?: LocalizedMargin
```

标题栏外边距，不支持设置负数。 默认值： { start: LengthMetrics.resource(\$r('sys.float.margin_left')), end: LengthMetrics.resource(\$r('sys.float.margin_right')) }。

**类型：** LocalizedMargin

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarStyleV2-@Trace  public contentMargin?: LocalizedMargin--><!--Device-EditableTitleBarStyleV2-@Trace  public contentMargin?: LocalizedMargin-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## safeAreaEdges

```TypeScript
@Trace
  public safeAreaEdges?: Array<SafeAreaEdge>
```

扩展安全区域的方向。 默认值：[SafeAreaEdge.TOP]。

**类型：** Array&lt;SafeAreaEdge&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarStyleV2-@Trace  public safeAreaEdges?: Array<SafeAreaEdge>--><!--Device-EditableTitleBarStyleV2-@Trace  public safeAreaEdges?: Array<SafeAreaEdge>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## safeAreaTypes

```TypeScript
@Trace
  public safeAreaTypes?: Array<SafeAreaType>
```

扩展安全区域的类型。 默认值：[SafeAreaType.SYSTEM]。

**类型：** Array&lt;SafeAreaType&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleBarStyleV2-@Trace  public safeAreaTypes?: Array<SafeAreaType>--><!--Device-EditableTitleBarStyleV2-@Trace  public safeAreaTypes?: Array<SafeAreaType>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

