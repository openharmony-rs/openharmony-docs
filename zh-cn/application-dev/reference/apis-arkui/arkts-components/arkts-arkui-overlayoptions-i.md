# OverlayOptions

浮层的定位。

> **说明：**
> 
> 为规范匿名对象的定义，API 12版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## align

```TypeScript
align?: Alignment
```

设置浮层相对于组件的方位。默认值：TopStart

**类型：** [Alignment](../arkts-apis/arkts-arkui-alignment-e.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: OverlayOffset
```

设置浮层基于自身左上角的偏移量。浮层默认处于组件左上角。

**类型：** [OverlayOffset](arkts-arkui-overlayoffset-i.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
