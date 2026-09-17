# SceneAnimationParams（系统接口）

场景动效卡片配置参数。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## abilityName

```TypeScript
abilityName: string
```

场景动效 extensionAbility 名称，如卡片提供方LiveFormExtensionAbility名称。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## disabledDesktopBehaviors

```TypeScript
disabledDesktopBehaviors?: string
```

支持的取值包括SWIPE_DESKTOP（滑动桌面）、PULL_DOWN_SEARCH（下拉全搜）、LONG_CLICK（长按）、DRAG（拖动）。可以取值一个或多个，不同行为通过 | 拼接，例如SWIPE_DESKTOP| PULL_DOWN_SEARCH。缺省表示不禁用任何行为。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## triggerTypes

```TypeScript
triggerTypes?: Array<SceneAnimationTriggerType>
```

场景动效卡片触发类型。

**类型：** Array&lt;[SceneAnimationTriggerType](arkts-form-forminfo-sceneanimationtriggertype-e-sys.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。
