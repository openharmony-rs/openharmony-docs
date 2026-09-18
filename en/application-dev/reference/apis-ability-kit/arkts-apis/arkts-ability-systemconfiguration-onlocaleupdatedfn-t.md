# OnLocaleUpdatedFn

```TypeScript
type OnLocaleUpdatedFn = (locale: string) => void
```

Defines an OnLocaleUpdatedFn function.

@typedef { function }

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | Yes | Indicates the locale settings. The application will automatically adjust its behavior based on the current locale to meet the user's localization requirements. This property can be configured by setting the system language, system region, and application language preferences |
