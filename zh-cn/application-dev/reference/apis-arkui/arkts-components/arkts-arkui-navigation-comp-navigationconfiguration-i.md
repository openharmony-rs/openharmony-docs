# NavigationConfiguration

```TypeScript
declare interface NavigationConfiguration
```

导航配置选项。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface NavigationConfiguration--><!--Device-unnamed-declare interface NavigationConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clearContentStackOnPrimaryNavigation

```TypeScript
clearContentStackOnPrimaryNavigation?: boolean
```

在导航分栏模式下，启用后，从主节点触发的导航会清除主节点之后的旧导航页面，同时保留当前操作创建的所有导航页面。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-NavigationConfiguration-clearContentStackOnPrimaryNavigation?: boolean--><!--Device-NavigationConfiguration-clearContentStackOnPrimaryNavigation?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## recyclePagesOnLowMemory

```TypeScript
recyclePagesOnLowMemory?: boolean
```

当收到低内存信号时，是否回收不可见页。启用时，导航在接收后回收不可见的NavDestination页面实例低内存压力通知。NavPathInfo是保留的，以后可以重新构造页面。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-NavigationConfiguration-recyclePagesOnLowMemory?: boolean--><!--Device-NavigationConfiguration-recyclePagesOnLowMemory?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stackSizeLimit

```TypeScript
stackSizeLimit?: number
```

导航页面堆栈大小限制。说明：-限制导航页面堆栈中活动页面节点的最大数量。-超过限制时，自动销毁最旧的页节点以先进先出（先进先出）的顺序。-完全保留页面的NavPathInfo，支持页面重建。  
- value &lt;=0不限制页面堆栈大小（默认值）。  
- value &gt;0将堆栈大小限制为指定值。  
取值范围为全体整数。

**类型：** number

**默认值：** 0 (nolimit)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-NavigationConfiguration-stackSizeLimit?: number--><!--Device-NavigationConfiguration-stackSizeLimit?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
