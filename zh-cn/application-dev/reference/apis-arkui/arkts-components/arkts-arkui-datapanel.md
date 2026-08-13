# DataPanel

数据面板组件，用于将多个数据占比情况使用占比图进行展示，支持环形和线性两种展示类型，可自定义颜色、阴影、底板等视觉效果，适用于存储容量、任务进度、资源占比等数据可视化场景，帮助用户直观了解数据分布情况。 > **说明：** > > - 该组件从API版本26.0.0开始支持WithTheme。

## 子组件 无

## DataPanel

```TypeScript
DataPanel(options: DataPanelOptions)
```

创建数据面板组件。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-DataPanelInterface-(options: DataPanelOptions): DataPanelAttribute--><!--Device-DataPanelInterface-(options: DataPanelOptions): DataPanelAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [DataPanelOptions](arkts-arkui-datapaneloptions-i.md) | 是 | 数据面板配置选项，用于设置数据面板的数据值列表、最大值和数据面板类型。 |

## 汇总

- [ColorStop](arkts-arkui-colorstop-i.md)
- [DataPanelConfiguration](arkts-arkui-datapanelconfiguration-i.md)
- [DataPanelOptions](arkts-arkui-datapaneloptions-i.md)
- [DataPanelShadowOptions](arkts-arkui-datapanelshadowoptions-i.md)
- [DataPanelType](arkts-arkui-datapaneltype-e.md)
