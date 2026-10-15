# PageIntentInfo (System API)

```TypeScript
interface PageIntentInfo
```

PageIntentInfo is used to describe the parameters supported by the [@InsightIntentPage](arkts-ability-app-ability-insightintentdecorator-insightintentpage-d.md#insightintentpage) decorator, for example, the [navDestination](../../apis-arkui/arkts-components/arkts-arkui-navdestination-comp.md) name of the target page.

**Since:** 20

<!--Device-insightIntentDriver-interface PageIntentInfo--><!--Device-insightIntentDriver-interface PageIntentInfo-End-->

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

Name of the [NavDestination](../../apis-arkui/arkts-components/arkts-arkui-navdestination-comp.md) component bound to the intent.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageIntentInfo-readonly navDestinationName: string--><!--Device-PageIntentInfo-readonly navDestinationName: string-End-->

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

<!--Device-PageIntentInfo-readonly navigationId: string--><!--Device-PageIntentInfo-readonly navigationId: string-End-->

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

<!--Device-PageIntentInfo-readonly pagePath: string--><!--Device-PageIntentInfo-readonly pagePath: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## uiAbility

```TypeScript
readonly uiAbility: string
```

Name of the UIAbility component.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageIntentInfo-readonly uiAbility: string--><!--Device-PageIntentInfo-readonly uiAbility: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
