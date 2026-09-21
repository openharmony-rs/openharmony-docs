# UnionEffectContainerOptions (System API)

```TypeScript
declare interface UnionEffectContainerOptions
```

Sets the construction options of **UnionEffectContainer**.

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## spacing

```TypeScript
spacing?: number
```

Degree of union deformation of the descendant component. This parameter does not represent the actual spacing. Union occurs only when the descendant components use the union effect of the ancestor component **UnionEffectContainer** and they come close to a certain extent. **NOTE:** If **spacing** is greater than 0 and the descendant components that use the union effect of the ancestor component **UnionEffectContainer** come close to a certain extent, the descendant components start to deform due to union. The closer the descendant components are, the stronger the deformation effect. A larger value indicates that the union of descendant components starts earlier and is more likely to occur when the descendant components come close to each other. The Value must be greater than or equal to 0. Default value: **0**.

**Type:** number

**Default:** 0

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
