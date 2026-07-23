# SaveButton属性/事件

不支持通用属性，除了继承[安全控件通用属性](../arkts-apis/arkts-security_component.md)，还支持以下属性。不支持通用事件，仅支持以下事件。

**继承/实现关系：** SaveButtonAttribute extends [SecurityComponentMethod<SaveButtonAttribute>]

**起始版本：** 10

<!--Device-unnamed-declare class SaveButtonAttribute extends SecurityComponentMethod<SaveButtonAttribute>--><!--Device-unnamed-declare class SaveButtonAttribute extends SecurityComponentMethod<SaveButtonAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconBorderRadius

```TypeScript
iconBorderRadius(radius: Dimension | BorderRadiuses)
```

设置保存控件图标的边框圆角半径。

**起始版本：** 20

**需要权限：** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonAttribute-iconBorderRadius(radius: Dimension | BorderRadiuses): SaveButtonAttribute--><!--Device-SaveButtonAttribute-iconBorderRadius(radius: Dimension | BorderRadiuses): SaveButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) \| BorderRadiuses | 是 | 保存控件图标的圆角半径，支持设置四个圆角。<br>默认值：四个圆角均为0vp。支持像素单位（vp、px等），取值范围≥0。传入负值时自动修正为0。<br/>若应用不具备ohos.permission.CUSTOMIZE_SAVE_BUTTON权限，则图标的圆角半径设置不生效。 |

## iconSize

```TypeScript
iconSize(size: Dimension | SizeOptions)
```

设置保存控件的图标尺寸。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonAttribute-iconSize(size: Dimension | SizeOptions): SaveButtonAttribute--><!--Device-SaveButtonAttribute-iconSize(size: Dimension | SizeOptions): SaveButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) \| SizeOptions | 是 | 图标尺寸，支持像素单位（vp、px等）。<br>不支持设置百分比字符串。若设置Dimension类型入参的百分比字符串，则图标尺寸显示为默认值；若设置SizeOptions类型入参的width或height属性为百分比字符串，则图标尺寸显示为0vp。<br/>对于保存控件提供的系统图标：<br/>- 使用Dimension类型入参时，宽、高相等，均为设定值。<br/>- 使用SizeOptions类型入参时，若宽、高设定值不一致，则宽、高相等取两者较小值；若仅设定其中一个值，则取该值作为宽、高值。系统提供图标采用此规则是为保证图标的正方形显示和视觉一致性。<br/>对于自定义图标：<br/>- 使用Dimension类型入参时，宽、高相等，均为设定值。<br/>- 使用SizeOptions类型入参时，建议同时设定宽和高，此时按照指定宽、高生效；若仅设定其中一个值，则宽高均显示为该设定值。自定义图标允许灵活设定尺寸以适应不同图片比例。<br/>- 当设定的宽高与自定义图标的宽高比例不一致时，图片按[ImageFit.Cover](../arkts-apis/arkts-arkui-imagefit-e.md)的方式填充显示区域。 |

## onClick

```TypeScript
onClick(event: SaveButtonCallback)
```

点击保存控件触发该回调。用户首次点击保存控件时会展示授权弹窗，点击允许后授权成功，应用会获取访问媒体库接口的临时授权（授权持续时间见[SaveButton](../../../reference/apis-arkui/arkui-ts/ts-security-components-savebutton.md#savebutton-1)构造函数说明）；点击拒绝或关闭弹窗则授权失败。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonAttribute-onClick(event: SaveButtonCallback): SaveButtonAttribute--><!--Device-SaveButtonAttribute-onClick(event: SaveButtonCallback): SaveButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [SaveButtonCallback](arkts-arkui-savebuttoncallback-t.md) | 是 | 点击事件的回调对象，包含点击事件信息、授权结果和错误信息。<br>从APIversion 18开始，统一使用SaveButtonCallback，可额外获取error信息。<br>**起始版本：** 18 |

## setIcon

```TypeScript
setIcon(icon: Resource)
```

设置保存控件的图标。

**起始版本：** 20

**需要权限：** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonAttribute-setIcon(icon: Resource): SaveButtonAttribute--><!--Device-SaveButtonAttribute-setIcon(icon: Resource): SaveButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | 自定义图标资源信息，仅支持Resource类型的数据源。<br>可支持的图片格式：png、jpg、jpeg、bmp、svg、webp、gif和heif等，支持的图片格式范围见[Image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)。当资源为非图片资源或不支持的格式时，图标显示为空白。<br/>从API版本26.0.0开始，支持Symbol格式的Resource类型的数据源。<br/>若应用不具备ohos.permission.CUS TOMIZE_SAVE_BUTTON权限，则自定义图标设置不生效，保存控件保持默认样式。 |

## setText

```TypeScript
setText(text: string | Resource)
```

设置保存控件的文本。

**起始版本：** 20

**需要权限：** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonAttribute-setText(text: string | Resource): SaveButtonAttribute--><!--Device-SaveButtonAttribute-setText(text: string | Resource): SaveButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string \| Resource | 是 | 自定义文本信息。适用于需要使用与业务强相关的文本替代系统预置描述的场景。传入字符串时直接使用文本内容；传入Resource时，可配合资源管理实现多语言文本。<br>若应用不具备ohos.permission.CUSTOMIZE_SAVE_BUTTON权限，则该设置不生效，保存控件保持默认样式。 |

## stateEffect

```TypeScript
stateEffect(enabled: boolean)
```

设置保存控件的按压效果。

**起始版本：** 20

**需要权限：** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonAttribute-stateEffect(enabled: boolean): SaveButtonAttribute--><!--Device-SaveButtonAttribute-stateEffect(enabled: boolean): SaveButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | true表示保存控件按压时显示按压效果，false表示保存控件按压时不显示按压效果。<br>默认值：true。<br/>若应用不具备ohos.permission.CUSTOMIZE_SAVE_BUTTON权限，按压效果设置不生效。 |

## symbolFontWeight

```TypeScript
symbolFontWeight(fontWeight: number | FontWeight | string | Resource)
```

设置保存控件Symbol图标粗细。

- 调用本方法前，需先调用[setIcon](SaveButtonAttribute#setIcon)设置Symbol格式的图标资源（如$r('sys.symbol.xxx')），本方法才会生效。  
- 若未设置Symbol图标，该方法设置的粗细不会生效。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonAttribute-symbolFontWeight(fontWeight: number | FontWeight | string | Resource): SaveButtonAttribute--><!--Device-SaveButtonAttribute-symbolFontWeight(fontWeight: number | FontWeight | string | Resource): SaveButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontWeight | number \| FontWeight \| string \| Resource | 是 | 设置保存控件Symbol图标粗细。<br>支持number类型：取值范围为[100, 900]，取值间隔为100，数值越大字体越粗。<br/>支持string类型：可传入number类型的数字字符串（如"400"），或[FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md)的枚举值的小写字符串（如"normal"）。<br/>默认值：FontWeight.Normal（对应数值400）。<br/>若应用不具备ohos.permission.CUSTOMIZE_SAVE_BUTTON权限，则该设置不生效。 |

## symbolIconColor

```TypeScript
symbolIconColor(color: Array<ResourceColor>)
```

设置保存控件Symbol图标颜色。

- 调用本方法前，需先调用[setIcon](SaveButtonAttribute#setIcon)设置Symbol格式的图标资源（如$r('sys.symbol.xxx')），本方法才会生效。  
- 若未设置Symbol图标，该方法设置的颜色不会生效。  
- 建议与[symbolRenderingStrategy](SaveButtonAttribute#symbolRenderingStrategy)配合使用，以实现不同的渲染效果。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonAttribute-symbolIconColor(color: Array<ResourceColor>): SaveButtonAttribute--><!--Device-SaveButtonAttribute-symbolIconColor(color: Array<ResourceColor>): SaveButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Array&lt;ResourceColor&gt; | 是 | 设置保存控件Symbol图标颜色。适用于Symbol图标需要与业务视觉风格保持一致的场景。<br>默认值：随[symbolRenderingStrategy](SaveButtonAttribute#symbolRenderingStrategy)不同而变化。<br>若应用不具备ohos.permission.CUSTOMIZE_SAVE_BUTTON权限，则该设置不生效。 |

## symbolRenderingStrategy

```TypeScript
symbolRenderingStrategy(strategy: SymbolRenderingStrategy)
```

设置保存控件Symbol图标渲染策略。

- 调用本方法前，需先调用[setIcon](SaveButtonAttribute#setIcon)设置Symbol格式的图标资源（如$r('sys.symbol.xxx')），本方法才会生效。  
- 若未设置Symbol图标，该方法设置的渲染策略不会生效。  
- 与[symbolIconColor](SaveButtonAttribute#symbolIconColor)配合使用时，渲染策略会影响颜色数组的作用方式。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CUSTOMIZE_SAVE_BUTTON

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonAttribute-symbolRenderingStrategy(strategy: SymbolRenderingStrategy): SaveButtonAttribute--><!--Device-SaveButtonAttribute-symbolRenderingStrategy(strategy: SymbolRenderingStrategy): SaveButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strategy | [SymbolRenderingStrategy](arkts-arkui-symbolrenderingstrategy-e.md) | 是 | 保存控件Symbol图标渲染策略，用于控制Symbol图标的渲染方式。<br>默认值：SymbolRenderingStrategy.SINGLE。<br>若应用不具备ohos.permission.CUSTOMIZE_SAVE_BUTTON权限，则该设置不生效。 |

## userCancelEvent

```TypeScript
userCancelEvent(enabled: boolean)
```

设置接收保存控件的用户取消授权事件。适用于需要区分用户主动取消授权和授权失败的场景，以便进行不同的业务处理，例如记录用户行为、提供重试提示等。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonAttribute-userCancelEvent(enabled: boolean): SaveButtonAttribute--><!--Device-SaveButtonAttribute-userCancelEvent(enabled: boolean): SaveButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 表示是否接收保存控件的用户取消授权事件。<br>true表示当用户在授权弹窗中主动取消时，会通过回调将结果区分为CANCELED_BY_USER；false表示不单独区分此类场景。<br/>当业务需要区分“用户取消”和“系统错误/授权失败”时，建议开启该参数。 |

