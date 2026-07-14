# AutoFillTriggerType（系统接口）

自动填充服务的拉起类型，通过用户手势操作来选择不同的自动填充服务拉起方式。

**起始版本：** 23

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## AUTO_REQUEST

```TypeScript
AUTO_REQUEST = 0
```

自动拉起自动填充服务，可通过[TextInput](@internal/component/ets/text_input)控件获焦后自动拉起。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## MANUAL_REQUEST

```TypeScript
MANUAL_REQUEST = 1
```

手动拉起自动填充服务，可通过长按任意输入控件弹出二级菜单，选择自动填充，拉起自动填充服务。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

## PASTE_REQUEST

```TypeScript
PASTE_REQUEST = 2
```

粘贴拉起自动填充服务，可通过在密码保险箱内长按用户名或密码选择安全复制后，再长按任意输入控件弹出二级菜单，选择粘贴，拉起自动填充服务。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

