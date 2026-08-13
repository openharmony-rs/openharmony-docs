# ContentFormCard

内容卡片控件，用于在应用内展示标题、描述、内容图片、应用信息等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare struct ContentFormCard--><!--Device-unnamed-declare struct ContentFormCard-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## build

```TypeScript
@Builder
  build(): void
```

构建组件的方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentFormCard-@Builder  build(): void--><!--Device-ContentFormCard-@Builder  build(): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## contentFormData

```TypeScript
contentFormData: uniformDataStruct.ContentForm
```

内容卡片数据。

**类型：** uniformDataStruct.ContentForm

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentFormCard-contentFormData: uniformDataStruct.ContentForm--><!--Device-ContentFormCard-contentFormData: uniformDataStruct.ContentForm-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## formHeight

```TypeScript
@PropRef
  formHeight?: double
```

卡片高度，当contentFormData中的title为空字符串时，卡片高度为传入的值，否则其范围在设置的内容卡片类型默认宽度的0.8 ~ 1.2倍之间，当formType为TYPE_SMALL时，其范围在设置的内容卡片类型默认宽度的0.4 ~ 1.2倍之间。单位为vp。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentFormCard-@PropRef  formHeight?: double--><!--Device-ContentFormCard-@PropRef  formHeight?: double-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## formType

```TypeScript
@PropRef
  formType: FormType
```

内容卡片类型，影响内容卡片的大小。

**类型：** [FormType](arkts-na-data-udmfcomponents-formtype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentFormCard-@PropRef  formType: FormType--><!--Device-ContentFormCard-@PropRef  formType: FormType-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## formWidth

```TypeScript
@PropRef
  formWidth?: double
```

卡片宽度，其范围在设置的内容卡片类型默认宽度的0.8 ~ 1.2倍之间，当formType为TYPE_SMALL时，其范围在设置的内容卡片类型默认宽度的0.4 ~ 1.2倍之间。单位为vp。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentFormCard-@PropRef  formWidth?: double--><!--Device-ContentFormCard-@PropRef  formWidth?: double-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## handleOnClick

```TypeScript
handleOnClick?: Function
```

点击事件回调函数。

**类型：** Function

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentFormCard-handleOnClick?: Function--><!--Device-ContentFormCard-handleOnClick?: Function-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

