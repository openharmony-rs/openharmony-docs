# SettingsChangeEvent

```TypeScript
type SettingsChangeEvent = (settingItem: SettingItem) => Promise<SettingItem>
```

The settings change event.

@typedef { function } SettingsChangeEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| settingItem | [SettingItem](arkts-avsession-avmusictemplate-settingitem-i.md) | Yes | setting item |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SettingItem](arkts-avsession-avmusictemplate-settingitem-i.md)&gt; | (SettingItem) returned through promise |
