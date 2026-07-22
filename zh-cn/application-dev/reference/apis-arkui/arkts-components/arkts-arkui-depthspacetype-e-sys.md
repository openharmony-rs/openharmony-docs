# DepthSpaceType（系统接口）

景深空间类型枚举。
> **说明：**  
>  
> 全局模式下，其余进程复用壁纸进程的背景、深度图及相机和光照参数，且不可自定义。

**起始版本：** 26.0.0

<!--Device-unnamed-declare enum DepthSpaceType--><!--Device-unnamed-declare enum DepthSpaceType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## INSTANCE

```TypeScript
INSTANCE = 0
```

实例模式。使用当前进程的背景、深度图、相机参数及光照参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DepthSpaceType-INSTANCE = 0--><!--Device-DepthSpaceType-INSTANCE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## GLOBAL

```TypeScript
GLOBAL = 1
```

全局模式。使用全局的背景、深度图、相机参数及光照参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DepthSpaceType-GLOBAL = 1--><!--Device-DepthSpaceType-GLOBAL = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

