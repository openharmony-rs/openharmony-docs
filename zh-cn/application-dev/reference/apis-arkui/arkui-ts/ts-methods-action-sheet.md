# 列表选择弹窗 (ActionSheet)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--SE: @houguobiao-->
<!--TSE: @lxl007-->

列表弹窗。

>  **说明：**
>
>  从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../ui/arkts-global-interface.md)的地方使用，参见[UIContext](../arkts-apis-uicontext-uicontext.md)说明。

## ActionSheetOptions对象说明

列表选择弹窗的样式。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称      | 类型                    | 只读 | 可选 | 说明                          |
| ---------- | -------------------------- | ------- | ----------------------------- | ----------------------------- |
| title      | string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | 否    | 否    |  弹窗标题。<br/>当文本内容过长无法显示时，用省略号代替未显示的部分。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| subtitle<sup>10+</sup> | [ResourceStr](ts-types.md#resourcestr) | 否 | 是 | 弹窗副标题。<br/>当文本内容过长无法显示时，用省略号代替未显示的部分。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| message    | string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | 否    | 否    | 弹窗内容。<br/>文本超长时会触发滚动条。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。  |
| autoCancel | boolean                           | 否     | 是    | 点击遮障层时，是否关闭弹窗。<br>默认值：true<br>值为true时，点击遮障层关闭弹窗，值为false时，点击遮障层不关闭弹窗。 <br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。|
| confirm    | [ActionSheetButtonOptions](#actionsheetbuttonoptions18对象说明) | 否  | 是 | 确认Button的使能状态、默认焦点、按钮风格、文本内容和点击回调。在弹窗获焦且未进行tab键走焦时，该按钮默认响应Enter键。多重弹窗情况下，可自动获焦并连续响应。默认响应Enter键能力在defaultFocus为true时不生效。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| cancel     | [VoidCallback](ts-types.md#voidcallback12) | 否     | 是    | 点击遮障层关闭dialog时的回调。  <br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。  |
| alignment  | [DialogAlignment](ts-methods-alert-dialog-box.md#dialogalignment枚举说明) | 否     | 是    |  弹窗在竖直方向上的对齐方式。<br>默认值：DialogAlignment.Bottom  <br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**说明：** <br/>若在UIExtension中设置showInSubWindow为true，弹窗将基于UIExtension的宿主窗口对齐。|
| offset     | [ActionSheetOffset](#actionsheetoffset18对象说明) | 否      | 是     | 弹窗相对alignment所在位置的偏移量。<br/>默认值：<br/>1.alignment设置为Top、TopStart、TopEnd时默认值为{dx:&nbsp;0,dy:&nbsp;"40vp"} <br/>2.alignment设置为其他时默认值为{dx:&nbsp;0,dy:&nbsp;"-40vp"} <br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。|
| sheets     | Array&lt;[SheetInfo](#sheetinfo对象说明)&gt; | 否      | 否      | 设置选项内容，每个选择项支持设置图片、文本和选中的回调。 <br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。|
| maskRect<sup>10+</sup> | [Rectangle](ts-methods-alert-dialog-box.md#rectangle8类型说明) | 否     | 是   | 弹窗遮蔽层区域，在遮蔽层区域内的事件不透传，在遮蔽层区域外的事件透传。<br/>默认值：{ x: 0, y: 0, width: '100%', height: '100%' } <br/>**说明：** <br/>showInSubWindow为true时，maskRect不生效。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。|
| showInSubWindow<sup>11+</sup> | boolean | 否 | 是 | 某弹窗需要显示在主窗口之外时，是否在子窗口显示此弹窗。值为true表示在子窗口显示弹窗。<br/>默认值：false，弹窗显示在应用内，而非独立子窗口。<br/>**说明：** <br/>showInSubWindow为true的弹窗无法触发显示另一个showInSubWindow为true的弹窗。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| isModal<sup>11+</sup> | boolean | 否 | 是 | 弹窗是否为模态窗口，模态窗口有蒙层，非模态窗口无蒙层。值为false时，弹窗为非模态窗口，无蒙层。<br/>默认值：true，此时弹窗有蒙层。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| backgroundColor<sup>11+</sup> | [ResourceColor](ts-types.md#resourcecolor)  | 否 | 是 | 弹窗背板颜色。<br/>默认值：Color.Transparent<br/>**说明：** <br/>backgroundColor会与模糊属性backgroundBlurStyle叠加产生效果，如果不符合预期，可将backgroundBlurStyle设置为BlurStyle.NONE，即可取消模糊。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| backgroundBlurStyle<sup>11+</sup> | [BlurStyle](ts-universal-attributes-background.md#blurstyle9) | 否 | 是 | 弹窗背板模糊材质。<br/>默认值：BlurStyle.COMPONENT_ULTRA_THICK<br/>**说明：** <br/>设置为BlurStyle.NONE即可关闭背景虚化。当设置了backgroundBlurStyle为非NONE值时，则不要设置backgroundColor，否则颜色显示将不符合预期效果。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| backgroundBlurStyleOptions<sup>19+</sup> | [BackgroundBlurStyleOptions](ts-universal-attributes-background.md#backgroundblurstyleoptions10对象说明) | 否 | 是 | 背景模糊效果。默认值请参考BackgroundBlurStyleOptions类型说明。<br />**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。 |
| backgroundEffect<sup>19+</sup> | [BackgroundEffectOptions](ts-universal-attributes-background.md#backgroundeffectoptions11) | 否 | 是 | 背景效果参数。默认值请参考BackgroundEffectOptions类型说明。<br />**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。 |
| onWillDismiss<sup>12+</sup> | Callback<[DismissDialogAction](#dismissdialogaction12)> | 否 | 是 | 交互式关闭回调函数。<br/>**说明：**<br/>1.当用户执行点击遮障层关闭、侧滑（左滑/右滑）、三键back、键盘ESC关闭交互操作时，如果注册该回调函数，则不会立刻关闭弹窗。在回调函数中可以通过reason得到阻拦关闭弹窗的操作类型，从而根据原因选择是否能关闭弹窗。当前组件返回的reason中，暂不支持CLOSE_BUTTON的枚举值。<br/>2.在onWillDismiss回调中，不能再做onWillDismiss拦截。 <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| cornerRadius<sup>12+</sup> | [Dimension](ts-types.md#dimension10)&nbsp;\|&nbsp;[BorderRadiuses](ts-types.md#borderradiuses9) &nbsp;\|&nbsp; [LocalizedBorderRadiuses](ts-types.md#localizedborderradiuses12) | 否 | 是 | 设置背板的圆角半径。<br />可分别设置4个圆角的半径。<br />默认值：{ topLeft: '32vp', topRight: '32vp', bottomLeft: '32vp', bottomRight: '32vp' }<br /> 圆角大小受组件尺寸限制，最大值为组件宽或高的一半，若值为负，则按照默认值处理。 <br /> 百分比参数方式：以父元素弹窗宽和高的百分比来设置弹窗的圆角。<br/>**说明：**<br/>当cornerRadius属性类型为LocalizedBorderRadiuses时，支持随语言习惯改变布局顺序。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| borderWidth<sup>12+</sup> | [Dimension](ts-types.md#dimension10)&nbsp;\|&nbsp;[EdgeWidths](ts-types.md#edgewidths9)&nbsp;\|&nbsp;[LocalizedEdgeWidths](ts-types.md#localizededgewidths12) | 否 | 是 | 设置弹窗背板的边框宽度。<br />可分别设置4个边框宽度。<br />默认值：0<br /> 百分比参数方式：以父元素弹窗宽的百分比来设置弹窗的边框宽度。<br />当弹窗左边框和右边框大于弹窗宽度，弹窗上边框和下边框大于弹窗高度，显示可能不符合预期。<br/>**说明：**<br/>当borderWidth属性类型为LocalizedEdgeWidths时，支持随语言习惯改变布局顺序。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| borderColor<sup>12+</sup> | [ResourceColor](ts-types.md#resourcecolor)&nbsp;\|&nbsp;[EdgeColors](ts-types.md#edgecolors9)&nbsp;\|&nbsp;[LocalizedEdgeColors](ts-types.md#localizededgecolors12) | 否 | 是 | 设置弹窗背板的边框颜色。<br/>默认值：Color.Black<br/> 如果使用borderColor属性，需要和borderWidth属性一起使用。<br/>**说明：**<br/>当borderColor属性类型为LocalizedEdgeColors时，支持随语言习惯改变布局顺序。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| borderStyle<sup>12+</sup> | [BorderStyle](ts-appendix-enums.md#borderstyle)&nbsp;\|&nbsp;[EdgeStyles](ts-types.md#edgestyles9)  | 否 | 是 | 设置弹窗背板的边框样式。<br/>默认值：BorderStyle.Solid。<br/> 如果使用borderStyle属性，需要和borderWidth属性一起使用。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| width<sup>12+</sup> | [Dimension](ts-types.md#dimension10)   | 否 | 是 | 设置弹窗背板的宽度。<br />**说明：**<br>- 弹窗宽度默认最大值：400vp。<br />- 百分比参数方式：弹窗参考宽度为所在窗口的宽度，在此基础上调小或调大。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| height<sup>12+</sup> | [Dimension](ts-types.md#dimension10)   | 否 | 是 | 设置弹窗背板的高度。<br />**说明：**<br />- 弹窗高度默认最大值：0.9 *（窗口高度 - 安全区域）。<br />- 百分比参数方式：弹窗参考高度为（窗口高度 - 安全区域），在此基础上调小或调大。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| shadow<sup>12+</sup> | [ShadowOptions](ts-universal-attributes-image-effect.md#shadowoptions对象说明)&nbsp;\|&nbsp;[ShadowStyle](ts-universal-attributes-image-effect.md#shadowstyle10枚举说明)   | 否 | 是 | 设置弹窗背板的阴影。 <br /> 当设备为2in1时，默认场景下获焦阴影值为ShadowStyle.OUTER_FLOATING_MD，失焦为ShadowStyle.OUTER_FLOATING_SM。其他设备默认无阴影。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| transition<sup>12+</sup> | [TransitionEffect](ts-transition-animation-component.md#transitioneffect10对象说明) | 否 | 是 | 设置弹窗显示和退出的过渡效果。<br/>**说明：**<br/>1.如果不设置，则使用默认的显示/退出动效。<br/>2.显示动效中按back键，打断显示动效，执行退出动效，动画效果为显示动效与退出动效的曲线叠加后的效果。<br/>3.退出动效中按back键，不会打断退出动效，退出动效继续执行，继续按back键退出应用。 <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| enableHoverMode<sup>14+</sup>     | boolean | 否   | 是  | 是否响应悬停态，值为true表示响应悬停态。<br />默认值：false，默认不响应。<br/>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。|
| hoverModeArea<sup>14+</sup>       | [HoverModeAreaType](ts-appendix-enums.md#hovermodeareatype14) | 否   | 是  | 悬停态下弹窗默认展示区域。<br />默认值：HoverModeAreaType.BOTTOM_SCREEN。<br/>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。|
| onWillAppear<sup>19+</sup> | Callback&lt;void&gt; | 否 | 是 | 弹窗显示动效前的事件回调。<br />**说明：**<br />1.正常时序依次为：onWillAppear >> onDidAppear >> onWillDisappear >> onDidDisappear。<br />2.在onWillAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。 <br/>**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。|
| onDidAppear<sup>19+</sup> | Callback&lt;void&gt; | 否 | 是 | 弹窗弹出时的事件回调。<br />**说明：**<br />1.正常时序依次为：onWillAppear >> onDidAppear >> onWillDisappear >> onDidDisappear。<br />2.在onDidAppear内设置改变弹窗显示效果的回调事件，二次弹出生效。<br />3.快速点击弹出，关闭弹窗时，onWillDisappear在onDidAppear前生效。<br/>4.弹窗入场动效未完成时彻底关闭弹窗，动效打断，onDidAppear不会触发。<br/>**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。 |
| onWillDisappear<sup>19+</sup> | Callback&lt;void&gt; | 否 | 是 | 弹窗退出动效前的事件回调。<br />**说明：**<br />正常时序依次为：onWillAppear >> onDidAppear >> onWillDisappear >> onDidDisappear。<br /> **原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。|
| onDidDisappear<sup>19+</sup> | Callback&lt;void&gt; | 否 | 是 | 弹窗消失时的事件回调。<br />**说明：**<br />正常时序依次为：onWillAppear >> onDidAppear >> onWillDisappear >> onDidDisappear。<br/>**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。 |
| levelMode<sup>15+</sup>       | [LevelMode](#levelmode15) | 否   | 是  | 设置弹窗显示层级。<br />**说明：**<br />- 默认值：LevelMode.OVERLAY <br />- 仅当showInSubWindow属性设置为false时生效。<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。|
| levelUniqueId<sup>15+</sup>       | number | 否   | 是  | 设置页面级弹窗需要显示的层级下的[节点 uniqueId](../js-apis-arkui-frameNode.md#getuniqueid12)。<br/>取值范围：大于等于0的数字。<br />**说明：**<br />- 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。|
| immersiveMode<sup>15+</sup>       | [ImmersiveMode](#immersivemode15) | 否   | 是  | 设置页面内弹窗蒙层效果。<br />**说明：**<br />- 默认值：ImmersiveMode.DEFAULT <br />- 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。|
| levelOrder<sup>18+</sup>       | [LevelOrder](../js-apis-promptAction.md#levelorder18) | 否   | 是  | 设置弹窗显示的顺序。<br />**说明：**<br />- 默认值：LevelOrder.clamp(0) <br />- 不支持动态刷新顺序。<br/>**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。|

## SheetInfo对象说明

弹窗中的选项内容，每一项支持设置文本、图标以及选中的回调。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型                                                     | 只读 | 可选 | 说明         |
| ------ | ------------------------------------------------------------ | ---- | ----------------- | ----------------- |
| title  | string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | 否  | 否  | 选项的文本内容。<br/>文本超长时会触发滚动条。|
| icon   | string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | 否   | 是  | 选项的图标，默认无图标显示。<br>string格式可用于加载网络图片和本地图片，常用于加载网络图片。当使用相对路径引用本地图片时，例如Image("common/test.jpg")。|
| action | [VoidCallback](ts-types.md#voidcallback12) | 否  | 否  | 选项选中的回调。 |

## LevelMode<sup>15+</sup>

type LevelMode = LevelMode

弹窗的显示层级。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                                                        | 说明                 |
| ----------------------------------------------------------- | -------------------- |
| [LevelMode](../js-apis-promptAction.md#levelmode15枚举说明) | 设置弹窗的显示层级。 |

## ImmersiveMode<sup>15+</sup>

type ImmersiveMode = ImmersiveMode

弹窗的蒙层效果。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                                                         | 说明                       |
| ------------------------------------------------------------ | -------------------------- |
| [ImmersiveMode](../js-apis-promptAction.md#immersivemode15枚举说明) | 设置页面内弹窗的蒙层效果。 |

## DismissDialogAction<sup>12+</sup>

Dialog关闭的信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### 属性

| 名称    | 类型                                                         | 可读 | 可写 | 说明                                                         |
| ------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| dismiss | Callback&lt;void&gt;                                         | 否   | 否   | Dialog关闭回调函数。开发者需要退出时调用，不需要退出时无需调用。 |
| reason  | [DismissReason](../js-apis-promptAction.md#dismissreason12枚举说明) | 否   | 否   | Dialog无法关闭原因。根据开发者需求选择不同操作下，Dialog是否关闭。 |

## ActionSheetButtonOptions<sup>18+</sup>对象说明

弹窗中按钮的样式。

> **说明：**
>
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称         | 类型    | 只读 | 可选 | 说明 |
| ------------ | ------- | ---- | ---- | ---- |
| enabled<sup>10+</sup> | boolean | 否   | 是  | 点击Button是否响应，true表示Button可以响应，false表示Button不可以响应。<br/>默认值：true<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| defaultFocus<sup>10+</sup> | boolean | 否   | 是  | 设置Button是否是默认焦点，true表示Button是默认焦点，false表示Button不是默认焦点。<br/>默认值：false<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| style<sup>10+</sup> | [DialogButtonStyle](ts-appendix-enums.md#dialogbuttonstyle10) | 否  | 是 | 设置Button的风格样式。<br />默认值：DialogButtonStyle.DEFAULT<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| value<sup>8+</sup> |  string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) |   否  |   否  | Button文本内容。<br/>当文本内容过长无法显示时，用省略号代替未显示的部分。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| action<sup>8+</sup> | [VoidCallback](ts-types.md#voidcallback12)      |   否   |   否   | Button选中时的回调。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |

## ActionSheetOffset<sup>18+</sup>对象说明

弹窗的对齐方式。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型                                                         | 只读 | 可选 | 说明                                                         |
| ---- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| dx   | number&nbsp;\|&nbsp;string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | 否   | 否   | 弹出窗口相对于对齐位置dx的偏移量。<br/>需要显式指定像素单位，如'10px'，也可设置百分比字符串，如'100%'。<br/>**说明：** <br/>不指定像素单位时，默认单位vp，如'10'，等同于10。 |
| dy   | number&nbsp;\|&nbsp;string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | 否   | 否   | 弹出窗口相对于对齐位置dy的偏移量。<br/>需要显式指定像素单位，如'10px'，也可设置百分比字符串，如'100%'。<br/>**说明：** <br/>不指定像素单位时，默认单位vp，如'10'，等同于10。 |

## ActionSheet

### show<sup>(deprecated)</sup>

static show(value: ActionSheetOptions)

定义列表弹窗并弹出。

> **说明：**
> 
> 从API version 18开始废弃，建议使用[UIContext](../arkts-apis-uicontext-uicontext.md)中的[showActionSheet](../arkts-apis-uicontext-uicontext.md#showactionsheet)替代。
>
> 从API version 10开始，可以通过使用[UIContext](../arkts-apis-uicontext-uicontext.md)中的[showActionSheet](../arkts-apis-uicontext-uicontext.md#showactionsheet)来明确UI的执行上下文。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                              | 必填 | 说明                     |
| ------ | ------------------------------------------------- | ---- | ------------------------ |
| value  | [ActionSheetOptions](#actionsheetoptions对象说明) | 是   | 配置列表选择弹窗的参数。 |

## 示例

> **说明：**
> 
> 直接使用ActionSheet可能导致实例不明确的问题，建议使用getUIContext()获取[UIContext](../arkts-apis-uicontext-uicontext.md)实例，并使用[showActionSheet](../arkts-apis-uicontext-uicontext.md#showactionsheet)调用绑定实例的ActionSheet.show()。

### 示例1（弹出列表选择弹窗）

该示例通过点击按钮弹窗列表选择弹窗。

```ts
// xxx.ets
@Entry
@Component
struct ActionSheetExample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('Click to Show ActionSheet')
        .onClick(() => {
          this.getUIContext().showActionSheet({
            title: 'ActionSheet title',
            subtitle: 'ActionSheet subtitle',
            message: 'message',
            autoCancel: true,
            confirm: {
              defaultFocus: true,
              value: 'Confirm button',
              action: () => {
                console.info('Get ActionSheet handled');
              }
            },
            cancel: () => {
              console.info('ActionSheet canceled');
            },
            onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
              console.info(`reason= ${dismissDialogAction.reason}`);
              console.info('ActionSheet onWillDismiss');
              if (dismissDialogAction.reason === DismissReason.PRESS_BACK) {
                dismissDialogAction.dismiss();
              }
              if (dismissDialogAction.reason === DismissReason.TOUCH_OUTSIDE) {
                dismissDialogAction.dismiss();
              }
            },
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -10 },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('pears');
                }
              }
            ]
          })
        })
    }.width('100%')
    .height('100%')
  }
}
```

![zh-cn_image_action](figures/zh-cn_image_action.gif)

### 示例2（可在主窗外弹出的弹窗）

在2in1设备上设置showInSubWindow为true时，可以弹出在主窗外显示的弹窗。

```ts
// xxx.ets
@Entry
@Component
struct ActionSheetExample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('Click to Show ActionSheet')
        .onClick(() => {
          this.getUIContext().showActionSheet({
            title: 'ActionSheet title',
            subtitle: 'ActionSheet subtitle',
            message: 'message',
            autoCancel: true,
            showInSubWindow: true,
            isModal: true,
            confirm: {
              defaultFocus: true,
              value: 'Confirm button',
              action: () => {
                console.info('Get ActionSheet handled');
              }
            },
            cancel: () => {
              console.info('ActionSheet canceled');
            },
            onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
              console.info(`reason= ${dismissDialogAction.reason}`);
              console.info('ActionSheet onWillDismiss');
              if (dismissDialogAction.reason === DismissReason.PRESS_BACK) {
                dismissDialogAction.dismiss();
              }
              if (dismissDialogAction.reason === DismissReason.TOUCH_OUTSIDE) {
                dismissDialogAction.dismiss();
              }
            },
            alignment: DialogAlignment.Center,
            offset: { dx: 0, dy: -10 },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('pears');
                }
              }
            ]
          })
        })
    }.width('100%')
    .height('100%')
  }
}
```

![zh-cn_image_action_showinsubwindow](figures/zh-cn_image_action_showinsubwindow.jpg)

### 示例3（设置弹窗的动画）

该示例通过配置transition实现弹窗的显示和消失动画。

```ts
// xxx.ets
@Entry
@Component
struct ActionSheetExample {
  build() {
    Column({ space: 5 }) {
      Button('ActionSheet Set Duration')
        .onClick(() => {
          this.getUIContext().showActionSheet({
            title: 'ActionSheet 1',
            message: 'Set Animation Duration open 3 second, close 100 ms',
            autoCancel: true,
            alignment: DialogAlignment.Top,
            transition: TransitionEffect.asymmetric(TransitionEffect.OPACITY
              .animation({ duration: 3000, curve: Curve.Sharp })
              .combine(TransitionEffect.scale({ x: 1.5, y: 1.5 }).animation({ duration: 3000, curve: Curve.Sharp })),
              TransitionEffect.OPACITY.animation({ duration: 100, curve: Curve.Smooth })
                .combine(TransitionEffect.scale({ x: 0.5, y: 0.5 }).animation({ duration: 100, curve: Curve.Smooth }))),
            offset: { dx: 0, dy: -20 },
            confirm: {
              value: 'button',
              action: () => {
                console.info('Button-clicking callback');
              }
            },
            cancel: () => {
              console.info('Closed callbacks');
            },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('pears');
                }
              }
            ]
          })
        }).backgroundColor(0x317aff).height("88px")
    }.width('100%').margin({ top: 5 })
  }
}
```

![zh-cn_image_action_animation](figures/zh-cn_image_action_animation.gif)

### 示例4（设置弹窗的样式）

该示例定义了ActionSheet的样式，如宽度、高度、背景色、阴影等。

```ts
// xxx.ets
@Entry
@Component
struct ActionSheetExample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center }) {
      Button('Click to Show ActionSheet')
        .onClick(() => {
          this.getUIContext().showActionSheet({
            title: 'ActionSheet title',
            subtitle: 'ActionSheet subtitle',
            message: 'message',
            autoCancel: true,
            width: 300,
            height: 350,
            cornerRadius: 20,
            borderWidth: 1,
            borderStyle: BorderStyle.Solid, //使用borderStyle属性，需要和borderWidth属性一起使用
            borderColor: Color.Blue, //使用borderColor属性，需要和borderWidth属性一起使用
            backgroundColor: Color.White,
            shadow: ({
              radius: 20,
              color: Color.Grey,
              offsetX: 50,
              offsetY: 0
            }),
            confirm: {
              defaultFocus: true,
              value: 'Confirm button',
              action: () => {
                console.info('Get ActionSheet handled');
              }
            },
            cancel: () => {
              console.info('ActionSheet canceled');
            },
            onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
              console.info(`reason= ${dismissDialogAction.reason}`);
              console.info('ActionSheet onWillDismiss');
              if (dismissDialogAction.reason === DismissReason.PRESS_BACK) {
                dismissDialogAction.dismiss();
              }
              if (dismissDialogAction.reason === DismissReason.TOUCH_OUTSIDE) {
                dismissDialogAction.dismiss();
              }
            },
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -10 },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('pears');
                }
              }
            ]
          })
        })
    }.width('100%')
  }
}
```

![zh-cn_image_action_style](figures/zh-cn_image_action_style.gif)

### 示例5（悬停态弹窗）

该示例展示了在折叠屏悬停态下设置dialog布局区域的效果。

```ts
// xxx.ets
@Entry
@Component
struct ActionSheetExample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('Click to Show ActionSheet')
        .onClick(() => {
          this.getUIContext().showActionSheet({
            title: 'ActionSheet title',
            subtitle: 'ActionSheet subtitle',
            message: 'message',
            autoCancel: true,
            confirm: {
              defaultFocus: true,
              value: 'Confirm button',
              action: () => {
                console.info('Get ActionSheet handled');
              }
            },
            cancel: () => {
              console.info('ActionSheet canceled');
            },
            onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
              console.info(`reason= ${dismissDialogAction.reason}`);
              console.info('ActionSheet onWillDismiss');
              if (dismissDialogAction.reason === DismissReason.PRESS_BACK) {
                dismissDialogAction.dismiss();
              }
              if (dismissDialogAction.reason === DismissReason.TOUCH_OUTSIDE) {
                dismissDialogAction.dismiss();
              }
            },
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -10 },
            enableHoverMode: true,
            hoverModeArea: HoverModeAreaType.TOP_SCREEN,
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('pears');
                }
              }
            ]
          })
        })
    }.width('100%')
    .height('100%')
  }
}
```

![zh-cn_image_action_style](figures/zh-cn_image_action_hovermode.gif)

### 示例6（弹窗生命周期）

该示例展示了弹窗生命周期的相关接口的使用方法。

```ts
// xxx.ets
@Entry
@Component
struct Example1 {
  @State log: string = 'Log information:';
  flag: boolean = false;

  build() {
    Column({ space: 5 }) {
      Button('ActionSheet')
        .onClick(() => {
          this.getUIContext().showActionSheet({
            title: 'ActionSheet',
            message: 'message',
            autoCancel: true,
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -20 },
            confirm: {
              value: 'button',
              action: () => {
                console.info('ActionSheet Button-clicking callback');
              }
            },
            cancel: () => {
              console.info('ActionSheet Closed callbacks');
            },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('ActionSheet apples')
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('ActionSheet bananas')
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('ActionSheet pears')
                }
              }
            ],
            onDidAppear: () => {
              this.log += '# onDidAppear';
              console.info('ActionSheet,is onDidAppear!');
            },
            onDidDisappear: () => {
              this.log += '# onDidDisappear';
              console.info('ActionSheet,is onDidDisappear!');
            },
            onWillAppear: () => {
              this.log = 'Log information:onWillAppear';
              console.info('ActionSheet,is onWillAppear!');
            },
            onWillDisappear: () => {
              this.log += '# onWillDisappear';
              console.info('ActionSheet,is onWillDisappear!');
            }
          })
        })
      Text(this.log).fontSize(30).margin({ top: 200 })
    }.width('100%').margin({ top: 5 })
  }
}
```

![zh-cn_image_action_lifecycle](figures/zh-cn_image_action_lifecycle.gif)
