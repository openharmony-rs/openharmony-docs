# QrCodeInfo

```TypeScript
interface QrCodeInfo
```

The definition of QR code Information.

@interface QrCodeInfo

**Since:** 23

<!--Device-avMusicTemplate-interface QrCodeInfo--><!--Device-avMusicTemplate-interface QrCodeInfo-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## Modules to Import

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## codeData

```TypeScript
codeData?: image.PixelMap
```

QR code image.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-QrCodeInfo-codeData?: image.PixelMap--><!--Device-QrCodeInfo-codeData?: image.PixelMap-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## content

```TypeScript
content: string
```

QR code content.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-QrCodeInfo-content: string--><!--Device-QrCodeInfo-content: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## detailName

```TypeScript
detailName: string
```

Detail name.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-QrCodeInfo-detailName: string--><!--Device-QrCodeInfo-detailName: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## icon

```TypeScript
icon?: image.PixelMap
```

The icon of the app associated with the QR code, such as a QR code for logging in via WeChat, should be the WeChat icon.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-QrCodeInfo-icon?: image.PixelMap--><!--Device-QrCodeInfo-icon?: image.PixelMap-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## id

```TypeScript
id: string
```

A QR code session used to uniquely identify a user login. When the QR code expires, MediaUI will use this ID to query and update a new QR code from the third party.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-QrCodeInfo-id: string--><!--Device-QrCodeInfo-id: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## price

```TypeScript
price: string
```

Purchase price.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-QrCodeInfo-price: string--><!--Device-QrCodeInfo-price: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## tips

```TypeScript
tips: string
```

Tips message.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-QrCodeInfo-tips: string--><!--Device-QrCodeInfo-tips: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## titleName

```TypeScript
titleName: string
```

Title name.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-QrCodeInfo-titleName: string--><!--Device-QrCodeInfo-titleName: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## validPeriod

```TypeScript
validPeriod: number
```

QR code validity period (unit: seconds). When the QR code expires, the QR code ID will be used to query and obtain a new QR code again.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-QrCodeInfo-validPeriod: int--><!--Device-QrCodeInfo-validPeriod: int-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate
