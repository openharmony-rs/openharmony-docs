# HapModuleInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=ed9771a647e46c1bc2b91beefb7250a4e3e55152 translatedAt=2026-11-03T13:26:05.256Z pushedAt=2026-11-04T06:22:45.214Z nl=1 -->

The module defines the HAP module information. An application can obtain its own HAP module information through [getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself), with **GET_BUNDLE_INFO_WITH_HAP_MODULE** passed in for [bundleFlags](js-apis-bundleManager.md#bundleflag).

**Since:** 26.0.1

> **NOTE**
>
> This page contains only the system APIs of this module. For details about other public APIs, see [HapModuleInfo](js-apis-bundleManager-hapModuleInfo.md).

## Modules to Import

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## HapModuleInfo

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

<!--Table: 20%; 20%; 8%; 8%; 44%-->
| Name                              | Type                                                         | Read-only | Optional | Description                 |
| --------------------------------- | ------------------------------------------------------------ | ---- | ---- | -------------------- |
| codePhysicalPath                  | string                                                       | Yes   | Yes   | Physical installation path of the module.<br>**Model constraint:** This field can be used only in the Stage model.<br>**Starting version:** 26.0.1 |

