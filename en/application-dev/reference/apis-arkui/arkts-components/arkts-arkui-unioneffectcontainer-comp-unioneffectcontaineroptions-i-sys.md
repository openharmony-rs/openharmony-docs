# UnionEffectContainerOptions (System API)

```TypeScript
declare interface UnionEffectContainerOptions
```

Sets the construction options of **UnionEffectContainer**.

**Since:** 23

<!--Device-unnamed-declare interface UnionEffectContainerOptions--><!--Device-unnamed-declare interface UnionEffectContainerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## spacing

```TypeScript
spacing?: number
```

Degree of union deformation that occurs between descendant components. It does not represent the actual spacing. Union occurs only when descendant components that use the union effect of the ancestor **UnionEffectContainer** component are set and come close to a certain degree.

**NOTE:** 

If **spacing** is set to a value greater than 0 and descendant components that use the union effect of the ancestor **UnionEffectContainer** component come close to a certain degree, these descendant components start to fuse and deform with each other, and the union deformation effect becomes stronger as the distance decreases. A larger value causes the union to start earlier and makes union deformation more likely to occur when descendant components come close to each other.

Default value: **0**, in which case the shapes of descendant components fuse together without any deformation effect.

Value range: [0, +∞). Values less than 0 are treated as 0.

**Type:** number

**Default:** 0

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-UnionEffectContainerOptions-spacing?: number--><!--Device-UnionEffectContainerOptions-spacing?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
