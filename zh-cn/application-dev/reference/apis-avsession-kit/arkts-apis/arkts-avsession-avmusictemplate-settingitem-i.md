# SettingItem

设置项的定义。@interface SettingItem

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## desc

```TypeScript
desc: string
```

设置项的描述。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## id

```TypeScript
id: string
```

设置项的唯一ID。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## mediaId

```TypeScript
mediaId: string
```

与当前设置关联的媒体ID。如果设置与当前媒体信息相关联，需要设置mediaId；否则，不需要设置mediaId。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## settingType

```TypeScript
settingType?: SettingType
```

设置项的类型。

**类型：** [SettingType](arkts-avsession-avmusictemplate-settingtype-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## settingValue

```TypeScript
settingValue?: string | boolean | SettingContent[] | WantAgent
```

设置项的值。  
- 当settingType为SettingType.SWITCH时，该值为boolean类型。  
- 当settingType为SettingType.LIST时，该值为SettingContent数组。  
- 当settingType为SettingType.JUMP时，该值为string类型。

**类型：** string \| boolean \| [SettingContent](arkts-avsession-avmusictemplate-settingcontent-i.md)[] \| [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## title

```TypeScript
title: string
```

设置项的标题。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate
