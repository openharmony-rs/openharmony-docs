# DocumentPickerMode

```TypeScript
export enum DocumentPickerMode
```

Enumerates the modes for saving documents.

**Since:** 12

**System capability:** SystemCapability.FileManagement.UserFileService

## DEFAULT

```TypeScript
DEFAULT = 0
```

Standard mode.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService

## DOWNLOAD

```TypeScript
DOWNLOAD = 1
```

Download mode.

**Note:**  The directories created in DOWNLOAD mode are used only to save files. There is no access isolation between directories. You are advised not to save sensitive application data.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.UserFileService
