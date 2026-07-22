# PopupV2Button

PopupV2Button定义按钮的相关属性和事件。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface PopupV2Button--><!--Device-unnamed-export interface PopupV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { PopupV2Button, PopupV2, PopupV2InitInfo } from '@kit.ArkUI';
```

## action

```TypeScript
action?: Callback<void>
```

设置按钮点击回调。

默认不执行任何操作。

**类型：** Callback&lt;void&gt;

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PopupV2Button-action?: Callback<void>--><!--Device-PopupV2Button-action?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonTextModifier

```TypeScript
buttonTextModifier?: TextModifier
```

设置按钮文本属性，如设置文本颜色、字体大小等。默认值：undefined，值为undefined时，默认使用系统按钮文本属性。

**类型：** TextModifier

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PopupV2Button-buttonTextModifier?: TextModifier--><!--Device-PopupV2Button-buttonTextModifier?: TextModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: ResourceStr
```

设置按钮内容。

**类型：** ResourceStr

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PopupV2Button-text: ResourceStr--><!--Device-PopupV2Button-text: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

