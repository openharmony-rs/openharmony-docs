# ArcAlphabetIndexerInterface

The **ArcAlphabetIndexer** component is an arc-shaped component designed for quick navigation through alphabetically sorted items. It can be integrated with container components to quickly locate items within the visible area.

> **NOTE:** 

> - This component can be used on phones, PCs, 2-in-1 devices, tablets, TVs, and wearables. In API version 22 and earlier versions, a compilation warning will be reported when this component is used on phones, PCs, 2-in-1devices, tablets, and TVs, but the component can still run properly.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcAlphabetIndexer, ArcAlphabetIndexerAttribute } from '@kit.ArkUI';
```

## [[Call]]

```TypeScript
(info: ArcAlphabetIndexerInitInfo): ArcAlphabetIndexerAttribute
```

Creates an instance of the **ArcAlphabetIndexer** component with initialization parameters.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [ArcAlphabetIndexerInitInfo](arkts-arkui-arkui-arcalphabetindexer-arcalphabetindexerinitinfo-i.md) | Yes | Initialization parameters for the **ArcAlphabetIndexer** component. |

**Return value:**

| Type | Description |
| --- | --- |
| [ArcAlphabetIndexerAttribute](arkts-arkui-arkui-arcalphabetindexer-arcalphabetindexerattribute-c.md) |  |
