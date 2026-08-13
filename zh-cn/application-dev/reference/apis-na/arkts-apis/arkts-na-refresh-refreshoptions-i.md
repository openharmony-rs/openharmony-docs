# RefreshOptions

用于设置Refresh组件参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface RefreshOptions--><!--Device-unnamed-export interface RefreshOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: CustomBuilder
```

自定义刷新区域显示内容。

**类型：** CustomBuilder

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RefreshOptions-builder?: CustomBuilder--><!--Device-RefreshOptions-builder?: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## promptText

```TypeScript
promptText?: ResourceStr
```

设置刷新区域底部显示的自定义文本。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RefreshOptions-promptText?: ResourceStr--><!--Device-RefreshOptions-promptText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## refreshing

```TypeScript
refreshing: boolean | Bindable<boolean>
```

组件当前是否处于刷新中状态。该参数支持\$用于双向绑定变量。

**类型：** boolean \| [Bindable](arkts-na-common-bindable-i.md)&lt;boolean&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RefreshOptions-refreshing: boolean | Bindable<boolean>--><!--Device-RefreshOptions-refreshing: boolean | Bindable<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## refreshingContent

```TypeScript
refreshingContent?: ComponentContentBase
```

自定义刷新区域显示内容。

**类型：** [ComponentContentBase](arkts-na-componentcontent-componentcontentbase-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RefreshOptions-refreshingContent?: ComponentContentBase--><!--Device-RefreshOptions-refreshingContent?: ComponentContentBase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

