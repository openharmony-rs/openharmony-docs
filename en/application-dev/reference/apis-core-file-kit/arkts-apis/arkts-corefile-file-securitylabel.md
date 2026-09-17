# @ohos.file.securityLabel(Data Label)

The **securityLabel** module provides APIs for managing data security levels of files, including obtaining and setting file security levels.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { securityLabel } from '@kit.CoreFileKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getSecurityLabel](arkts-corefile-securitylabel-getsecuritylabel-f.md) | Obtains the data security level of a file or directory. If no data security level has been set, **s3** is returned by default. This API uses a promise to return the result. |
| [getSecurityLabel](arkts-corefile-securitylabel-getsecuritylabel-f.md) | Obtains the data security level of a file or directory. If no data security level has been set, **s3** is returned by default. This API uses an asynchronous callback to return the result. |
| [getSecurityLabelSync](arkts-corefile-securitylabel-getsecuritylabelsync-f.md) | Obtains the data security level of a file or directory in synchronous mode. If no data security level has been set, **s3** is returned by default. |
| [setSecurityLabel](arkts-corefile-securitylabel-setsecuritylabel-f.md) | Sets the data security level for a file or directory. The level can only be adjusted from low to high, or set to the same level. This API uses a promise to return the result. |
| [setSecurityLabel](arkts-corefile-securitylabel-setsecuritylabel-f.md) | Sets the data security level for a file or directory. The level can only be adjusted from low to high, or set to the same level. This API uses an asynchronous callback to return the result. |
| [setSecurityLabelSync](arkts-corefile-securitylabel-setsecuritylabelsync-f.md) | Sets the data security level for a file or directory in synchronous mode. The level can only be adjusted from low to high, or set to the same level. |

### Types

| Name | Description |
| --- | --- |
| [DataLevel](arkts-corefile-securitylabel-datalevel-t.md) | Represents the data security level. |
