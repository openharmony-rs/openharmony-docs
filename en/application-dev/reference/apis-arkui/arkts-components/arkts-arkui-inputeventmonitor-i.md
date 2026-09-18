# InputEventMonitor

Input event monitor identity object.

This object is created and returned by the system, serving as the unique identifier of the monitor.

> **NOTE:** 
> 
> - The object is empty and does not contain any accessible members.
> 
> - Developers cannot create this object on their own. It can only be obtained by registering through the addLocalInputEventMonitor API.
> 
> - It is used for identity verification when unregistering later.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
