# mkdtempSync

## Modules to Import

```TypeScript
```

## mkdtempSync

```TypeScript
declare function mkdtempSync(prefix: string): string
```

Creates a temporary directory. This API returns the result synchronously.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [mkdtempSync](arkts-corefile-file-fs-mkdtempsync-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| prefix | string | Yes | String to be replaced with six randomly generated characters to create a unique temporary directory. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Unique directory generated. |
