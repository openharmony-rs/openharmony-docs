# AtomicServiceBar

原子化服务栏

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface AtomicServiceBar--><!--Device-unnamed-export interface AtomicServiceBar-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## getBarRect

```TypeScript
getBarRect(): Frame
```

获取bar的尺寸和位置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicServiceBar-getBarRect(): Frame--><!--Device-AtomicServiceBar-getBarRect(): Frame-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Frame](../../apis-arkui/arkts-apis/arkts-arkui-graphics-frame-i.md) | The size and position of bar in vp relative to window. |

## setBackgroundColor

```TypeScript
setBackgroundColor(color: Nullable< Color | int | string>): void
```

设置bar的背景色。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicServiceBar-setBackgroundColor(color: Nullable< Color | int | string>): void--><!--Device-AtomicServiceBar-setBackgroundColor(color: Nullable< Color | int | string>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Nullable](arkts-na-nullable-t.md)&lt;[Color](arkts-na-enums-color-e.md) \| int \| string&gt; | 是 | the color to set, undefined indicates using default. |

## setIconColor

```TypeScript
setIconColor(color: Nullable< Color | int | string>): void
```

设置bar上图标的颜色。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicServiceBar-setIconColor(color: Nullable< Color | int | string>): void--><!--Device-AtomicServiceBar-setIconColor(color: Nullable< Color | int | string>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Nullable](arkts-na-nullable-t.md)&lt;[Color](arkts-na-enums-color-e.md) \| int \| string&gt; | 是 | the color to set to icon, undefined indicates using default. |

## setTitleContent

```TypeScript
setTitleContent(content: string): void
```

设置bar的标题。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicServiceBar-setTitleContent(content: string): void--><!--Device-AtomicServiceBar-setTitleContent(content: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string | 是 | the content of the bar. |

## setTitleFontStyle

```TypeScript
setTitleFontStyle(font: FontStyle): void
```

设置bar标题的字体样式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicServiceBar-setTitleFontStyle(font: FontStyle): void--><!--Device-AtomicServiceBar-setTitleFontStyle(font: FontStyle): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| font | [FontStyle](arkts-na-enums-fontstyle-e.md) | 是 | the font style of the bar's title. |

## setVisible

```TypeScript
setVisible(visible: boolean): void
```

设置bar的可见性，不包括icon。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtomicServiceBar-setVisible(visible: boolean): void--><!--Device-AtomicServiceBar-setVisible(visible: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| visible | boolean | 是 | whether this bar is visible. |

