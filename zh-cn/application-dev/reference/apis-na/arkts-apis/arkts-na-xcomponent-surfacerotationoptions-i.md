# SurfaceRotationOptions

用于描述XComponent持有Surface在屏幕旋转时是否锁定方向的设置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface SurfaceRotationOptions--><!--Device-unnamed-export declare interface SurfaceRotationOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lock

```TypeScript
lock?: boolean
```

Surface在屏幕旋转时是否锁定方向，未设置时默认取值为false，即不锁定方向。 true：锁定方向；false：不锁定方向。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SurfaceRotationOptions-lock?: boolean--><!--Device-SurfaceRotationOptions-lock?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

