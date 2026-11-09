# OH_UDMF_VirtualFileCallbacks

```c
struct OH_UDMF_VirtualFileCallbacks {...}
```

## Overview

Describes the callbacks used to provide virtual file metadata and content.<br> <code>structSize</code> must be set to <code>sizeof(OH_UDMF_VirtualFileCallbacks)</code>. <code>onRead</code> is mandatory, and <code>onStat</code> and <code>onCancel</code> are optional. All files must be pre-declared in size. Set <code>onCancel</code> to nullptr if you do not need to cancel the notification. Different threads may invoke callbacks concurrently. Callbacks cannot be blocked indefinitely.

<!--Device-struct OH_UDMF_VirtualFileCallbacks {...}--><!--Device-struct OH_UDMF_VirtualFileCallbacks {...}-End-->

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 26.1.0

**Related module**: [UDMF](capi-arkdata-udmf.md)

**Header file**: [uds.h](capi-uds-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t structSize | Structure size.<br>**Since**: 26.1.0 |
| [OH_UDMF_VirtualFileOnStat](capi-uds-h.md#oh_udmf_virtualfileonstat) onStat | Optional metadata callback.<br>**Since**: 26.1.0 |
| [OH_UDMF_VirtualFileOnRead](capi-uds-h.md#oh_udmf_virtualfileonread) onRead | Mandatory content read callback.<br>**Since**: 26.1.0 |
| [OH_UDMF_VirtualFileOnCancel](capi-uds-h.md#oh_udmf_virtualfileoncancel) onCancel | Optional cancel callback. If the value is nullptr, the cancellation is successful and the provider is not notified.<br>**Since**: 26.1.0 |


