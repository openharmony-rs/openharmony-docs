# OnBackupSizeReport (System API)

```TypeScript
type OnBackupSizeReport = (reportInfo: string) => void
```

function that returns backup datasize by bundleName.

@typedef {function} OnBackupSizeReport

**Since:** 18

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reportInfo | string | Yes | the scanned backup datasize infos. |
