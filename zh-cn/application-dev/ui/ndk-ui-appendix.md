# UI结构化数据映射附录

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

## 控件命令参数与行为

本附录集中列出控件命令的支持组件、参数、边界规则和组件行为。完整JSON结构、命令提交方式及返回码说明见[注入控件命令](ndk-ui-command-injection.md)，下文示例仅展示`cmd`对象。

通用参数约定见[注入控件命令](ndk-ui-command-injection.md#命令使用建议)。可选字段省略时按各命令的默认行为处理；显式传入`null`会因类型校验不通过被拒绝。下文仅补充各命令的组件差异、边界行为和结果处理规则。文中的`L`表示操作时的有效内容长度，`N`表示组件当前子项数量，范围`[start, end)`包含起点，不包含终点。

### setText

**示例**

```json
{
  "type": "setText",
  "action_info": {
    "value": "示例文本"
  }
}
```

**支持组件**

| 组件                                                                                       | 行为                                                                                                                       |
| ------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| [TextInput](../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md)、[TextArea](../reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md) | 替换当前文本。                                                                                                              |
| [RichEditor](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md)           | 先请求删除现有内容，再插入新的文本Span；原有富文本样式和非文本Span不会保留，删除和插入分别遵循本附录deleteText和addText的处理规则。 |

**参数**

| 参数    | 必填 | 类型   | 说明                                       |
| ------- | ---- | ------ | ------------------------------------------ |
| value | 是   | string | 设置的文本内容；空字符串表示将内容设置为空。 |

**约束与限制**

- 文本修改仍受输入过滤、最大长度和业务变更回调影响。
- 变更前回调拒绝时，组件可以恢复原文本及光标或选区状态。

### addText

**示例**

```json
{
  "type": "addText",
  "action_info": {
    "value": "示例文本",
    "offset": 5
  }
}
```

**支持组件**

| 组件                | 行为                                                                                                                               |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| TextInput、TextArea | 省略`offset`或`offset > L`时追加到末尾；`offset < 0`时调整为0；`0 <= offset <= L`时在指定位置插入，不替换现有选区。               |
| RichEditor          | 插入位置限制在有效内容范围内，并按Span边界、预上屏文本（输入法组合输入中尚未确认上屏的文本）和Symbol等特殊内容调整，不能按普通字符串字节偏移理解。 |

**参数**

| 参数     | 必填 | 类型    | 说明                               |
| -------- | ---- | ------- | ---------------------------------- |
| value  | 是   | string  | 追加或插入的文本内容。             |
| offset | 否   | integer | 插入位置；省略时在当前内容末尾追加。 |

**约束与限制**

- `value`为空字符串时不插入内容。
- 非空内容仍受输入过滤、最大长度和业务变更回调影响。

### deleteText

**示例**

```json
{
  "type": "deleteText",
  "action_info": {
    "start": 0,
    "end": 5
  }
}
```

**支持组件**

| 组件                | 行为                                                                                          |
| ------------------- | --------------------------------------------------------------------------------------------- |
| TextInput、TextArea | 省略或传入负数的端点按0处理；端点先限制在`[0, L]`，起点大于终点时交换两端点；两端相等时不删除。 |
| RichEditor          | 执行相同的缺省值处理和端点调整，并进一步按Span边界裁剪；没有有效交集时不删除。                |

**参数**

| 参数    | 必填 | 类型    | 说明             |
| ------- | ---- | ------- | ---------------- |
| start | 否   | integer | 删除范围的起点。 |
| end   | 否   | integer | 删除范围的终点。 |

**约束与限制**

- 两端都省略得到`[0, 0)`，不表示删除全部内容。
- 清空文本使用`setText`并传入空字符串。

### selectText

**示例**

```json
{
  "type": "selectText",
  "action_info": {
    "selectionStart": 0,
    "selectionEnd": 5
  }
}
```

**支持组件**

| 组件                                                                                     | 行为                                                                                                                                                        |
| ---------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Text](../reference/apis-arkui/arkui-ts/ts-basic-components-text.md)、TextInput、TextArea | 负起点按0处理，负终点按L处理；超出范围的端点收敛到有效范围；起点大于终点时交换端点；相等端点形成空选区。                                                  |
| RichEditor                                                                               | 先判断特殊值：两个端点均为-1时，在组件有焦点且不处于预上屏输入状态时选择全部；其他情况下端点分别限制到`[0, L]`，限制后起点大于或等于终点时清除选区，不交换端点。 |

**参数**

| 参数             | 必填 | 类型    | 说明                 |
| ---------------- | ---- | ------- | -------------------- |
| selectionStart | 是   | integer | 选区起点的文本位置。 |
| selectionEnd   | 是   | integer | 选区终点的文本位置。 |

**约束与限制**

- Text：组件需要处于允许选择的状态并具有有效布局；禁用、遮挡或不支持选择的状态可能使选择请求不生效。
- RichEditor：无焦点或处于预上屏输入期间时，忽略选择请求。

### copy

**示例**

```json
{
  "type": "copy",
  "action_info": {}
}
```

**支持组件**

| 组件 | 行为 |
| ---- | ---- |
| Text、TextInput、TextArea、RichEditor | 对当前有效选区执行默认复制。 |

**参数**

无额外参数，`action_info`使用空对象。

**约束与限制**

