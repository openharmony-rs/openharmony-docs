# AtomicServiceBar

interface AtomicServiceBar

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getBarRect

```TypeScript
getBarRect(): Frame
```

Get size and position of the bar.

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Frame | The size and position of bar in vp relative to window. |

## onBarRectChange

```TypeScript
onBarRectChange(callback: Callback<Frame>): void
```

当appbar的组件大小发生变化时会触发调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;Frame&gt; | 是 | 回调函数的参数为Frame。当传入的callback为undefined时表示取消监听appbar组件的大小变化。回调函数触发时，回调函数的参数不可能为undefined或者null。 |

## setBackgroundColor

```TypeScript
setBackgroundColor(color: Nullable< Color | number | string>): void
```

Set the background color of the bar.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Nullable&lt; Color \| number \| string&gt; | 是 | the color to set, undefined indicates using default. |

## setIconColor

```TypeScript
setIconColor(color: Nullable< Color | number | string>): void
```

Set the color of the icon on the bar.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Nullable&lt; Color \| number \| string&gt; | 是 | the color to set to icon, undefined indicates using default. |

## setTitleContent

```TypeScript
setTitleContent(content: string): void
```

Set the title of the bar.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string | 是 | the content of the bar. |

## setTitleFontStyle

```TypeScript
setTitleFontStyle(font: FontStyle): void
```

Set the font style of the bar's title.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| font | FontStyle | 是 | the font style of the bar's title. |

## setVisible

```TypeScript
setVisible(visible: boolean): void
```

Set the visibility of the bar, except the icon.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| visible | boolean | 是 | whether this bar is visible. |

