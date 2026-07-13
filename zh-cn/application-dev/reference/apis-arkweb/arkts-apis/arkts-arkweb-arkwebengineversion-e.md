# ArkWebEngineVersion

ArkWeb内核版本，请参考
[M114内核在OpenHarmony 6.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_6.0.md)
，
[M132内核在OpenHarmony 7.0系统上的适配指导](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_7.0.md)
。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## SYSTEM_DEFAULT

```TypeScript
SYSTEM_DEFAULT = 0
```

系统默认内核，OpenHarmony 6.0版本默认为M132，OpenHarmony 7.0版本默认为M144。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## M114

```TypeScript
M114 = 1
```

OpenHarmony 6.0版本的遗留内核。开发者可选择此遗留内核，若系统版本上不存在此内核则设置无效。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## M132

```TypeScript
M132 = 2
```

OpenHarmony 6.0版本的常青内核（OpenHarmony 7.0版本的遗留内核），M132为OpenHarmony 6.0版本的默认内核。若系统版本上不存在此内核则设置无效。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## M144

```TypeScript
M144 = 3
```

OpenHarmony 7.0版本的常青内核，M144为OpenHarmony 7.0版本的默认内核。若系统版本上不存在此内核则设置无效。

26.0.0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

## ARKWEB_EVERGREEN

```TypeScript
ARKWEB_EVERGREEN = 99999
```

常青内核，系统的最新内核。开发者可选择在每个系统版本上都使用最新的内核，OpenHarmony开发套件（基于API 23）及之后所有系统版本都生效。

**起始版本：** 23

**系统能力：** SystemCapability.Web.Webview.Core

