# FormInfo

卡片配置信息。

**起始版本：** 23

<!--Device-formInfo-interface FormInfo--><!--Device-formInfo-interface FormInfo-End-->

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## enableBlurBackground

```TypeScript
readonly enableBlurBackground?: boolean
```

卡片是否使用模糊背板。 - true：开启模糊背板。 - false：关闭模糊背板。

**类型：** boolean

**起始版本：** 23

<!--Device-FormInfo-readonly enableBlurBackground?: boolean--><!--Device-FormInfo-readonly enableBlurBackground?: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## funInteractionParams

```TypeScript
readonly funInteractionParams?: FunInteractionParams
```

趣味交互卡片配置参数。主要配置互动卡片激活态时长等参数。

**类型：** [FunInteractionParams](arkts-form-forminfo-funinteractionparams-i-sys.md)

**起始版本：** 23

<!--Device-FormInfo-readonly funInteractionParams?: FunInteractionParams--><!--Device-FormInfo-readonly funInteractionParams?: FunInteractionParams-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## groupId

```TypeScript
readonly groupId?: string
```

表示一组卡片的共同id。多张卡片的groupId相同且resizable为true时，多张卡片的supportDimensions配置共享。例如，卡片A和B的groupId相同且resizable均为true，则卡片A可以调整 为卡片A和B的supportDimensions配置中的任意尺寸。 推荐多张卡片功能相同且需要调整卡片尺寸时配置。

**类型：** string

**起始版本：** 23

<!--Device-FormInfo-readonly groupId?: string--><!--Device-FormInfo-readonly groupId?: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## isFontScaleFollowSystem

```TypeScript
isFontScaleFollowSystem?: boolean
```

卡片的字体缩放是否跟随系统，默认值为true。 - true：字体缩放跟随系统。 - false：字体缩放不会跟随系统。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormInfo-isFontScaleFollowSystem?: boolean--><!--Device-FormInfo-isFontScaleFollowSystem?: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## isPrivacySensitive

```TypeScript
readonly isPrivacySensitive?: boolean
```

卡片是否是隐私敏感卡片。 - true：是隐私敏感卡片。 - false：不是隐私敏感卡片。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormInfo-readonly isPrivacySensitive?: boolean--><!--Device-FormInfo-readonly isPrivacySensitive?: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## isStandbyAdapted

```TypeScript
readonly isStandbyAdapted?: boolean
```

卡片是否已适配灵动显示规则。 - true：已适配灵动显示。 - false：未适配灵动显示。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormInfo-readonly isStandbyAdapted?: boolean--><!--Device-FormInfo-readonly isStandbyAdapted?: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## isStandbySupported

```TypeScript
readonly isStandbySupported?: boolean
```

卡片是否支持在灵动显示界面展示。 - true：支持灵动显示。 - false：不支持灵动显示。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FormInfo-readonly isStandbySupported?: boolean--><!--Device-FormInfo-readonly isStandbySupported?: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## isTemplateForm

```TypeScript
readonly isTemplateForm?: boolean
```

表示卡片是否是模板卡。 - true：是模板卡。 - false：不是模板卡。

**类型：** boolean

**起始版本：** 23

<!--Device-FormInfo-readonly isTemplateForm?: boolean--><!--Device-FormInfo-readonly isTemplateForm?: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## previewImages

```TypeScript
readonly previewImages?: Array<int>
```

卡片预览图资源ID。 **说明：** 值为正整数的数组。

**类型：** Array&lt;int&gt;

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-FormInfo-readonly previewImages?: Array<int>--><!--Device-FormInfo-readonly previewImages?: Array<int>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## renderingMode

```TypeScript
readonly renderingMode?: RenderingMode
```

卡片渲染模式。

**类型：** [RenderingMode](arkts-form-forminfo-renderingmode-e-sys.md)

**起始版本：** 23

<!--Device-FormInfo-readonly renderingMode?: RenderingMode--><!--Device-FormInfo-readonly renderingMode?: RenderingMode-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## resizable

```TypeScript
readonly resizable?: boolean
```

表示是否可以拖拽卡片调整大小。调整值必须在该卡片或者同groupId卡片的supportDimensions配置列表中。 - true：可以调整大小。 - false：不可以调整大小。

**类型：** boolean

**起始版本：** 23

<!--Device-FormInfo-readonly resizable?: boolean--><!--Device-FormInfo-readonly resizable?: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## sceneAnimationParams

```TypeScript
readonly sceneAnimationParams?: SceneAnimationParams
```

场景动效卡片配置参数。主要配置互动卡片触发方式和禁用手势等参数。

**类型：** [SceneAnimationParams](arkts-form-forminfo-sceneanimationparams-i-sys.md)

**起始版本：** 23

<!--Device-FormInfo-readonly sceneAnimationParams?: SceneAnimationParams--><!--Device-FormInfo-readonly sceneAnimationParams?: SceneAnimationParams-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

