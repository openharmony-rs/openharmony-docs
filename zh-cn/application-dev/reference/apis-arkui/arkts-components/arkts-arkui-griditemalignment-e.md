# GridItemAlignment

GridItem的对齐方式枚举。

> **说明：**  
>  
> 1、只有可滚动的Grid中，设置STRETCH参数会生效，其他场景不生效。

> 2、在Grid的一行中，如果每个GridItem都是大小规律的（只占一行一列），设置STRETCH参数会生效，存在跨行或跨列的GridItem的场景不生效。

> 3、设置STRETCH后，只有不设置高度的GridItem才会以当前行中最高的GridItem作为自己的高度，设置过高度的GridItem高度不会变化。

> 4、设置STRETCH后，Grid布局时会有额外的布局流程，可能会带来额外的性能开销。

**起始版本：** 12

<!--Device-unnamed-declare enum GridItemAlignment--><!--Device-unnamed-declare enum GridItemAlignment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

使用Grid的默认对齐方式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridItemAlignment-DEFAULT = 0--><!--Device-GridItemAlignment-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## STRETCH

```TypeScript
STRETCH = 1
```

以一行中的最高的GridItem作为其他GridItem的高度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridItemAlignment-STRETCH = 1--><!--Device-GridItemAlignment-STRETCH = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

