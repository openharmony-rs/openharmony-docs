# ContentFormCard

内容卡片控件，用于在应用内展示标题、描述、内容图片、应用信息等。适用于内容分发、社交动态、消息通知等场景。

**起始版本：** 20

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { ContentFormCard, FormType } from '@kit.ArkData';
```

## contentFormData

```TypeScript
contentFormData: uniformDataStruct.ContentForm
```

内容卡片数据，用于设置卡片展示的标题、描述、应用图标、应用名称、跳转链接或内容图片等信息。

**类型：** uniformDataStruct.ContentForm

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## formHeight

```TypeScript
formHeight?: number
```

卡片高度，当contentFormData中的title为空字符串时，卡片高度为传入的值，否则其范围在设置的内容卡片类型默认宽度的0.8 ~ 1.2倍之间，当formType为TYPE_SMALL时，其范围在设置的内容卡片类型默认 宽度的0.4 ~ 1.2倍之间。单位为vp。省略时使用内容卡片类型的默认高度。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## formType

```TypeScript
formType: FormType
```

内容卡片类型，影响内容卡片的大小。

**类型：** [FormType](arkts-arkdata-data-udmfcomponents-formtype-e.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## formWidth

```TypeScript
formWidth?: number
```

卡片宽度，其范围在设置的内容卡片类型默认宽度的0.8 ~ 1.2倍之间，当formType为TYPE_SMALL时，其范围在设置的内容卡片类型默认宽度的0.4 ~ 1.2倍之间。单位为vp。省略时使用内容卡片类型的默认宽度。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## handleOnClick

```TypeScript
handleOnClick?: Function
```

点击事件回调函数。用户点击卡片时，会执行传入的回调函数，实现自定义点击行为。

**类型：** Function

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core
