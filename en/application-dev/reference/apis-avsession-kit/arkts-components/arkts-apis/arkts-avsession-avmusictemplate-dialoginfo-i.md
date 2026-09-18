# DialogInfo

The definition of dialog information.

@interface DialogInfo

**Since:** 23

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## Modules to Import

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## buttons

```TypeScript
buttons?: DialogButtonInfo[]
```

Buttons of the dialog.

**Type:** [DialogButtonInfo](arkts-avsession-avmusictemplate-dialogbuttoninfo-i.md)[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## description

```TypeScript
description?: string
```

Other message of the dialog.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## dialogId

```TypeScript
dialogId: string
```

Unique id of the dialog.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## dialogType

```TypeScript
dialogType: DialogType
```

Type of the dialog.

**Type:** [DialogType](arkts-avsession-avmusictemplate-dialogtype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## qrCodes

```TypeScript
qrCodes?: QrCodeInfo[]
```

QR code of the dialog. Once the QR code information is set, this pop-up will be recognized as a QR code pop-up and will display the QR code information with priority. A maximum of two can be set.

**Type:** [QrCodeInfo](arkts-avsession-avmusictemplate-qrcodeinfo-i.md)[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## text

```TypeScript
text?: string
```

Text content of the dialog.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## title

```TypeScript
title?: string
```

Title of the dialog.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate
