# CrossLanguageOptions

该接口用于配置或查询FrameNode的跨语言访问权限。例如，针对ArkTS语言创建的节点，可通过该接口控制是否允许通过非ArkTS语言进行属性访问或修改。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface CrossLanguageOptions--><!--Device-unnamed-export declare interface CrossLanguageOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeSetting

```TypeScript
attributeSetting?: boolean
```

FrameNode是否支持跨ArkTS语言进行属性设置。 true表示支持跨ArkTS语言进行属性设置，false表示不支持跨ArkTS语言进行属性设置。 默认值为false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CrossLanguageOptions-attributeSetting?: boolean--><!--Device-CrossLanguageOptions-attributeSetting?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## treeOperating

```TypeScript
treeOperating?: boolean
```

FrameNode是否支持跨ArkTS语言进行组件树操作。 true表示支持跨ArkTS语言进行组件树操作，false表示不支持跨ArkTS语言进行组件树操作。 默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CrossLanguageOptions-treeOperating?: boolean--><!--Device-CrossLanguageOptions-treeOperating?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

