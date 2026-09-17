# PolicyErrorResult

Failed policy result on URI.

@interface { object }

**Since:** 11

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

## Modules to Import

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## code

```TypeScript
code: PolicyErrorCode
```

Indicates the error code of the failure in the policy information.

**Type:** [PolicyErrorCode](arkts-corefile-fileshare-policyerrorcode-e.md)

**Since:** 11

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

## message

```TypeScript
message: string
```

Indicates the reason of the failure in the policy information.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

## uri

```TypeScript
uri: string
```

Indicates the failed uri of the policy information.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization
