# DialogInfo

对话框信息的定义。

@interface DialogInfo

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## buttons

```TypeScript
buttons?: DialogButtonInfo[]
```

对话框按钮的数组。

**类型：** [DialogButtonInfo](arkts-avsession-avmusictemplate-dialogbuttoninfo-i.md)[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## description

```TypeScript
description?: string
```

对话框的其他信息。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## dialogId

```TypeScript
dialogId: string
```

对话框的唯一ID。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## dialogType

```TypeScript
dialogType: DialogType
```

对话框的类型。

**类型：** [DialogType](arkts-avsession-avmusictemplate-dialogtype-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## qrCodes

```TypeScript
qrCodes?: QrCodeInfo[]
```

对话框二维码的数组。

当设置了二维码信息时，此对话框将被识别为二维码对话框，并将优先显示二维码信息。最多可以设置两个。

**类型：** [QrCodeInfo](arkts-avsession-avmusictemplate-qrcodeinfo-i.md)[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## text

```TypeScript
text?: string
```

对话框的内容。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## title

```TypeScript
title?: string
```

对话框的标题。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate
