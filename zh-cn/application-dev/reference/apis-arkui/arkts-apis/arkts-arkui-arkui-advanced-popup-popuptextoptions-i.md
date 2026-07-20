# PopupTextOptions

设置文本样式。

**起始版本：** 11

<!--Device-unnamed-export interface PopupTextOptions--><!--Device-unnamed-export interface PopupTextOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Popup, PopupOptions, PopupButtonOptions, PopupIconOptions, PopupTextOptions } from '@kit.ArkUI';
```

## fontColor

```TypeScript
fontColor?: ResourceColor
```

设置文本字体颜色。

默认值：`$r('sys.color.ohos_id_color_text_secondary')`

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupTextOptions-fontColor?: ResourceColor--><!--Device-PopupTextOptions-fontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | string | Resource
```

设置文本字体大小。

默认值：`$r('sys.float.ohos_id_text_size_body2')`

string类型可选值：可以转化为数字的字符串（如'10'）或带长度单位的字符串（如'10px'），不支持设置百分比字符串。

number：取值范围(0,+∞)。为number类型时默认单位：fp。

**类型：** number \| string \| Resource

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupTextOptions-fontSize?: number | string | Resource--><!--Device-PopupTextOptions-fontSize?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | string
```

设置文本字体粗细。

number类型取值[100,900]，取值间隔为100，默认为400，取值越大，字体越粗。

string类型仅支持number类型取值的字符串形式，例如“400”，以及“bold”、“bolder”、“lighter”、“regular” 、“medium”分别对应FontWeight中相应的枚举值。

默认值：FontWeight.Regular

**类型：** number \| FontWeight \| string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupTextOptions-fontWeight?: number | FontWeight | string--><!--Device-PopupTextOptions-fontWeight?: number | FontWeight | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: ResourceStr
```

设置文本内容。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupTextOptions-text: ResourceStr--><!--Device-PopupTextOptions-text: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

