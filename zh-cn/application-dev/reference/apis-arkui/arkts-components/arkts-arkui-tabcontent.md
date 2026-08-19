# TabContent

仅在[Tabs](../../apis-avsession-kit/arkts-apis/arkts-avsession-avmusictemplate-customelement-i.md#tabs)中使用，对应一个切换页签的内容视图。 > **说明：** > - 该组件默认设置了clip属性的值为true，若需要扩展内容区到组件外显示，需先关闭clip属性。

## 子组件 支持单个子组件。 > **说明：** > > 可内置系统组件和自定义组件，支持渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和 > [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)）。

## TabContent

```TypeScript
TabContent()
```

创建TabContent页签和内容。 > **说明：** > > TabContent组件仅能作为Tabs组件的子组件使用，否则会导致组件无法正常显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabContentInterface-(): TabContentAttribute--><!--Device-TabContentInterface-(): TabContentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [BoardStyle](arkts-arkui-boardstyle-i.md) | 背板风格对象。 |
| [DrawableTabBarIndicator](arkts-arkui-drawabletabbarindicator-i.md) | 使用图片资源作为下划线的对象。 |
| [IndicatorStyle](arkts-arkui-indicatorstyle-i.md) | 下划线风格对象。 |
| [LabelStyle](arkts-arkui-labelstyle-i.md) | label文本和字体的样式对象。 |
| [TabBarIconStyle](arkts-arkui-tabbariconstyle-i.md) | Label图标样式对象。 |
| [TabBarOptions](arkts-arkui-tabbaroptions-i.md) | 设置页签内的图片和文字内容。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | 作为DrawableTabBarIndicator对象中drawable属性的入参对象。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LayoutMode](arkts-arkui-layoutmode-e.md) | 页签内容排布方式枚举。 |
| [SelectedMode](arkts-arkui-selectedmode-e.md) | 选中子页签的显示模式枚举。 |

