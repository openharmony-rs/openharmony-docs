# GridCol

栅格布局系统中的列组件，必须作为栅格容器组件(GridRow)的子组件使用。适用于响应式布局、多设备适配等需要动态调整列宽的场景。支持响应式断点配置、跨列布局、偏移和排序功能。使用GridCol 组件可以快速实现响应式布局，简化多设备适配的开发工作。 > **说明：** > > 该组件从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 子组件 可以包含单个子组件。

## GridCol

```TypeScript
GridCol(option?: GridColOptions)
```

栅格列布局组件。创建成功后，可根据配置的span、offset、order属性进行栅格布局，作为GridRow的子组件参与栅格系统的布局计算。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridColInterface-(option?: GridColOptions): GridColAttribute--><!--Device-GridColInterface-(option?: GridColOptions): GridColAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [GridColOptions](arkts-arkui-gridcoloptions-i.md) | 否 |  |

## 汇总

- [GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md)
- [GridColOptions](arkts-arkui-gridcoloptions-i.md)
