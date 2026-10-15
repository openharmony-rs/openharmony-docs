# @ohos.connectedTag(Active Tags)

The **connectedTag** module provides APIs for using active tags. You can use the APIs to initialize the active tag chip and read and write active tags.

**Since:** 8

<!--Device-unnamed-declare namespace connectedTag--><!--Device-unnamed-declare namespace connectedTag-End-->

**System capability:** SystemCapability.Communication.ConnectedTag

## Modules to Import

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [initialize](arkts-connectivity-connectedtag-initialize-f.md#initialize) | Initializes the active tag chip. |
| [off('notify')](arkts-connectivity-connectedtag-off-f.md#offnotify) | Unregisters the NFC field strength state events. |
| [on('notify')](arkts-connectivity-connectedtag-on-f.md#onnotify) | Registers the NFC field strength state events. |
| [read](arkts-connectivity-connectedtag-read-f.md#read1) | Reads the content of this active tag. This API uses a promise to return the result. |
| [read](arkts-connectivity-connectedtag-read-f.md#read2) | Reads the content of this active tag. This API uses an asynchronous callback to return the result. |
| [uninitialize](arkts-connectivity-connectedtag-uninitialize-f.md#uninitialize) | Uninitializes the active tag resources. |
| [write](arkts-connectivity-connectedtag-write-f.md#write1) | Writes data to this active tag. This API uses a promise to return the result. |
| [write](arkts-connectivity-connectedtag-write-f.md#write2) | Writes data to this active tag. This API uses an asynchronous callback to return the result. |
| [init](arkts-connectivity-connectedtag-init-f.md#init) | Initializes the active tag chip. |
| [readNdefTag](arkts-connectivity-connectedtag-readndeftag-f.md#readndeftag1) | Reads the content of this active tag. This API uses a promise to return the result. |
| [readNdefTag](arkts-connectivity-connectedtag-readndeftag-f.md#readndeftag2) | Reads the content of this active tag. This API uses an asynchronous callback to return the result. |
| [uninit](arkts-connectivity-connectedtag-uninit-f.md#uninit) | Uninitializes the active tag resources. |
| [writeNdefTag](arkts-connectivity-connectedtag-writendeftag-f.md#writendeftag1) | Writes data to this active tag. This API uses a promise to return the result. |
| [writeNdefTag](arkts-connectivity-connectedtag-writendeftag-f.md#writendeftag2) | Writes data to this active tag. This API uses an asynchronous callback to return the result. |

### Enums

| Name | Description |
| --- | --- |
| [NfcRfType](arkts-connectivity-connectedtag-nfcrftype-e.md) | Enumerates the NFC field strength states. |
