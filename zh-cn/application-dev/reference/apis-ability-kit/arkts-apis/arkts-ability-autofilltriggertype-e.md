# AutoFillTriggerType

```TypeScript
export enum AutoFillTriggerType
```

自动填充服务的拉起类型，通过用户手势操作来选择不同的自动填充服务拉起方式。

**起始版本：** 26.0.0

<!--Device-unnamed-export enum AutoFillTriggerType--><!--Device-unnamed-export enum AutoFillTriggerType-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## AUTO_REQUEST

```TypeScript
AUTO_REQUEST = 0
```

自动拉起自动填充服务，可通过TextInput控件获焦后自动拉起。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-AutoFillTriggerType-AUTO_REQUEST = 0--><!--Device-AutoFillTriggerType-AUTO_REQUEST = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## MANUAL_REQUEST

```TypeScript
MANUAL_REQUEST = 1
```

手动拉起自动填充服务，可通过长按任意输入控件弹出二级菜单，选择自动填充，拉起自动填充服务。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-AutoFillTriggerType-MANUAL_REQUEST = 1--><!--Device-AutoFillTriggerType-MANUAL_REQUEST = 1-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

## PASTE_REQUEST

```TypeScript
PASTE_REQUEST = 2
```

粘贴拉起自动填充服务，仅在用户已从密码保险箱内长按用户名或密码选择安全复制后，通过长按任意输入控件弹出二级菜单并选择粘贴时拉起自动填充服务。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-AutoFillTriggerType-PASTE_REQUEST = 2--><!--Device-AutoFillTriggerType-PASTE_REQUEST = 2-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore
