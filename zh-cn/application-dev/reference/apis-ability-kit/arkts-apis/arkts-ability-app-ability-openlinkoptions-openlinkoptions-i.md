# OpenLinkOptions

OpenLinkOptions可以作为[openLink()](arkts-ability-uiabilitycontext-c.md#openLink)的入参，用于标识是否仅打开 AppLinking和传递键值对可选参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export default interface OpenLinkOptions--><!--Device-unnamed-export default interface OpenLinkOptions-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## appLinkingOnly

```TypeScript
appLinkingOnly?: boolean
```

表示是否必须以&lt;!--RP1--&gt;[AppLinking](../../../application-models/app-linking-startup.md)&lt;!--RP1End--&gt;的方式启动UIAbility。 - 取值为true时，如果不存在与AppLinking相匹配的UIAbility，直接返回。 - 取值为false时，如果不存在与AppLinking相匹配的UIAbility，AppLinking会退化为 [DeepLinking](../../../application-models/deep-linking-startup.md)。默认值为false。 aa命令隐式拉起Ability时可以通过设置"--pb appLinkingOnly true/false"以AppLinking的方式进行启动。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-OpenLinkOptions-appLinkingOnly?: boolean--><!--Device-OpenLinkOptions-appLinkingOnly?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## completionHandler

```TypeScript
completionHandler?: CompletionHandler
```

拉起应用结果的操作类，用于处理拉起应用的结果。

**类型：** [CompletionHandler](arkts-ability-app-ability-completionhandler-completionhandler-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-OpenLinkOptions-completionHandler?: CompletionHandler--><!--Device-OpenLinkOptions-completionHandler?: CompletionHandler-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## hideFailureTipDialog

```TypeScript
hideFailureTipDialog?: boolean
```

表示[Deep Linking](../../../application-models/deep-linking-startup.md)找不到应用时是否显示“暂无可用打开方式”的弹窗。 - 取值为true时，不显示“暂无可用打开方式”的弹窗。 - 取值为false时，显示“暂无可用打开方式”的弹窗。默认值为false。 **说明：**appLinkingOnly字段为true时不会触发Deep Linking流程，该字段不会生效。

**类型：** boolean

**默认值：** { false }

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-OpenLinkOptions-hideFailureTipDialog?: boolean--><!--Device-OpenLinkOptions-hideFailureTipDialog?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters?: Record<string, RecordData>
```

表示WantParams参数。

**类型：** Record&lt;string, [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenLinkOptions-parameters?: Record<string, RecordData>--><!--Device-OpenLinkOptions-parameters?: Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

