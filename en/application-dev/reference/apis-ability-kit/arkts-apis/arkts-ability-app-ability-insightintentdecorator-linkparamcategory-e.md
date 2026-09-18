# LinkParamCategory

Enumerates the intent parameter categories available for the [@InsightIntentLink](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink) decorator. The enum is used to define how intent parameters should be passed.

**Since:** 20

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## LINK

```TypeScript
LINK = 'link'
```

Category of link. Intent parameters are appended to the end of a URI link and passed to the application via the URI.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## WANT

```TypeScript
WANT = 'want'
```

Category of want. Intent parameters are passed to the application through the **parameters** field in [Want](arkts-ability-app-ability-want-want-c.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
