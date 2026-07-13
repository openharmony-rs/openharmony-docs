# CustomData（系统接口）

拉起模态页面时，开发者可通过[reloadInModal](arkts-ability-autofillextensioncontext-c-sys.md#reloadinmodal-1)接口将自定义数据传递给自动填充服
务，并可通过自动填充服务的
[onFillRequest](./../@ohos.app.ability.AutoFillExtensionAbility:AutoFillExtensionAbility.onFillRequest)获取到该数据。

**起始版本：** 13

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## data

```TypeScript
data: Record<string, Object>
```

拉起模态页面时传递的自定义数据，该数据为Record类型。

**类型：** Record<string, Object>

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

