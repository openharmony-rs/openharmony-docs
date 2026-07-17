# SettingContent

设置内容的定义（音频模板里有定义设置页面，设置内容用于设置页的填充）。

**起始版本：** 23

<!--Device-avMusicTemplate-interface SettingContent--><!--Device-avMusicTemplate-interface SettingContent-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## imageTags

```TypeScript
imageTags?: image.PixelMap[]
```

设置内容的图片标签数组。

**类型：** image.PixelMap[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SettingContent-imageTags?: image.PixelMap[]--><!--Device-SettingContent-imageTags?: image.PixelMap[]-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## isSelected

```TypeScript
isSelected: boolean
```

是否选择设置项内容。true表示选择，false表示不选择。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SettingContent-isSelected: boolean--><!--Device-SettingContent-isSelected: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## textTags

```TypeScript
textTags?: string[]
```

设置内容的描述的数组。

**类型：** string[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SettingContent-textTags?: string[]--><!--Device-SettingContent-textTags?: string[]-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## value

```TypeScript
value: string
```

设置的内容。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SettingContent-value: string--><!--Device-SettingContent-value: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

