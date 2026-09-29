# ViewData

```TypeScript
export default interface ViewData
```

The module defines the view data used for auto-fill.

**Since:** 26.0.0

<!--Device-unnamed-export default interface ViewData--><!--Device-unnamed-export default interface ViewData-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## bundleName

```TypeScript
bundleName: string
```

Bundle name. The value cannot exceed 512 characters.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ViewData-bundleName: string--><!--Device-ViewData-bundleName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## pageNodeInfos

```TypeScript
pageNodeInfos: Array<PageNodeInfo>
```

Information of the page nodes.

**Type:** Array&lt;[PageNodeInfo](arkts-ability-pagenodeinfo-i.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ViewData-pageNodeInfos: Array<PageNodeInfo>--><!--Device-ViewData-pageNodeInfos: Array<PageNodeInfo>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## pageRect

```TypeScript
pageRect: AutoFillRect
```

Coordinates, width, and height of the page. On PC/2-in-1 devices, the password vault is displayed as a pop-up. To ensure the pop-up position follows the input box, left and top must be set to 0.

**Type:** [AutoFillRect](arkts-ability-autofillrect-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ViewData-pageRect: AutoFillRect--><!--Device-ViewData-pageRect: AutoFillRect-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## pageUrl

```TypeScript
pageUrl: string
```

URL of the page.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ViewData-pageUrl: string--><!--Device-ViewData-pageUrl: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore
