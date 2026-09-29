# VisibilityType

```TypeScript
enum VisibilityType
```

The visibility of a form.

**Since:** 9

<!--Device-formInfo-enum VisibilityType--><!--Device-formInfo-enum VisibilityType-End-->

**System capability:** SystemCapability.Ability.Form

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

Indicates the type of the form type is unknown. Often used as a condition variable in function OnVisibilityChange to specify actions only on forms that are changing to unknown.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-VisibilityType-UNKNOWN = 0--><!--Device-VisibilityType-UNKNOWN = 0-End-->

**System capability:** SystemCapability.Ability.Form

## FORM_VISIBLE

```TypeScript
FORM_VISIBLE = 1
```

Indicates the type of the form is visible. Often used as a condition variable in function OnVisibilityChange to specify actions only on forms that are changing to visible.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-VisibilityType-FORM_VISIBLE = 1--><!--Device-VisibilityType-FORM_VISIBLE = 1-End-->

**System capability:** SystemCapability.Ability.Form

## FORM_INVISIBLE

```TypeScript
FORM_INVISIBLE = 2
```

Indicates the type of the form is invisible. Often used as a condition variable in function OnVisibilityChange to specify actions only on forms that are changing to invisible.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-VisibilityType-FORM_INVISIBLE = 2--><!--Device-VisibilityType-FORM_INVISIBLE = 2-End-->

**System capability:** SystemCapability.Ability.Form
