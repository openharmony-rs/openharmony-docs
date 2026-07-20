# ExecuteModeForConfiguration（系统接口）

[使用配置文件开发的意图](docroot://application-models/insight-intent-config-development.md)支持的意图执行模式。例如，将[insight_intent.json配置文件](docroot://application-models/insight-intent-config-development.md#insight_intentjson配置文件说明)中的executeMode设置为"foreground"，表示支持与UIAbility组件绑定的意图在前台运行。

**起始版本：** 23

<!--Device-insightIntentDriver-enum ExecuteModeForConfiguration--><!--Device-insightIntentDriver-enum ExecuteModeForConfiguration-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## FOREGROUND

```TypeScript
FOREGROUND = 0
```

表示支持与UIAbility组件绑定的意图在前台运行。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecuteModeForConfiguration-FOREGROUND = 0--><!--Device-ExecuteModeForConfiguration-FOREGROUND = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## BACKGROUND

```TypeScript
BACKGROUND = 1
```

表示支持与UIAbility组件绑定的意图在后台运行。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExecuteModeForConfiguration-BACKGROUND = 1--><!--Device-ExecuteModeForConfiguration-BACKGROUND = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

