# MenuAlignParams

```TypeScript
export interface MenuAlignParams
```

Sets the alignment between the drop-down list button and the drop-down list box.

**Since:** 18

<!--Device-unnamed-export interface MenuAlignParams--><!--Device-unnamed-export interface MenuAlignParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceSearch, InputFilterParams, SearchButtonParams, MenuAlignParams, SearchParams, SelectParams, OperationParams, } from '@kit.ArkUI';
```

## alignType

```TypeScript
alignType: MenuAlignType
```

Alignment type. Default value: **MenuAlignType.START**

**Type:** [MenuAlignType](../arkts-components/arkts-arkui-select-comp-menualigntype-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-MenuAlignParams-alignType: MenuAlignType--><!--Device-MenuAlignParams-alignType: MenuAlignType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

Offset of the drop-down list box relative to the drop-down list button after alignment based on the alignment type. Default value: **{dx: 0, dy: 0}**

**Type:** Offset

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-MenuAlignParams-offset?: Offset--><!--Device-MenuAlignParams-offset?: Offset-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
