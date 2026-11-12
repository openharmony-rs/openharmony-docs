# ShortcutInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=eba81a7f1473f18663b6ac51b186853c585433f7 translatedAt=2026-11-03T13:26:37.581Z pushedAt=2026-11-04T06:23:07.024Z nl=1 -->

Defines the shortcut types used by system applications.

> **NOTE**
>
> This page contains only the system API parameters of this module. For other public parameter definitions, see [ShortcutInfo](js-apis-bundleManager-shortcutInfo.md).

**Since:** 26.1.0

## Modules to Import

```ts
import { shortcutManager } from '@kit.AbilityKit';
```

## ShortcutWant

Defines the target information set in a shortcut.

**System capability**: SystemCapability.BundleManager.BundleFramework.Launcher

**System API**: This is a system API.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

| Name               | Type                                    | Read-only | Optional | Description                 |
| ------------------ | --------------------------------------- | --- | --- | -------------------- |
| action            | string                                  | No   | Yes  | Operation to perform when launching the shortcut. |
| uri               | string                                  | No   | Yes  | URI to match when launching the shortcut. |
| flags             | number                                  | No   | Yes  | How the Want object is processed when launching the shortcut. The value is an enumerated value of [Flags](js-apis-app-ability-wantConstant.md#flags). |
