# TabContent

仅在[Tabs](../../apis-avsession-kit/arkts-apis/arkts-avsession-avmusictemplate-customelement-i.md#tabs)中使用，对应一个切换页签的内容视图。

> **说明：**

> - 该组件默认设置了clip属性的值为true，若需要扩展内容区到组件外显示，需先关闭clip属性。

## 子组件

支持单个子组件。

> **说明：** 
> 
> 可内置系统组件和自定义组件，支持渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、
> [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和
> [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)）。

## TabContent

```TypeScript
TabContent()
```

创建TabContent页签和内容。

> **说明：** 
> 
> TabContent组件仅能作为Tabs组件的子组件使用，否则会导致组件无法正常显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

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
| [TabBarOptions](arkts-arkui-tabbaroptions-i.md) | 设置页签内的图片和文字内容。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | 作为DrawableTabBarIndicator对象中drawable属性的入参对象。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LayoutMode](arkts-arkui-layoutmode-e.md) | 页签内容排布方式枚举。 |
| [SelectedMode](arkts-arkui-selectedmode-e.md) | 选中子页签的显示模式枚举。 |

## 示例

```TypeScript
### 示例1（自定义页签切换联动）

本示例通过[onAnimationStart](ts-container-tabs.md#onanimationstart11)、[onChange](ts-container-tabs.md#onchange)实现切换时自定义tabBar和TabContent的联动。

> 说明
> 
> 此示例的资源不在src > main > resource目录下，从DevEco Studio 6.0.0 Beta2开始，新建工程或者模块时，默认创建的模块不会对非resources目录下的资源进行打包，需使能相关开关：模块的build-profile.json5中buildOptions > resOptions > copyCodeResource > enable设置为true，详见[resOptions](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348)中相关介绍。


```

```TypeScript
### 示例2（自定义侧边页签）

本示例通过[vertical](./ts-container-tabs.md#vertical)、[barPosition](./ts-container-tabs.md#barposition9)实现侧边页签。

> 说明
> 
> 此示例的资源不在src > main > resource目录下，从DevEco Studio 6.0.0 Beta2开始，新建工程或者模块时，默认创建的模块不会对非resources目录下的资源进行打包，需使能相关开关：模块的build-profile.json5中buildOptions > resOptions > copyCodeResource > enable设置为true，详见[resOptions](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348)中相关介绍。


```

```TypeScript
### 示例3（子页签/底部页签/侧边页签样式对比）

本示例使用了[SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md)、[BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md)实现了子页签、底部页签和侧边页签。


```

```TypeScript
### 示例4（设置子页签下划线基本属性）

本示例通过SubTabBarStyle中的[indicator](#indicator10)属性，实现了子页签下划线基本属性的展示。


```

```TypeScript
### 示例5（设置子页签文本自适应高度属性）

本示例通过[heightAdaptivePolicy](#labelstyle10对象说明)实现了子页签文本高度自适应。


```

```TypeScript
### 示例6（设置底部页签基本属性）

本示例通过[padding](#padding10)、[verticalAlign](#verticalalign10)、[layoutMode](#layoutmode10)、[symmetricExtensible](arkts-arkui-bottomtabbarstyle-c.md#symmetricextensible)实现了底部页签基本属性的展示。


```

```TypeScript
### 示例7（设置子页签/底部页签文本颜色）

本示例通过[LabelStyle](#labelstyle10对象说明)中的unselectedColor和selectedColor改变底部页签以及子页签的文本颜色。

通过[iconStyle](#iconstyle12)中的unselectedColor和selectedColor改变底部页签的图标颜色。

> 说明
> 
> 此示例的资源不在src > main > resource目录下，从DevEco Studio 6.0.0 Beta2开始，新建工程或者模块时，默认创建的模块不会对非resources目录下的资源进行打包，需使能相关开关：模块的build-profile.json5中buildOptions > resOptions > copyCodeResource > enable设置为true，详见[resOptions](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348)中相关介绍。


```

```TypeScript
### 示例8（设置底部页签使用symbol图标）

该示例实现了[BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md)图片传入Symbol。


```

```TypeScript
### 示例9（通过ComponentContent设置TabBar）

该示例实现了通过ComponentContent封装组件内容，设置[TabBar](arkts-arkui-tabcontent-comp-attribute.md#tabbar)。通过ComponentContent的update函数更新TabBar。


```

```TypeScript
### 示例10（通过ComponentContent预加载子节点）

该示例实现了通过ComponentContent设置TabBar，使用TabsController的[preloadItems](ts-container-tabs.md#preloaditems12)预加载子节点。


```

```TypeScript
### 示例11（设置子页签indicator为图片）

该示例通过SubTabBarStyle中的[indicator](#indicator22)属性，实现了图片格式的子页签下划线风格。

从API version 22开始，新增了入参类型包含图片的indicator属性。
```
