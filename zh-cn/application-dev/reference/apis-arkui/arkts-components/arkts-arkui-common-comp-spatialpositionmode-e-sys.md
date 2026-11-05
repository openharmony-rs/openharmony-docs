# SpatialPositionMode（系统接口）

```TypeScript
declare enum SpatialPositionMode
```

空间位置模式。表示角点位置使用的坐标系。

**起始版本：** 26.0.0

<!--Device-unnamed-declare enum SpatialPositionMode--><!--Device-unnamed-declare enum SpatialPositionMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## NDC_XY_WORLD_Z

```TypeScript
NDC_XY_WORLD_Z = 1
```

NDC XY与世界Z坐标系模式。X、Y分量使用NDC（标准化设备坐标系），Z分量使用世界坐标。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-SpatialPositionMode-NDC_XY_WORLD_Z = 1--><!--Device-SpatialPositionMode-NDC_XY_WORLD_Z = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## WORLD_XYZ

```TypeScript
WORLD_XYZ = 0
```

世界XYZ坐标系模式。X、Y、Z分量均使用世界坐标。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-SpatialPositionMode-WORLD_XYZ = 0--><!--Device-SpatialPositionMode-WORLD_XYZ = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
