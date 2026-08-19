# GridCol

栅格布局系统中的列组件，必须作为栅格容器组件(GridRow)的子组件使用。适用于响应式布局、多设备适配等需要动态调整列宽的场景。支持响应式断点配置、跨列布局、偏移和排序功能。使用GridCol 组件可以快速实现响应式布局，简化多设备适配的开发工作。 > **说明：** > > 该组件从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 子组件 可以包含单个子组件。

## GridCol

```TypeScript
GridCol(option?: GridColOptions)
```

栅格列布局组件。创建成功后，可根据配置的span、offset、order属性进行栅格布局，作为GridRow的子组件参与栅格系统的布局计算。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridColInterface-(option?: GridColOptions): GridColAttribute--><!--Device-GridColInterface-(option?: GridColOptions): GridColAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [GridColOptions](arkts-arkui-gridcoloptions-i.md) | 否 |  |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md) | 用于自定义指定在不同宽度设备类型上，栅格子组件占据的栅格数量单位。 - API version 20之前，仅配置部分断点下GridCol组件所占列数，取已配置的更小断点的列数补全未配置的列数。若未配置更小断点的列数，取默认值1。 <!--code_no_check--> ```ts span: {xs:2, md:4, lg:8} // 等于配置 span: {xs:2, sm:2, md:4, lg:8, xl:8, xxl:8} span: {md:4, lg:8} // 等于配置 span: {xs:1, sm:1, md:4, lg:8, xl:8, xxl:8} ``` - API version 20及以后，仅配置部分断点下GridCol组件所占列数，取已配置的更小断点的列数补全未配置的列数。若未配置更小断点的列数，取已配置的更大断点的列数补全未配置的列数。 <!--code_no_check--> ```ts span: {xs:2, md:4, lg:8} // 等于配置 span: {xs:2, sm:2, md:4, lg:8, xl:8, xxl:8} span: {md:4, lg:8} // 等于配置 span: {xs:4, sm:4, md:4, lg:8, xl:8, xxl:8} ``` - 建议手动配置不同断点下GridCol组件所占列数，避免默认补全列数的布局效果不符合预期。 |
| [GridColOptions](arkts-arkui-gridcoloptions-i.md) | 设置栅格列布局组件布局选项。 `span`、`offset`、`order`属性按照`xs`、`sm`、`md`、`lg`、`xl`、`xxl`的顺序具有“继承性”，未设置值的断点将会从前一个断点取值。 API version 20之后，`span`的继承规则见[GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md)，`offset`和`order`的继承规则保持不变。 |

