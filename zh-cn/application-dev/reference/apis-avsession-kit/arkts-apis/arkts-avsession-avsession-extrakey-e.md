# ExtraKey

表示定义在不同场景中使用的额外键的枚举。

**起始版本：** 26.0.0

<!--Device-avSession-enum ExtraKey--><!--Device-avSession-enum ExtraKey-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## REQUIRE_ABILITY_LIST

```TypeScript
REQUIRE_ABILITY_LIST = 'requireAbilityList'
```

作为[setExtras](arkts-avsession-avsession-avsession-i.md#setextras))}接口传入的键，用于向系统设置应用所需的能力列表。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExtraKey-REQUIRE_ABILITY_LIST = 'requireAbilityList'--><!--Device-ExtraKey-REQUIRE_ABILITY_LIST = 'requireAbilityList'-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## SUPPORT_URL_CASTING

```TypeScript
SUPPORT_URL_CASTING = 'url-cast'
```

作为[setExtras](arkts-avsession-avsession-avsession-i.md#setextras))}接口，给REQUIRE_ABILITY_LIST键传入能力列表的值，用于通知系统当前应用支持URL投播功能。

[setExtras](arkts-avsession-avsession-avsession-i.md#setextras))}接口传入入参`{[avSession.ExtraKey.REQUIRE_ABILITY_LIST]: [avSession.ExtraKey.SUPPORT_URL_CASTING]}`表示当前应用支持投播功能。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExtraKey-SUPPORT_URL_CASTING = 'url-cast'--><!--Device-ExtraKey-SUPPORT_URL_CASTING = 'url-cast'-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## DLNA_CURRENT_URI_METADATA

```TypeScript
DLNA_CURRENT_URI_METADATA = 'CurrentURIMetadata'
```

[AVMediaDescription](arkts-avsession-avsession-avmediadescription-i.md)中extras属性可传入的键，值传入string类型。

用于DLNA投播场景下，在发送给对端的报文中，为CurrentURIMetaData标签添加内容。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExtraKey-DLNA_CURRENT_URI_METADATA = 'CurrentURIMetadata'--><!--Device-ExtraKey-DLNA_CURRENT_URI_METADATA = 'CurrentURIMetadata'-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## DLNA_DIDL_LITE

```TypeScript
DLNA_DIDL_LITE = 'DIDL-Lite'
```

[AVMediaDescription](arkts-avsession-avsession-avmediadescription-i.md)中extras属性可传入的键，值传入string类型。

用于DLNA投播场景下，在发送给对端的报文中，为DIDL-Lite标签添加内容。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ExtraKey-DLNA_DIDL_LITE = 'DIDL-Lite'--><!--Device-ExtraKey-DLNA_DIDL_LITE = 'DIDL-Lite'-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

