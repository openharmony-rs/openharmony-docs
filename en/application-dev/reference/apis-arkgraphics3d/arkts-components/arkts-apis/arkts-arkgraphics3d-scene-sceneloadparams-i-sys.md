# SceneLoadParams (System API)

Scene load parameters object, used to specify additional configuration options when loading 3D model resources. A typical use case is loading an embedded glb model from an MP4 container file.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## offset

```TypeScript
offset?: number
```

The offset of the start of the 3D model data in the resource Unit: byte, The value must be greater than or equal to 0. Default value: 0.

**Type:** number

**Default:** 0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.
