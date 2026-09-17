# @ohos.dlpSetDlpFeature(DLP)

This module provides APIs for controlling the Data Loss Prevention (DLP) feature, including enabling or disabling the DLP feature and returning the DLP status. It helps enterprises meet data security compliance requirements and implement access control and encryption protection for confidential files.

**Use scenarios**

- Data security compliance requirements must be met.  
- Access control and encryption protection are provided for confidential files.

> **NOTE:** 
> - The initial APIs of this module are supported since API version 26.0.0. Newly added APIs will be marked with a
> - superscript to indicate their earliest API version.
> - The APIs provided by this module are system APIs.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { dlpSetDlpFeature } from '@kit.DataProtectionKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [setDlpFeature](arkts-dataprotection-dlpsetdlpfeature-setdlpfeature-f-sys.md) | Sets the DLP status. This API uses a promise to return the result. The system enables or disables the DLP protection function based on the DLP status specified using this API. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DLPFeatureInfo](arkts-dataprotection-dlpsetdlpfeature-dlpfeatureinfo-i-sys.md) | Sets the DLP status. |
| [StatusInfoResult](arkts-dataprotection-dlpsetdlpfeature-statusinforesult-i-sys.md) | Describes the DLP settings. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DlpFeatureStatus](arkts-dataprotection-dlpsetdlpfeature-dlpfeaturestatus-e-sys.md) | Enumerates DLP statuses. |
<!--DelEnd-->
