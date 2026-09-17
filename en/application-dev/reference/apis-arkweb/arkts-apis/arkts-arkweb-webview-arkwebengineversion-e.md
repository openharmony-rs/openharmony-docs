# ArkWebEngineVersion

For ArkWeb kernel versions, see [Adaptation Guide for the M114 Kernel on OpenHarmony 6.0](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_6.0.md) and [Adaptation Guide for the M132 Kernel on OpenHarmony 7.0](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/CompatibleWithLegacyWebEngine_7.0.md).

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## SYSTEM_DEFAULT

```TypeScript
SYSTEM_DEFAULT = 0
```

System default kernel (see [Constraints](../../../web/web-component-overview.md#constraints)). The default kernel is M132 for OpenHarmony 6.0 and M144 for OpenHarmony 7.0.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## M114

```TypeScript
M114 = 1
```

Legacy kernel of OpenHarmony 6.0. Developers can select this legacy kernel. If this kernel does not exist on the system version, the setting does not take effect and the system default kernel is used.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## M132

```TypeScript
M132 = 2
```

Evergreen kernel of OpenHarmony 6.0 (legacy kernel of OpenHarmony 7.0). M132 is the default kernel of OpenHarmony 6.0. If this kernel does not exist on the system version, the setting does not take effect and the system default kernel is used.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## M144

```TypeScript
M144 = 3
```

Evergreen kernel of OpenHarmony 7.0. M144 is the default kernel of OpenHarmony 7.0. If this kernel does not exist on the system version, the setting does not take effect and the system default kernel is used.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## ARKWEB_EVERGREEN

```TypeScript
ARKWEB_EVERGREEN = 99999
```

The latest kernel (evergreen kernel) of the system. Developers can select this kernel to always use the latest kernel on each system version.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core
