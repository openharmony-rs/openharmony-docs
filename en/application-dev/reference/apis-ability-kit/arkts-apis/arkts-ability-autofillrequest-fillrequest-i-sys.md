# FillRequest

```TypeScript
export interface FillRequest
```

Defines the information about an auto-fill request.

**Since:** 26.0.0

<!--Device-unnamed-export interface FillRequest--><!--Device-unnamed-export interface FillRequest-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## customData

```TypeScript
customData: CustomData
```

Custom data.

**Type:** [CustomData](arkts-ability-customdata-i-sys.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

<!--Device-FillRequest-customData: CustomData--><!--Device-FillRequest-customData: CustomData-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

## isPopup

```TypeScript
isPopup: boolean
```

Whether a dialog box is displayed for the auto-fill request.

**true**: A dialog box is displayed

**false**: A modal window is displayed

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-FillRequest-isPopup: boolean--><!--Device-FillRequest-isPopup: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.
