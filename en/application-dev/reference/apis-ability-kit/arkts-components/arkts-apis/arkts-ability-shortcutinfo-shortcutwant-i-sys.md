# ShortcutWant

Describes a collection of target [Wants](../../../quick-start/module-configuration-file.md#wants) information defined within a shortcut.

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## action

```TypeScript
action?: string
```

Action to take when starting the shortcut, consistent with the **action** field of [Want](arkts-ability-app-ability-want-want-c.md#action). It is used with **uri** or **parameters** to specify the operation to be performed in implicit Want mode.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

**System API:** This is a system API.

## flags

```TypeScript
flags?: number
```

How the shortcut Want object will be handled. The value is of the enumeration type [Flags](arkts-ability-wantconstant-flags-e.md), consistent with the **flags** field of [Want](arkts-ability-app-ability-want-want-c.md#flags).

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

**System API:** This is a system API.

## uri

```TypeScript
uri?: string
```

URI to be matched when starting the shortcut, consistent with the **uri** field of [Want](arkts-ability-app-ability-want-want-c.md#uri).

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

**System API:** This is a system API.
