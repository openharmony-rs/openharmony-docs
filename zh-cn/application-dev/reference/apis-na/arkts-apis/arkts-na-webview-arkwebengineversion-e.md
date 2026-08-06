# ArkWebEngineVersion

ArkWeb内核版本，请参考 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ ， \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_ 。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-webview-enum ArkWebEngineVersion--><!--Device-webview-enum ArkWebEngineVersion-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SYSTEM_DEFAULT

```TypeScript
SYSTEM_DEFAULT = 0
```

系统默认内核，OpenHarmony 6.0版本默认为M132，OpenHarmony 7.0版本默认为M144。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArkWebEngineVersion-SYSTEM_DEFAULT = 0--><!--Device-ArkWebEngineVersion-SYSTEM_DEFAULT = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## M114

```TypeScript
M114 = 1
```

OpenHarmony 6.0版本的遗留内核。开发者可选择此遗留内核，若系统版本上不存在此内核则设置无效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArkWebEngineVersion-M114 = 1--><!--Device-ArkWebEngineVersion-M114 = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## M132

```TypeScript
M132 = 2
```

OpenHarmony 6.0版本的常青内核（OpenHarmony 7.0版本的遗留内核），M132为OpenHarmony 6.0版本的默认内核。若系统版本上不存在此内核则设置无效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArkWebEngineVersion-M132 = 2--><!--Device-ArkWebEngineVersion-M132 = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## M144

```TypeScript
M144 = 3
```

OpenHarmony 7.0版本的常青内核，M144为OpenHarmony 7.0版本的默认内核。若系统版本上不存在此内核则设置无效。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-ArkWebEngineVersion-M144 = 3--><!--Device-ArkWebEngineVersion-M144 = 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ARKWEB_EVERGREEN

```TypeScript
ARKWEB_EVERGREEN = 99999
```

常青内核，系统的最新内核。开发者可选择在每个系统版本上都使用最新的内核，OpenHarmony开发套件（基于API 23）及之后所有系统版本都生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ArkWebEngineVersion-ARKWEB_EVERGREEN = 99999--><!--Device-ArkWebEngineVersion-ARKWEB_EVERGREEN = 99999-End-->

**系统能力：** SystemCapability.Web.Webview.Core

