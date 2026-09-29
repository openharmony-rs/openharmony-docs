# SettingItem

```TypeScript
interface SettingItem
```

The definition of setting Information.

@interface SettingItem

**Since:** 23

<!--Device-avMusicTemplate-interface SettingItem--><!--Device-avMusicTemplate-interface SettingItem-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## Modules to Import

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## desc

```TypeScript
desc: string
```

Description of the setting item.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-SettingItem-desc: string--><!--Device-SettingItem-desc: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## id

```TypeScript
id: string
```

Unique ID of the setting item.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-SettingItem-id: string--><!--Device-SettingItem-id: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## mediaId

```TypeScript
mediaId: string
```

Media id associated with the current settings. If the settings are associated with the current media information, you need to set the mediaId; otherwise, it is not required to set the mediaId.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-SettingItem-mediaId: string--><!--Device-SettingItem-mediaId: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## settingType

```TypeScript
settingType?: SettingType
```

Type of the setting item.

**Type:** [SettingType](arkts-avsession-avmusictemplate-settingtype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-SettingItem-settingType?: SettingType--><!--Device-SettingItem-settingType?: SettingType-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## settingValue

```TypeScript
settingValue?: string | boolean | SettingContent[] | WantAgent
```

Value of the setting item. SWITCH: bool, LIST: SettingContent, JUMP: string.

**Type:** string &#124; boolean &#124; [SettingContent](arkts-avsession-avmusictemplate-settingcontent-i.md)[] &#124; [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-SettingItem-settingValue?: string | boolean | SettingContent[] | WantAgent--><!--Device-SettingItem-settingValue?: string | boolean | SettingContent[] | WantAgent-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## title

```TypeScript
title: string
```

Title of the setting item.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-SettingItem-title: string--><!--Device-SettingItem-title: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate
