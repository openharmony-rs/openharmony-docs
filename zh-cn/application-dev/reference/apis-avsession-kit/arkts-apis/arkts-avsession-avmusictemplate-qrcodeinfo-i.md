# QrCodeInfo

二维码信息的定义。

**起始版本：** 23

<!--Device-avMusicTemplate-interface QrCodeInfo--><!--Device-avMusicTemplate-interface QrCodeInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## codeData

```TypeScript
codeData?: image.PixelMap
```

二维码图片。

**类型：** image.PixelMap

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QrCodeInfo-codeData?: image.PixelMap--><!--Device-QrCodeInfo-codeData?: image.PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## content

```TypeScript
content: string
```

二维码的内容。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QrCodeInfo-content: string--><!--Device-QrCodeInfo-content: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## detailName

```TypeScript
detailName: string
```

详情名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QrCodeInfo-detailName: string--><!--Device-QrCodeInfo-detailName: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## icon

```TypeScript
icon?: image.PixelMap
```

与二维码关联的应用图标，用于应用登录的二维码应显示目标应用的图标。

**类型：** image.PixelMap

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QrCodeInfo-icon?: image.PixelMap--><!--Device-QrCodeInfo-icon?: image.PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## id

```TypeScript
id: string
```

用于唯一标识用户登录的二维码会话。

当二维码过期时，MediaUI将使用此ID从媒体应用查询并更新新的二维码。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QrCodeInfo-id: string--><!--Device-QrCodeInfo-id: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## price

```TypeScript
price: string
```

购买价格。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QrCodeInfo-price: string--><!--Device-QrCodeInfo-price: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## tips

```TypeScript
tips: string
```

提示信息。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QrCodeInfo-tips: string--><!--Device-QrCodeInfo-tips: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## titleName

```TypeScript
titleName: string
```

标题名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QrCodeInfo-titleName: string--><!--Device-QrCodeInfo-titleName: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## validPeriod

```TypeScript
validPeriod: number
```

二维码有效期（单位：秒）。

当二维码到期时，二维码ID将用于再次查询并获得新的二维码。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-QrCodeInfo-validPeriod: int--><!--Device-QrCodeInfo-validPeriod: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

