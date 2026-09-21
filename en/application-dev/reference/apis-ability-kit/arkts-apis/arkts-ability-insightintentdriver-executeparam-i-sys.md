# ExecuteParam (System API)

```TypeScript
interface ExecuteParam
```

Defines the parameter used to execute an intent call.

**Since:** 11

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## abilityName

```TypeScript
abilityName: string
```

Name of the ability to be called. If an intent defined by the [@InsightIntentLink](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator is used to implement application redirection, this parameter can be left empty.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

Name of the bundle to which the ability to be called belongs.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## deviceId

```TypeScript
deviceId?: string
```

Indicates the device identifier. Obtained from [getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## displayId

```TypeScript
displayId?: number
```

Physical screen ID specified during intent call. The value must be an integer. This parameter is valid only when **executeMode** is set to **UI_ABILITY_FOREGROUND**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## executeMode

```TypeScript
executeMode: insightIntent.ExecuteMode
```

Intent execution mode. If an intent defined by the [@InsightIntentLink](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator is used to implement application redirection, this parameter must be filled (with any value that conforms to the definition), although it will not actually take effect.

**Type:** [insightIntent.ExecuteMode](arkts-ability-insightintent-executemode-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## flags

```TypeScript
flags?: number
```

[Flags](arkts-ability-wantconstant-flags-e.md) of the URIs authorized by the intent caller to the intent executor during the call.

**NOTE:** 

This parameter supports only **FLAG_AUTH_READ_URI_PERMISSION**, **FLAG_AUTH_WRITE_URI_PERMISSION**, and FLAG_AUTH_READ_URI_PERMISSION|

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## insightIntentName

```TypeScript
insightIntentName: string
```

Intent name.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## insightIntentParam

```TypeScript
insightIntentParam: Record<string, Object>
```

Intent call parameter.

**Type:** Record&lt;string, Object&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## moduleName

```TypeScript
moduleName: string
```

Name of the module to which the ability belongs.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## toolCallId

```TypeScript
toolCallId?: string
```

Indicates the tool call ID. Used to associate this intent execute with a test step.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

## uris

```TypeScript
uris?: Array<string>
```

List of URIs authorized by the intent caller to the intent executor during the call. If an intent defined by the [@InsightIntentLink](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator is used to implement application redirection, this field is mandatory. Only the first element in the array is read as the URI of [openLink](arkts-ability-uiabilitycontext-c.md#openlink).

**Type:** Array&lt;string&gt;

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

ID of the user to which the intent belongs.

**NOTE:** 

If the user ID of the calling application is different from the user ID of the intent, the calling application must request the ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
