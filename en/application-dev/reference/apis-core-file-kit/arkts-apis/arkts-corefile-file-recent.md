# @ohos.file.recent(Latest Access List)

The **file.recent** module provides APIs for managing the list of recently accessed files.

> **NOTE:** 
> 
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs provided by this module are system APIs.
> - Currently, the APIs of this module can be called only by **FileManager**.
> - The APIs of this module are deprecated since API version 23. The following APIs are not recommended.

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { recent } from '@kit.CoreFileKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [add](arkts-corefile-recent-add-f-sys.md) | Adds the file of the specified URI to the recent file list. |
| [listFile](arkts-corefile-recent-listfile-f-sys.md) | Lists the files that are accessed recently. |
| [remove](arkts-corefile-recent-remove-f-sys.md) | Removes the file of the specified URI from the recent file list. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [FileInfo](arkts-corefile-recent-fileinfo-i-sys.md) | Represents information about the recent file list. |
<!--DelEnd-->
