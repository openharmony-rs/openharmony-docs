# UnionMode (System API)

```TypeScript
declare enum UnionMode
```

Enumerates the union effect modes.

**Since:** 26.0.0

<!--Device-unnamed-declare enum UnionMode--><!--Device-unnamed-declare enum UnionMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## GRAVITY_UNION

```TypeScript
GRAVITY_UNION = 1
```

Union deformation effect under gravity, suitable for union scenarios that require simulating a gravitational attraction effect, such as the visual representation of attraction and approaching trends between elements.

**NOTE:** 

When this type is set, it takes effect only when used together with [useUnionEffect](arkts-arkui-common-comp-commonmethod-c-sys.md#useunioneffect2) and when **gravityCenter** of [GravityCenterOptions](arkts-arkui-common-comp-gravitycenteroptions-i-sys.md) is set to **true**. If the preceding conditions are not met, **GRAVITY_UNION** does not take effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UnionMode-GRAVITY_UNION = 1--><!--Device-UnionMode-GRAVITY_UNION = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## SMOOTH_UNION

```TypeScript
SMOOTH_UNION = 0
```

Smooth union deformation effect, suitable for union scenarios that require smooth transitions and natural connections.

**NOTE:** 

When this type is set, the union effect is produced only when descendant components set the [useUnionEffect](arkts-arkui-common-comp-commonmethod-c-sys.md#useunioneffect1) attribute.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UnionMode-SMOOTH_UNION = 0--><!--Device-UnionMode-SMOOTH_UNION = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
