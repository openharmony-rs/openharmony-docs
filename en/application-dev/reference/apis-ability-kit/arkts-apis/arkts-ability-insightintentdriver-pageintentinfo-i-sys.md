# PageIntentInfo (System API)

Describes the parameters supported by the [@InsightIntentPage](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentpage) decorator, such as the [NavDestination](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10) name of the target page.

**Since:** 20

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## navDestinationName

```TypeScript
readonly navDestinationName: string
```

Name of the [NavDestination](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10) component bound to the intent.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## navigationId

```TypeScript
readonly navigationId: string
```

ID of the Navigation component bound to the intent.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## pagePath

```TypeScript
readonly pagePath: string
```

Page name.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## uiAbility

```TypeScript
readonly uiAbility: string
```

Ability name.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
