# AtomicServiceMenuBar (System API)

Creates an **AtomicServiceMenuBar** object based on the context of the current atomic service. The object is used to control the display of the menu function capsule in the upper right corner.

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { AtomicServiceMenuBar } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(uiContext: UIContext)
```

A constructor used to create an **AtomicServiceMenuBar** object.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiContext | UIContext | Yes | Context information of the current atomic service. |

## setVisible

```TypeScript
public setVisible(visible: boolean): void
```

Sets whether to display or hide the menu function capsule of the current atomic service.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| visible | boolean | Yes | Expected status of the menu function capsule. true: The menu function capsule is displayed. false: The menu function capsule is hidden. |
