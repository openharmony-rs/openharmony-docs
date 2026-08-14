# SceneLoadParams（系统接口）

加载场景的参数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export interface SceneLoadParams--><!--Device-unnamed-export interface SceneLoadParams-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## offset

```TypeScript
offset?: long
```

3D模型数据在资源文件中的起始偏移量，单位为字节。 系统将从资源文件的该偏移位置定位并读取glb模型数据。 例如，当glb模型嵌在MP4容器文件中时，可将此参数设置为glb数据在MP4文件中的起始字节位置，使系统能够正确提取并加载模型。 取值必须大于或等于0。默认值为0，表示模型数据从文件起始位置开始。

**类型：** long

**默认值：** { 0 }

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SceneLoadParams-offset?: long--><!--Device-SceneLoadParams-offset?: long-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

