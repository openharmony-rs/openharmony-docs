# SettingsChangeEvent

```TypeScript
type SettingsChangeEvent = (settingItem: SettingItem) => Promise<SettingItem>
```

设置变更事件类型。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type SettingsChangeEvent = (settingItem: SettingItem) => Promise<SettingItem>--><!--Device-avMusicTemplate-type SettingsChangeEvent = (settingItem: SettingItem) => Promise<SettingItem>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| settingItem | [SettingItem](arkts-avsession-avmusictemplate-settingitem-i.md) | 是 | 设置项。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SettingItem&gt; | Promise对象，返回变更过的设置项。  |

