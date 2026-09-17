# PageIntentDecoratorInfo

PageIntentDecoratorInfo inherits from [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md) and describes the parameters supported by the [@InsightIntentPage](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentpage) decorator, such as the name of [NavDestination](../../apis-arkui/arkts-components/arkts-arkui-navigation-comp-attribute.md#navdestination) of the target page.

**Inheritance/Implementation:** PageIntentDecoratorInfo extends [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)

**Since:** 20

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { InsightIntentLink, InsightIntentPage, InsightIntentFunctionMethod, InsightIntentFunction, InsightIntentEntry, LinkParamCategory, InsightIntentForm, InsightIntentEntity } from '@kit.AbilityKit';
```

## navDestinationName

```TypeScript
navDestinationName?: string
```

Name of the [navDestination](../../apis-arkui/arkts-components/arkts-arkui-navigation-comp-attribute.md#navdestination) component bound to the intent.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## navigationId

```TypeScript
navigationId?: string
```

ID of the [NavDestination组件](../../apis-arkui/arkts-components/arkts-arkui-navigation-comp-attribute.md#navigationattribute) component bound to the intent.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## pagePath

```TypeScript
pagePath: string
```

Path of the page bound to the intent. The page must be a file that actually exists.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## uiAbility

```TypeScript
uiAbility?: string
```

Name of the UIAbility bound to the intent.

**Type:** string

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
