# Metadata
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=d067d0e28903a909bd18e16fb4e6ef9702d944d0 translatedAt=2026-09-03T11:15:53.971Z pushedAt=2026-09-05T10:47:30.578Z -->

Represents a metadata object, which can be obtained through [bundleManager.getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself), where the **bundleFlags** parameter must contain at least GET_BUNDLE_INFO_WITH_METADATA. This object is included in [ApplicationInfo](js-apis-bundleManager-applicationInfo.md), [HapModuleInfo](js-apis-bundleManager-hapModuleInfo.md), [AbilityInfo](js-apis-bundleManager-abilityInfo.md), and [ExtensionAbilityInfo](js-apis-bundleManager-extensionAbilityInfo.md).

> **NOTE**
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
Describes the configuration information of module, uiAbility, and extensionAbility. The tag value is of the array type, and the configuration under this tag takes effect only for the current module, uiAbility, or extensionAbility.

## Modules to Import

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## Metadata

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
| Name     | Type   | Read-only | Optional | Description       |
| -------- | ------ | ---- | ---- | ---------- |
| name     | string | No   | No   | Metadata name. |
| value    | string | No   | No   | Metadata value.   |
| resource | string | No   | No   | Metadata resource descriptor. For example, $profile:config_file indicates that the config_file.json file is configured in the profile directory. |
| valueId<sup>18+</sup>  | number | Yes   | Yes   | Metadata value ID. When valueId is not 0, the current metadata value is a custom configuration, and valueId must be used to obtain the corresponding value from the resource manager. When valueId is 0, the current metadata value is a fixed string. |