- TextInput和TextArea：密码模式或`copyOption`为[None](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#copyoptions9)时拒绝复制；没有有效选区、选区为空或复制前业务回调拒绝时，不执行默认复制。
- Text：需要组件允许选择和复制，并且已有有效选区；组件处于不支持选择或复制的状态时不执行默认复制。
- RichEditor：复制能力被禁用、受到限制或被业务[onCopy](../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#oncopy12)回调阻止时，不执行默认复制。

### swiperSwitch

**示例**

```json
{
  "type": "swiperSwitch",
  "action_info": {
    "direction": "index",
    "index": 2
  }
}
```

**支持组件**

| 组件                                                             | 行为                                                                                                                                                         |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Swiper](../reference/apis-arkui/arkui-ts/ts-container-swiper.md) | `forward`和`backward`分别请求切换到下一项或上一项内容；启用[swipeByGroup](../reference/apis-arkui/arkui-ts/ts-container-swiper.md#displaycount22)时按`displayCount`分组切换，否则按单项切换；`0 <= index < N`时请求切换到指定项。 |

**参数**

| 参数        | 必填     | 类型    | 说明                                            |
| ----------- | -------- | ------- | ----------------------------------------------- |
| direction | 是       | string  | 切换方式，取值为`forward`、`backward`或`index`。 |
| index     | 条件必填 | integer | 目标项索引；`direction`为`index`时必填。         |

**约束与限制**

- `index < 0`或`index >= N`时，命令在组件执行阶段被拒绝。
- 循环、边界、隐藏子项、禁止滑动、子项不足两项、内容不足以滚动或正在切换时，均可能导致命令在执行阶段失败并通过完成回调返回失败结果；使用`index`模式不能绕过不可滚动状态。
- 当`direction`为`forward`或`backward`时，额外传入的`index`不参与目标选择。

### tabsSwitch

**示例**

```json
{
  "type": "tabsSwitch",
  "action_info": {
    "index": 1
  }
}
```

**支持组件**

| 组件                                                         | 行为                                                                                                                    |
| ------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| [Tabs](../reference/apis-arkui/arkui-ts/ts-container-tabs.md) | `0 <= index < N`时进入页签单击处理流程；存在子项时，`index < 0`或`index >= N`回退为0，再进入页签切换处理；没有子项时不执行切换。 |

**参数**

| 参数    | 必填 | 类型    | 说明           |
| ------- | ---- | ------- | -------------- |
| index | 是   | integer | 指定目标页签。 |

**约束与限制**

- 重复选择当前项或组件状态限制可能使页面保持不变。
- 页签单击处理或内容切换被业务逻辑拦截时，页面保持原状态。

## 控件树采集结果的字段解析

本附录提供控件树采集结果的解析说明。表中字段名和取值均为采集输出的字面值。

> **说明：**
>
> - **节点字段**描述节点在控件树中的身份、类型和层级关系，所有节点（组件节点与语法节点）均会输出，直接保存于`treeInfo`或其`$children`的节点对象顶层。
> - **组件字段**描述具体UI组件的边界、状态与属性，仅组件节点输出，按所属数据组读取：基础字段和基础交互/无障碍字段位于节点对象顶层，组件属性位于`$attrs`对象中（按`node.$attrs.xxx`读取），高阶视觉字段和高阶功能字段分别位于`advanced.visual`和`advanced.functional`对象中。
> - **保留单位**表示字段值为带单位后缀的字符串，单位后缀如px、vp、fp、%等。

### 默认字段

- **采集结果顶层字段**

采集结果本身是一个JSON对象，`schemaVersion`和`treeInfo`是它的顶层字段。

| 字段           | 值类型        | 说明                                                |
| --------------- | --------------- | ------------------------------------------------------------------- |
| schemaVersion | number        | 顶层协议版本，当前取值为1。                         |
| treeInfo      | object / null | 控件树根节点。                                    |

树中的节点分为对应具体组件的组件节点，以及不对应具体组件的语法节点（如JsView节点、[Span](../reference/apis-arkui/arkui-ts/ts-basic-components-span.md)、[ContainerSpan](../reference/apis-arkui/arkui-ts/ts-basic-components-containerspan.md)、ContentSlot、ForEach、LazyForEach、Repeat、IfElse等）。两类节点均输出以下公共字段：

- **节点公共字段**

| 字段             | 值类型 | 说明                                 |
| --------------- | -------- | ------------------------------------ |
| $ID           | number | 框架分配的整数节点ID。               |
| $type         | string | 框架节点类型。                       |
| type            | string | 节点类型编码：custom表示JsView节点，build-in表示内置节点。 |
| $children     | array  | 子节点对象数组；仅在节点有子节点且非内容边界组件时输出。 |

组件节点额外输出以下字段：

- **组件基础字段**

| 字段             | 值类型 | 说明 |
| --------------- | -------- | ---- |
| $rect           | string | 节点应用变换后相对窗口的边界，坐标单位为px，以窗口左上角为原点，形式为`[left, top],[right, bottom]`，不是数值数组，也不是`[x, y, width, height]`。 |
| compid          | string | 应用设置的组件字符串标识。 |
| active          | string | 节点激活状态，取值为"false"；节点处于激活状态时不输出该字段。 |
| visible         | string | 节点自身可见性状态，取值为"false"；节点可见时不输出该字段。 |
| opacity         | number | 节点透明度，不包含祖先透明度的累计值；仅在已设置且不等于1.0时输出。 |
| backgroundColor | string | 节点背景颜色字符串；仅在已设置背景颜色时输出。 |
| $attrs          | object | 组件默认属性和采集属性。 |
| advanced        | object | 高阶视觉属性和高阶功能属性。高阶视觉字段和高阶功能字段采集均未开启时不输出该字段；内容边界组件（[Web](../reference/apis-arkweb/arkts-basic-components-web.md)<!--Del-->、[UIExtensionComponent](../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md)<!--DelEnd-->、[XComponent](../reference/apis-arkui/arkui-ts/ts-basic-components-xcomponent.md)等）的节点不输出该字段。 |

- **`$attrs`中的默认属性字段**

滚动组件（[Scroll](../reference/apis-arkui/arkui-ts/ts-container-scroll.md)、[List](../reference/apis-arkui/arkui-ts/ts-container-list.md)、[Grid](../reference/apis-arkui/arkui-ts/ts-container-grid.md)和[WaterFlow](../reference/apis-arkui/arkui-ts/ts-container-waterflow.md)）在`$attrs`对象中输出以下默认属性字段：

| 字段             | 值类型 | 说明                                                                                |
| ----------------- | -------- | ------------------------------------------------------------------------------------- |
| isScrollable    | string | 滚动方向和边界状态编码：false（内容不可滚动）、scrollBackward（往起始端方向已到边界）、scrollForward（往末尾端方向已到边界）或scrollBidirectional（未到边界，双向均可滚动）。 |
| scrollDirection | string | vertical或horizontal，表示组件滚动方向。                                            |

### 交互信息字段

设置[OH_ArkUI_NativeModule_UIAgentTreeRequestSetInteractionInfo](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetinteractioninfo)为true后，可以采集交互信息，交互信息字段及对应含义如下。

- **基础交互信息字段**

| 字段           | 值类型  | 说明                             |
| --------------- | --------- | ---------------------------------- |
| clickable     | boolean | 节点是否可点击。true表示可点击，false表示不可点击。 |
| longClickable | boolean | 节点是否可长按。true表示可长按，false表示不可长按。 |
| focusable     | boolean | 节点是否可获得焦点。true表示可获得焦点，false表示不可获得焦点。 |
| scrollable    | boolean | 节点是否可滚动。true表示可滚动，false表示不可滚动。 |
| editable      | boolean | 节点是否可编辑。true表示可编辑，false表示不可编辑。 |

- **`$attrs`中的交互信息字段**

| 组件                                                                     | 字段           | 值类型  | 说明                                         |
| -------------------------------------------------------------------------- | --------------- | --------- | ---------------------------------------------- |
| [Toggle](../reference/apis-arkui/arkui-ts/ts-basic-components-toggle.md) | isOn          | string  | Switch开关状态，true表示开，false表示关。    |
| Swiper                                                                   | scrollAbility | string  | Swiper滚动能力，见Swiper滚动能力取值表。         |
| Swiper                                                                   | scrollAxis    | string  | 取值为horizontal（横向）或vertical（纵向）。 |
| Swiper                                                                   | isLoop        | boolean | 是否启用循环。true表示启用，false表示未启用。                               |

- **Swiper滚动能力取值表**

| 值              | 说明                   |
| ----------------- | ------------------------ |
| `forward`       | 可向下一项方向滚动。   |
| `backward`      | 可向上一项方向滚动。   |
| `bidirectional` | 可向前后两个方向滚动。 |
| `unable`        | 当前不可滚动。         |

### 无障碍信息字段

下表为无障碍信息字段详解，由[OH_ArkUI_NativeModule_UIAgentTreeRequestSetAccessibilityInfo](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetaccessibilityinfo)开关控制输出。

| 字段                  | 值类型 | 说明                 |
| ---------------------- | -------- | ---------------------- |
| accessibilityContent | string | 节点无障碍描述文本；仅在已设置无障碍文本时输出。 |

### 高阶视觉字段

下表为高阶视觉字段详解，由[OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectVisualProperties](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetcollectvisualproperties)开关控制输出。

> **说明：**
>
> - 矩形类字段的通用格式为`RectT (x, y) - [w x h]`，其中x、y为矩形左上角坐标（即left、top），w、h为矩形的宽度和高度，其他为固定字符串；四个数值均保留两位小数。例如：`RectT (10.00, 20.00) - [100.00 x 50.00]`。

- **通用几何与渲染字段**

| 字段                                                                                                       | 值类型 | 说明                                                                                                        |
| ----------------------------------------------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------- |
| FrameRect                                                                                                 | string | 节点在父布局坐标系中的布局矩形，单位为px。          |
| PaintRectWithoutTransform                                                                                 | string | 施加变换前的绘制矩形，采用父级绘制坐标，单位为px。 |
| BackgroundAlign                                                                                           | string | 背景对齐方式，格式为`Alignment (horizontal, vertical)`，horizontal和vertical保留1位小数。                   |
| BorderColor / BorderWidth                                                                                 | string | 各边边框颜色和宽度，见边框字段格式表。                                                                      |
| OuterBorderRadius / OuterBorderColor / OuterBorderWidth                                                   | string | 外边框圆角、颜色和宽度，见边框字段格式表。                                                                  |
| LinearGradient / SweepGradient / RadialGradient / BorderImageGradient                                     | object | 线性/扫描/径向/边框图片渐变，见渐变对象子字段。                                                             |
| [BlendMode](../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#blendmode11枚举说明) | number | 背景混合模式的整数枚举值。                                                                                  |
| FrontBrightness / FrontGrayScale / FrontContrast / FrontSaturate / FrontSepia                             | string | 前景亮度/灰度/对比度/饱和度/褐色效果的配置字符串，保留返回值中的单位。                                      |
| FrontHueRotate                                                                                            | number | 色相旋转配置值，单位为度（°）。                                                                            |
| FrontColorBlend / ForegroundColor                                                                         | string | 前景颜色混合值/前景颜色，例如"#FF000000"。                                                                  |
| SphericalEffect / LightUpEffect                                                                           | number | 球面效果/亮起效果参数。                                                                                     |
| PixelStretchEffect                                                                                        | string | 像素拉伸效果的多分量配置描述。                                                                              |
| DynamicLightUpRate / DynamicLightUpDegree                                                                 | number | 动态亮起效果的变化率/程度参数。                                                                             |
| LightIntensity                                                                                            | number | 光照强度。                                                                                                  |
| LightIlluminated                                                                                          | number | 受光配置的整数值。                                                                                          |
| IlluminatedBorderWidth                                                                                    | string | 受光边框宽度，保留长度单位。                                                                                |
| Bloom                                                                                                     | number | 泛光参数。                                                                                                  |

- **边框字段格式表**

| 字段                                 | 格式                                                                                           | 说明                                                       |
| -------------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------ |
| BorderColor / OuterBorderColor       | `leftColor: [<颜色>]rightColor: [<颜色>]topColor: [<颜色>]bottomColor: [<颜色>]`               | 按左、右、上、下顺序记录边框颜色。                         |
| BorderWidth / OuterBorderWidth       | `[<左边宽度>,<右边宽度>,<顶部宽度>,<底部宽度>]`                                                | 按左、右、上、下顺序记录边框宽度，保留长度单位。           |
| OuterBorderRadius / hostBorderRadius | `radiusTopLeft: <长度>radiusTopRight: <长度>radiusBottomLeft: <长度>radiusBottomRight: <长度>` | 记录四个角的圆角半径，保留长度单位；无对应值时使用`[NA]`。 |

示例：`leftColor: [#FF000000]rightColor: [#FF000000]topColor: [#FF000000]bottomColor: [#FF000000]`。

- **渐变对象子字段**

通用几何与渲染字段中的LinearGradient、SweepGradient、RadialGradient和BorderImageGradient字段，值为渐变对象，包含以下子字段：

| 字段                              | 值类型          | 说明                                                                                                                                                              |
| ---------------------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type                             | string          | linear、sweep或radial。                                                                                                                                           |
| repeating                        | boolean         | 是否重复渐变。true表示重复，false表示不重复。                                                                                                                                                    |
| colors                           | array           | 色标对象数组。                                                                                                                                                    |
| colors[].color                   | string          | 色标颜色，例如"#FFFF0000"。                                                                                                                                       |
| colors[].colorSpace              | number          | 颜色空间的整数枚举值。                                                                                                                                            |
| colors[].offset                  | string          | 色标位置，保留长度或百分比单位。                                                                                                                                  |
| colors[].hdr                     | object          | 高动态范围（High Dynamic Range，HDR）颜色信息，含red、green、blue、alpha和headRoom（参考白以上的亮度余量）分量。                                                                          |
| angle                             | number          | linear的可选角度值，单位为度（°）。                                                                                  |
| direction                         | string          | linear的可选方向，采用[GradientDirection](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#gradientdirection)枚举的字符串值。 |
| centerX / centerY                | string          | sweep或radial的可选中心X坐标/Y坐标配置，保留单位。                                                                                                                |
| startAngle / endAngle / rotation | number          | sweep的可选起始角度/终止角度/旋转值，单位均为度（°）。                                                                                                           |
| horizontalSize / verticalSize    | string          | radial的可选水平尺寸/垂直尺寸，保留单位。                                                                                                                         |
| shape / sizeType                 | number          | radial的可选形状/尺寸类型整数枚举值。                                                                                                                             |

- **文本组件字段**

| 组件                                                                                    | 字段                              | 值类型 | 说明                                               |
| ----------------------------------------------------------------------------------------- | ---------------------------------- | -------- | ---------------------------------------------------- |
| Text                                                                                    | contentRect                      | string | 组件局部坐标下的文本内容矩形，单位为px。 |
| Text                                                                                    | fontScale / fontWeightScale      | number | 当前环境字体缩放比例和字重缩放比例。               |
| Text                                                                                    | ForegroundColorStrategy          | number | 前景颜色策略整数枚举值。                           |
| Text                                                                                    | from TextEngine paragraphs_ info | object | 文本段落管理信息。参见Text段落信息子字段。 |
| TextInput、TextArea | FontColor                        | string | 文本颜色，支持组件主题颜色。                       |
| TextInput、TextArea                                                                     | textRect / contentRect           | string | 组件局部坐标下的文本矩形和内容区域矩形，单位为px。 |

- **Text段落信息子字段**

| 字段                                       | 值类型  | 说明                                    |
| ------------------------------------------- | --------- | ----------------------------------------- |
| DidExceedMaxLines                         | boolean | 是否超出最大行数。true表示超出，false表示未超出。                      |
| GetTextWidth / GetHeight                  | number  | 文本排版宽度/高度，单位为px。           |
| GetLineCount                              | number  | 排版行数。                              |
| GetLongestLine / GetLongestLineWithIndent | number  | 最长行宽/包含缩进的最长行宽，单位为px。 |

- **滚动组件字段**

本节“滚动组件”包括Scroll、List、Grid和WaterFlow。

| 字段                                   | 值类型          | 说明                                                           |
| --------------------------------------- | ----------------- | ---------------------------------------------------------------- |
| edgeEffect                            | string          | 边缘效果：NONE、SPRING或FADE。                                 |
| edgeEffectAlwaysEnabled               | boolean         | 内容大小小于组件自身时，是否仍开启滑动效果。true表示开启，false表示关闭。                |
| innerScrollBarState                   | string          | 内置滚动条显示模式：OFF、AUTO或ON。 |
| scrollBarHeight / scrollBarWidth / scrollBarStartMargin | string | 滚动条高度/宽度/起始边距，保留单位。 |
| scrollBarColor                        | string          | 滚动条颜色。                                                   |
| scrollBarMargin                       | string          | 滚动条边距，见滚动条边距格式表。 |
| fadingEdge                            | boolean         | 是否启用渐隐边缘。true表示启用，false表示未启用。                                 |
| fadingEdgeLength                      | string          | 渐隐边缘长度，保留单位。                                       |
| clipContent                           | string          | 裁剪模式：DEFAULT、CONTENT_ONLY、BOUNDARY、SAFE_AREA或CUSTOM。 |
| contentStartOffset / contentEndOffset | string / number | 公共滚动偏移配置；Scroll使用带vp单位的字符串，List使用px数值，表示内容主轴起始和结束处的预留偏移。 |
| activeRect / trackRect                | string          | 内置滚动条滑块/轨道矩形，单位为px，采用宿主节点局部布局坐标。                                 |
| touchRegion / hoverRegion             | string          | 触摸/悬停识别区域矩形；可能大于实际绘制区域，不能当作节点可见边界。                           |
| normalWidth / activeWidth / touchWidth / hoverWidth | string | 常态/活动态/触摸区/悬停区宽度，保留单位。                                       |
| shapeMode                             | string          | 形状模式：RECT（矩形）、ROUND（圆形）或DEFAULT（默认）。                           |
| padding.right / padding.left / padding.bottom       | string          | 滚动条边距字段，值为带单位的长度字符串；字段名中的点号为字面量组成部分，非嵌套路径；仅输出right、left、bottom三个方向。 |
| hostBorderRadius                      | string          | 宿主边框圆角，见边框字段格式表。                                                             |
| startReservedHeight / endReservedHeight             | string          | 滚动条起始端/结束端保留高度，保留单位。                                                       |

- **Scroll、List、ListItem和ListItemGroup字段**

| 组件                | 字段                                                         | 值类型  | 说明                                                              |
| --------------------- | ------------------------------------------------------------- | --------- | ------------------------------------------------------------------- |
| Scroll              | currentOffset                                               | number  | 主轴当前滚动偏移，单位为px，不是窗口绝对坐标。                    |
| List                | currentOffset / startMainPos / endMainPos / contentMainSize | number  | 当前主轴偏移/布局起始位置/布局结束位置/内容主轴尺寸，单位均为px。 |
| List                | lanes / laneGutter                                          | number  | 当前列数/已解析的列间距；前者为整数，后者单位为px。               |
| List                | IsAtTop / IsAtBottom / chainAnimation                       | boolean | 是否处于列表起始边界/结束边界，是否使用链式动画。true表示是，false表示否。                 |
| List                | alignListItem                                               | number  | 列表项对齐方式的整数枚举值。                                      |
| List、[ListItemGroup](../reference/apis-arkui/arkui-ts/ts-container-listitemgroup.md) | divider                                                     | object  | 分隔线对象，含strokeWidth、startMargin、endMargin和color。        |
| [ListItem](../reference/apis-arkui/arkui-ts/ts-container-listitem.md)            | curOffset / startNodeSize / endNodeSize                     | number  | 侧滑偏移/起始侧节点尺寸/结束侧节点尺寸，单位为px。                |
| ListItem            | isSelected / isHover / isPressed / isLayouted               | boolean | 是否选中/悬停/按压/已布局。true表示是，false表示否。                                       |
| ListItem            | restoredOpacity                                             | number  | 禁用时保存的恢复透明度，不是当前生效透明度或布尔开关。            |
| ListItemGroup       | headerMainSize / footerMainSize / spaceWidth                | number  | 头部/尾部主轴尺寸/间距，单位为px。                                |
| ListItemGroup       | lanes / laneGutter                                          | number  | 当前列数/列间距；前者为整数，后者单位为px。                       |
| ListItemGroup       | startHeaderPos / endFooterPos                               | number  | 头部起点/尾部终点的主轴布局位置，单位为px。                       |

- **Grid、GridItem和WaterFlow字段**

| 组件      | 字段                                                                                                | 值类型  | 说明                                                                                                                       |
| ----------- | ---------------------------------------------------------------------------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Grid      | currentOffset / contentEndPadding                                                                  | number  | 当前主轴偏移/内容末尾留白，单位为px。                                                                                      |
| Grid      | startIndex / endIndex / crossCount                                                                 | number  | 布局起始索引/结束索引/交叉轴数量，均为整数。                                                                               |
| Grid      | RowsTemplate / ColumnsTemplate                                                                     | string  | 行列模板字符串。                                                                                                           |
| Grid      | RowsGap / ColumnsGap                                                                               | string  | 行列间距，保留单位。                                                                                                       |
| Grid      | MaxCount / MinCount                                                                                | number  | 可显示的最大和最小行数或列数，均为整数。                                                                                                 |
| Grid      | CellLength                                                                                         | string  | 单元长度，使用带vp单位的字符串。                                                                                           |
| Grid      | AlignItems                                                                                         | string  | [GridItemAlignment](../reference/apis-arkui/arkui-ts/ts-container-grid.md#griditemalignment12枚举说明)的DEFAULT或STRETCH。 |
| [GridItem](../reference/apis-arkui/arkui-ts/ts-container-griditem.md)  | RowStart / RowEnd / ColumnStart / ColumnEnd                                                        | number  | 起始行、结束行、起始列和结束列整数索引。                                                                                   |
| GridItem  | isSelected / isHover / isPressed                                                                   | boolean | 是否选中/悬停/按压。true表示是，false表示否。                                                                                                       |
| GridItem  | [GridItemStyle](../reference/apis-arkui/arkui-ts/ts-container-griditem.md#griditemstyle11枚举说明) | string  | NONE或PLAIN。                                                                                                              |
| WaterFlow | RowsTemplate / ColumnsTemplate                                                                     | string  | 行列模板字符串。                                                                                                           |
| WaterFlow | ItemMinSize / ItemMaxSize                                                                          | object  | 最小和最大子项尺寸，含width和height。                                                                                      |
| WaterFlow | footerHeight                                                                                       | number  | 尾部高度，单位为px。                                                                                                       |

- **滚动条边距格式表**

| 字段                                          | 格式                                         | 说明                                                                                                                |
| ----------------------------------------------- | ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| scrollBarMargin                               | `ScrollBarMargin start: <长度>, end: <长度>` | 起始端和结束端边距，参见[ScrollBarMargin](../reference/apis-arkui/arkui-ts/ts-types.md#scrollbarmargin20对象说明)。 |
| padding.right / padding.left / padding.bottom | `<长度>`                                     | 对应方向的滚动条边距。 |

示例：`ScrollBarMargin start: 10.00vp, end: 10.00vp`。

- **ScrollBar节点字段**

独立ScrollBar组件在控件树中生成`$type`为`ScrollBar`的节点；本表为该节点输出的字段，区别于滚动组件字段表中输出在宿主节点上的内置滚动条字段。

| 字段                                                                | 值类型 | 说明                                                                        |
| -------------------------------------------------------------------- | -------- | ----------------------------------------------------------------------------- |
| Axis | string | [ScrollBar](../reference/apis-arkui/arkui-ts/ts-basic-components-scrollbar.md)的轴向：NONE、VERTICAL、HORIZONTAL或FREE；Axis为大写字段名称。 |
| outerScrollBarState                                                | string | 滚动条显示模式：OFF、AUTO或ON。 |
| childRect                                                          | string | 滚动条子节点的局部布局矩形，位置和尺寸单位为px。                            |
| activeRect / trackRect                              | string | 滚动条滑块/轨道矩形，单位为px，采用ScrollBar节点局部布局坐标。       |
| touchRegion / hoverRegion                           | string | 触摸/悬停识别区域矩形；可能大于实际绘制区域，不能当作节点可见边界。 |
| normalWidth / activeWidth / touchWidth / hoverWidth | string | 常态/活动态/触摸区/悬停区宽度，保留单位。                           |
| shapeMode                                           | string | 形状模式：RECT（矩形）、ROUND（圆形）或DEFAULT（默认，跟随主题）。                                    |
| padding.right / padding.left / padding.bottom       | string | 滚动条边距字段，值为带单位的长度字符串；字段名中的点号为字面量组成部分，非嵌套路径；仅输出right、left、bottom三个方向。 |
| hostBorderRadius                                    | string | 宿主边框圆角，见边框字段格式表。                                    |
| startReservedHeight / endReservedHeight             | string | 滚动条起始端/结束端保留高度，保留单位。                             |
| scrollBarHeight / scrollBarStartMargin              | string | 滚动条高度/起始边距，保留单位。                                     |
| scrollBarMargin                                     | string | 滚动条边距，见滚动条边距格式表。                                    |

- **Swiper、指示器与页签字段**

| 组件                                                                      | 字段                                                                                                | 值类型                     | 说明                                                                                 |
| --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------- | -------------------------------------------------------------------------------------- |
| Swiper                                                                    | currentIndex / currentFirstIndex                                                                   | number                     | 当前索引/当前首项索引。                                                              |
| Swiper                                                                    | currentOffset / fadeOffset / currentIndexOffset                                                    | number                     | 主轴当前偏移/边缘渐隐偏移/当前索引对应偏移，单位为px。                               |
| Swiper                                                                    | startMainPos / endMainPos / contentMainSize / contentCrossSize                                     | number                     | 主轴起始/结束位置/内容主轴尺寸/内容交叉轴尺寸，单位为px。                            |
| Swiper                                                                    | SwiperIndicatorType                                                                                | string                     | 当前指示器类型：DOT（圆点）、DIGIT（数字）或ARC_DOT（弧形）。                                                |
| Swiper                                                                    | TextDirection                                                                                      | number                     | 解析后的布局方向整数枚举值；Auto方向已解析为实际布局方向。                                                         |
| Swiper                                                                    | curve                                                                                              | string                     | 动画曲线描述。                                                                       |
| Swiper指示器                                                              | isHover / isPressed                                                                                 | boolean                    | 是否悬停/是否按压。true表示是，false表示否。                                                                      |
| Swiper指示器                                                              | SwiperIndicatorType                                                                                 | string                     | 指示器类型，取值同Swiper的SwiperIndicatorType。                                                                   |
| Swiper箭头                                                                | isHover / isTouch                                                                                  | boolean                    | 是否悬停/触摸。true表示是，false表示否。                                                                      |
| TabBar                                                                    | isRTL                                                                                              | boolean                    | 是否采用从右到左的布局。true表示是，false表示否。                                                             |
| TabBar                                                                    | animationCurve                                                                                      | string                     | 动画曲线描述。                                                                                                     |
| TabBar                                                                    | animationDuration                                                                                   | number                     | 动画时长，单位为ms。                                                                                               |
| TabBar                                                                    | indicator / scrollMargin                                                                           | number                     | 指示器索引/滚动边距，后者单位为px。                                                  |
| TabBar                                                                    | region                                                                                             | array                      | 页签栏渐变提示区域（TabBar边缘提示仍有未显示页签的渐变效果）状态：按各渐变区域顺序记录开关，true表示该侧开启渐变；某侧仍有未显示的页签时，对应区域为true。 |
| TabBar | Axis | string | NONE、HORIZONTAL、VERTICAL或FREE。                                                   |
| [TabContent](../reference/apis-arkui/arkui-ts/ts-container-tabcontent.md) | [SelectedMode](../reference/apis-arkui/arkui-ts/ts-container-tabcontent.md#selectedmode10枚举说明) | string                     | INDICATOR表示指示器选中样式，BOARD表示底板选中样式。                                 |

- **SheetPage字段**

SheetPage节点的字段放在advanced.visual["SheetPage Pattern"]对象中：

| 字段                                                                                                                    | 值类型          | 说明                                |
| ------------------------------------------------------------------------------------------------------------------------ | ----------------- | ------------------------------------- |
| [SheetType](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#sheettype11枚举说明)          | number          | 当前Sheet类型的整数枚举值。         |
| SheetPage Node Height                                                                                                  | number          | Sheet页面高度值，单位为px。         |
| Sheet Height [start from the bottom, KeyboardHeight = 0]                                                               | number          | 自底部起算的Sheet高度值，单位为px。   |
| SheetMaxHeight [start from the bottom, pageHeight - sheetTopSafeArea]                                                  | number          | 自底部起算的Sheet最大高度，单位为px。 |
| PopupSheet OffsetX / PopupSheet OffsetY                                                                                | number          | Sheet的X/Y偏移，单位为px。          |
| SheetMaxWidth / FitContent Height                                                                                      | number          | 最大宽度/自适应内容的高度，单位为px。 |
| SheetThemeType                                                                                                         | string          | 当前Sheet主题类型描述。             |
| currentOffset                                                                                                          | number          | 当前Sheet偏移值，单位为px。         |
| height                                                                                                                 | string          | Sheet高度配置，值为带单位后缀的字符串，保留两位小数，例如"500.00vp"；百分比以百分数输出。仅在已设置高度时输出。 |
| sheetMode        | number | Sheet高度模式的整数枚举值，取值见[SheetMode](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#sheetmode12枚举说明)；仅在已设置高度模式时输出。 |

表中含空格、方括号、等号或点号的字段名均为完整字面名称。

- **懒加载布局字段**

| 组件                                                                                          | 字段                                                                 | 值类型 | 说明                                                          |
| ----------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- | -------- | --------------------------------------------------------------- |
| [LazyColumnLayout](../reference/apis-arkui/arkui-ts/ts-container-lazycolumnlayout.md)         | headerMainSize / footerMainSize / space / totalMainSize             | number | 头部主轴尺寸/尾部主轴尺寸/间距/总主轴尺寸，单位为px。         |
| [LazyVGridLayout](../reference/apis-arkui/arkui-ts/ts-container-lazyvgridlayout.md)           | headerMainSize / footerMainSize / spaceWidth / totalMainSize        | number | 头部主轴尺寸/尾部主轴尺寸/间距/总主轴尺寸，单位为px。         |
| [LazyVWaterFlowLayout](../reference/apis-arkui/arkui-ts/ts-container-lazyvwaterflowlayout.md) | headerMainSize / footerMainSize / estimatedItemSize / totalMainSize | number | 头部主轴尺寸/尾部主轴尺寸/估算子项尺寸/总主轴尺寸，单位为px。 |

懒加载布局总尺寸可能包含估算值。

### 高阶功能字段

下表为高阶功能字段详解，由[OH_ArkUI_NativeModule_UIAgentTreeRequestSetCollectFunctionalProperties](../reference/apis-arkui/capi-ui-info-collection-h.md#oh_arkui_nativemodule_uiagenttreerequestsetcollectfunctionalproperties)开关控制输出。

- **公共配置**

| 字段               | 值类型          | 说明                                |
| ------------------- | ----------------- | ------------------------------------- |
| BackgroundImage   | string / object | 背景图片来源。                      |
| BorderImageSource | string / object | 边框图片来源。                      |
| keyboardShortcuts | array           | 快捷键对象数组，每项含value和keys。 |

- **资源引用格式表**

BackgroundImage、BorderImageSource和图片url的资源格式如下：

| 来源                                       | 值格式                             | 说明                                                                                        |
| -------------------------------------------- | ------------------------------------ | --------------------------------------------------------------------------------------------- |
| 文件、应用资源路径、网络地址或数据资源地址 | string                             | 资源地址字符串。                                                                            |
| 资源ID                                     | object：`{"id": 123}`              | 资源ID对象。                                                                                |
| 其他来源，例如PixelMap或嵌入图片数据       | object：`{"sourceType": "pixmap"}` | 来源类型对象；sourceType取值为memory、base64、internal、pixmap、astc、stream或unsupported。 |

资源字段支持字符串或对象格式，不直接包含图片二进制内容。

- **Image配置**

| 字段      | 值类型          | 说明         |
| ---------- | ----------------- | --------------- |
| url      | string / object | 图片来源。   |
| syncLoad | boolean         | 是否同步加载图片。true表示同步加载，false表示异步加载。 |

- **文本组件配置**

| 组件 | 字段 | 值类型 | 说明 |
| ---- | ---- | ------ | ---- |
| Text | BindSelectionMenu | boolean | 是否绑定自定义选择菜单。true表示已绑定，false表示未绑定。 |
| TextInput和TextArea | CustomKeyboard | boolean | 是否配置自定义键盘节点或构建函数。true表示已配置，false表示未配置。 |

- **Swiper配置**

| 字段          | 值类型  | 说明           |
| -------------- | --------- | ---------------- |
| disableSwipe | boolean | 是否禁用滑动。true表示禁用，false表示未禁用。 |

- **SheetPage配置**

| 字段            | 值类型  | 说明                                       |
| ----------------- | --------- | -------------------------------------------- |
| detents Size     | number  | Sheet档位配置数量。空格为字段名的组成部分。 |
| IsShouldDismiss | boolean | 是否配置关闭拦截回调。true表示已配置，false表示未配置。                           |

- **滚动组件公共配置与回调**

本节“滚动组件”包括Scroll、List、Grid和WaterFlow。这些组件共享滚动公共配置和回调字段。

| 字段                                | 值类型  | 说明                                                                                                                                                          |
| ------------------------------------ | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NestedScroll                       | string  | 嵌套滚动配置，参见[NestedScrollOptions](../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#nestedscrolloptions10对象说明)，见嵌套滚动格式表。 |
| backToTop                          | boolean | 是否支持点击状态栏回到顶部。true表示支持，false表示不支持。                                                                                                                                                |
| enableScrollInteraction            | boolean | 是否支持滚动手势。true表示支持，false表示不支持。                                                                                                                                                |
| friction / flingSpeedLimit         | number  | 摩擦系数和惯性滚动速度限制，速度单位为px/s。                                                                                                                  |
| hasOnScrollStart / hasOnScrollStop | boolean | 是否已配置滚动开始和停止回调。true表示已配置，false表示未配置。                                                                                                                                      |
| hasOnWillScroll / hasOnDidScroll   | boolean | 是否已配置滚动前和滚动后回调。true表示已配置，false表示未配置。                                                                                                                                      |
| hasOnScrollBegin                   | boolean | 是否已配置滚动帧开始回调。true表示已配置，false表示未配置。                                                                                                                  |
| hasOnReachStart / hasOnReachEnd    | boolean | 是否已配置到达起始位置和末尾位置的回调。true表示已配置，false表示未配置。                                                                                                                            |
| autoAdjustScrollBarMargin          | boolean | 是否自动调整滚动条边距。true表示自动调整，false表示不自动调整。                                                                                                                                      |
| isScrollable                       | boolean | 滚动条可滚动状态，true表示可滚动，false表示不可滚动；位于advanced.functional，与$attrs中的同名isScrollable（string滚动状态编码）含义不同。 |
| isReverse                          | boolean | 是否反向滚动；WaterFlow中该字段表示当前是否为反向布局。true表示是，false表示否。                                                                                                          |

- **嵌套滚动格式表**

| 字段         | 格式                                                    | 说明                                                                                                                   |
| -------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| NestedScroll | `NestedScrollOptions forward: <整数>, backward: <整数>` | 分别记录前向和后向[NestedScrollMode](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#nestedscrollmode10)整数值。 |

- **Scroll、List、ListItem、Grid、GridItem和WaterFlow配置**

| 组件               | 字段                                                                                                    | 值类型  | 说明                                           |
| -------------------- | -------------------------------------------------------------------------------------------------------- | --------- | ------------------------------------------------ |
| Scroll             | snapAlign                                                                                               | string  | [ScrollSnapAlign](../reference/apis-arkui/arkui-ts/ts-container-list.md#scrollsnapalign10枚举说明)对齐方式。 |
| Scroll             | snapPagination                                                                                          | object  | 吸附间隔或位置配置，见吸附分页格式表。         |
| Scroll             | enableSnapToStart / enableSnapToEnd                                                                     | boolean | 是否允许吸附到起始和结束边界。true表示允许，false表示不允许。 |
| Scroll             | enablePaging                                                                                            | string  | ScrollPagingStatus状态：NONE（未启用分页）、INVALID（分页配置无效）或VALID（分页配置有效）。 |
| Scroll             | initialOffset                                                                                           | string  | 主轴初始偏移，保留单位。                       |
| Scroll             | hasOnScrollEdge                                                                                         | boolean | 是否已配置滚动边缘回调。true表示已配置，false表示未配置。 |
| List               | multiSelectable / maintainVisibleContentPosition / stackFromEnd                                        | boolean | 是否启用多选/保持可见内容位置/从末尾排列。true表示是，false表示否。       |
| List               | sticky / scrollSnapAlign                                                                               | number  | 吸顶策略和滚动吸附对齐的整数枚举值。           |
| List               | syncLoad                                                                                               | boolean | 是否同步加载List区域内所有子组件。true表示同步加载，false表示异步加载。                                 |
| List               | hasOnScrollIndex / hasOnScrollChange                                                                   | boolean | 是否已配置索引变化和可见内容变化回调。true表示已配置，false表示未配置。               |
| ListItem、GridItem | selectable                                                                                             | boolean | 是否可选。true表示可选，false表示不可选。                               |
| ListItem           | startDeleteAreaDistance / endDeleteAreaDistance                                                        | number  | 起始侧和结束侧删除区域距离，单位为px。         |
| ListItem           | hasStartDeleteArea / hasEndDeleteArea                                                                  | boolean | 是否存在起始侧/结束侧删除区域。true表示存在，false表示不存在。                   |
| Grid               | [GridLayoutOptions](../reference/apis-arkui/arkui-ts/ts-container-grid.md#gridlayoutoptions10对象说明) | object  | 网格布局选项，含irregularIndexes整数索引数组。 |
| Grid               | CachedCount                                                                                            | number  | 缓存数量。                                     |
| Grid               | ShowCache                                                                                              | boolean | 是否显示缓存项。true表示显示，false表示不显示。                               |
| Grid               | Editable / ScrollEnabled                                                                               | boolean | 是否可编辑/是否可滚动。true表示是，false表示否。                               |
| WaterFlow          | CachedCount                                                                                            | number  | 缓存数量。                                     |
| WaterFlow          | footer                                                                                                 | boolean | 是否存在尾部节点。true表示存在，false表示不存在。                                 |
| WaterFlow          | hasOnScrollIndex                                                                                       | boolean | 是否已配置索引变化回调。true表示已配置，false表示未配置。                             |
| WaterFlow          | sections                                                                                               | array   | 分组配置对象数组，元素子字段见WaterFlow分组子字段。                             |

- **吸附分页格式表**

| 字段     | 格式   | 说明                                     |
| ---------- | -------- | ------------------------------------------ |
| interval | string | 吸附间隔，保留长度单位。                 |
| offsets  | array  | 吸附位置数组，元素为带单位的长度字符串。 |

- **WaterFlow分组子字段**

WaterFlow的sections数组元素包含以下子字段：

| 字段 | 值类型 | 说明 |
| ---- | ------ | ---- |
| itemsCount | number | 分组子项数量。 |
| crossCount | number | 交叉轴数量。 |
| columnsGap / rowsGap | string | 列间距和行间距，保留单位。 |
| margin | object | 分组边距对象，含left、right、top、bottom、start和end。 |
