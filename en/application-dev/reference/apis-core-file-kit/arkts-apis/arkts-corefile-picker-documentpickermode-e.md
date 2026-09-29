# DocumentPickerMode

```TypeScript
export enum DocumentPickerMode
```

Enumerates the modes for saving documents.

**Since:** 12

<!--Device-picker-export enum DocumentPickerMode--><!--Device-picker-export enum DocumentPickerMode-End-->

**System capability:** SystemCapability.FileManagement.UserFileService

## DEFAULT

```TypeScript
DEFAULT = 0
```

Standard mode.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DocumentPickerMode-DEFAULT = 0--><!--Device-DocumentPickerMode-DEFAULT = 0-End-->

**System capability:** SystemCapability.FileManagement.UserFileService

## DOWNLOAD

```TypeScript
DOWNLOAD = 1
```

Download mode.

**Note:**  The directories created in DOWNLOAD mode are used only to save files. There is no access isolation between directories. You are advised not to save sensitive application data.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-DocumentPickerMode-DOWNLOAD = 1--><!--Device-DocumentPickerMode-DOWNLOAD = 1-End-->

**System capability:** SystemCapability.FileManagement.UserFileService
