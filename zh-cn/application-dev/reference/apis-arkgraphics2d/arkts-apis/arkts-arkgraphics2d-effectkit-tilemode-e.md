# TileMode

着色器效果平铺模式的枚举。 > **说明：** > > CPU渲染下，着色器平铺模式仅支持DECAL。GPU渲染下，DECAL、CLAMP、REPEAT、MIRROR模式均支持。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-effectKit-enum TileMode--><!--Device-effectKit-enum TileMode-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## CLAMP

```TypeScript
CLAMP = 0
```

如果着色器效果超出其原始边界，剩余区域使用着色器的边缘颜色填充。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TileMode-CLAMP = 0--><!--Device-TileMode-CLAMP = 0-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## REPEAT

```TypeScript
REPEAT = 1
```

在水平和垂直方向上重复着色器效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TileMode-REPEAT = 1--><!--Device-TileMode-REPEAT = 1-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## MIRROR

```TypeScript
MIRROR = 2
```

在水平和垂直方向上重复着色器效果，交替镜像图像，以便相邻图像始终接合。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TileMode-MIRROR = 2--><!--Device-TileMode-MIRROR = 2-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## DECAL

```TypeScript
DECAL = 3
```

仅在其原始边界内渲染着色器效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-TileMode-DECAL = 3--><!--Device-TileMode-DECAL = 3-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

