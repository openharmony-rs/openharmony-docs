# AgentAppInfo

Agent的应用信息。

**起始版本：** 24

<!--Device-unnamed-export interface AgentAppInfo--><!--Device-unnamed-export interface AgentAppInfo-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## abilityName

```TypeScript
abilityName: string
```

Agent所属AgentExtensionAbility的Ability名称。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentAppInfo-abilityName: string--><!--Device-AgentAppInfo-abilityName: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

Agent所属AgentExtensionAbility的Bundle名称。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentAppInfo-bundleName: string--><!--Device-AgentAppInfo-bundleName: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## deviceTypes

```TypeScript
deviceTypes?: Array<string>
```

Agent支持的设备类型列表。取值范围参考[deviceTypes](../../../quick-start/module-configuration-file.md#devicetypes标签)。

**类型：** Array&lt;string&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentAppInfo-deviceTypes?: Array<string>--><!--Device-AgentAppInfo-deviceTypes?: Array<string>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## minAppVersion

```TypeScript
minAppVersion?: string
```

Agent运行的最低应用版本要求。使用语义化版本号格式（如"1.0.0"），指定运行该Agent所需的应用最低版本。低于此版本的应用将无法正确加载和运行该Agent。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentAppInfo-minAppVersion?: string--><!--Device-AgentAppInfo-minAppVersion?: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

## moduleName

```TypeScript
moduleName: string
```

Agent所属AgentExtensionAbility的Module名称。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AgentAppInfo-moduleName: string--><!--Device-AgentAppInfo-moduleName: string-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

