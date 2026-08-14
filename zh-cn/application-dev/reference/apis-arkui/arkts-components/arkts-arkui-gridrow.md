# GridRow

栅格布局可以为布局提供规律性的结构，解决多尺寸多设备的动态布局问题，保证不同设备上各个模块的布局一致性。 栅格容器组件，仅可以和栅格子组件(GridCol)在栅格布局场景中使用。 支持根据设备尺寸和断点动态调整列数与间距，实现响应式布局。 > **说明：** > > 该组件从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 子组件 可以包含GridCol子组件。

## GridRow

```TypeScript
GridRow(option?: GridRowOptions)
```

栅格行布局容器。仅可以和栅格子组件在栅格布局场景中使用。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowInterface-(option?: GridRowOptions): GridRowAttribute--><!--Device-GridRowInterface-(option?: GridRowOptions): GridRowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [GridRowOptions](arkts-arkui-gridrowoptions-i.md) | 否 |  |

## 汇总

- [BreakPoints](arkts-arkui-breakpoints-i.md)
- [GridRowColumnOption](arkts-arkui-gridrowcolumnoption-i.md)
- [GridRowOptions](arkts-arkui-gridrowoptions-i.md)
- [GridRowSizeOption](arkts-arkui-gridrowsizeoption-i.md)
- [GutterOption](arkts-arkui-gutteroption-i.md)
- [BreakpointsReference](arkts-arkui-breakpointsreference-e.md)
- [GridRowDirection](arkts-arkui-gridrowdirection-e.md)
