# CrossLanguageOptions

该接口用于配置或查询FrameNode的跨语言访问权限。例如，针对ArkTS语言创建的节点，可通过该接口控制是否允许通过非ArkTS语言进行属性访问或修改。

**起始版本：** 15

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeSetting

```TypeScript
attributeSetting?: boolean
```

FrameNode是否支持跨ArkTS语言进行属性设置。

true表示支持跨ArkTS语言进行属性设置，false表示不支持跨ArkTS语言进行属性设置。

默认值为false。

**类型：** boolean

**默认值：** false

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## treeOperating

```TypeScript
treeOperating?: boolean
```

FrameNode是否支持跨ArkTS语言进行组件树操作。

true表示支持跨ArkTS语言进行组件树操作，false表示不支持跨ArkTS语言进行组件树操作。

默认值为false。

**说明：** 当FrameNode启用了跨ArkTS语言进行组件树操作的选项后，支持该FrameNode跨ArkTS语言调用
[addChild](../../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#addchild)、
[insertChildAfter](../../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#insertchildafter)
、[insertChildAt](../../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#insertchildat)、
[insertChildBefore](../../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#insertchildbefore)
和[removeChild](../../../../reference/apis-arkui/capi-arkui-nativemodule-arkui-nativenodeapi-1.md#removechild)。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

