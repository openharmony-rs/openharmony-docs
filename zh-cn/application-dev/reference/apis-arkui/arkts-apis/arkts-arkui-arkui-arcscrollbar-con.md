# 常量

## ArcScrollBar

```TypeScript
export declare const ArcScrollBar: ArcScrollBarInterface
```

弧形滚动条组件ArcScrollBar，适用于圆形屏幕等需要弧形滚动条的场景，用于配合可滚动组件使用，如ArcList、 List、Grid、 Scroll、WaterFlow。

> **说明：**
> 
> - 未设置宽高时，ArcScrollBar采用父组件[LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md)中的maxSize作为尺寸。若父组件存在可滚动组件，如
> ArcList、List、
> Grid、Scroll、
> WaterFlow，建议设置ArcScrollBar宽高，否则尺寸可能为无穷大。
> 
> - 该组件支持在Phone、PC/2in1、Tablet、TV、Wearable设备上使用。API version 22及以前版本，在Phone、PC/2in1、Tablet、TV上使用会编译告警，但可以正常运行。

### 子组件

不包含子组件。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## ArcScrollBarInstance

```TypeScript
export declare const ArcScrollBarInstance: ArcScrollBarAttribute
```

定义ArcScrollBar组件实例。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle
