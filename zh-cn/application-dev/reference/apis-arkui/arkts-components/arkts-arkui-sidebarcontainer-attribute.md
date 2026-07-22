# SideBarContainer属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** SideBarContainerAttribute extends [CommonMethod<SideBarContainerAttribute>](CommonMethod<SideBarContainerAttribute>)

**起始版本：** 8

<!--Device-unnamed-declare class SideBarContainerAttribute extends CommonMethod<SideBarContainerAttribute>--><!--Device-unnamed-declare class SideBarContainerAttribute extends CommonMethod<SideBarContainerAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoHide

```TypeScript
autoHide(value: boolean)
```

设置当侧边栏拖拽到小于最小宽度后，是否自动隐藏。受minSideBarWidth属性方法影响，minSideBarWidth属性方法未设置值使用默认值。

拖拽过程中判断是否要自动隐藏。小于最小宽度时需要阻尼效果触发隐藏（越界一段距离）。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-autoHide(value: boolean): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-autoHide(value: boolean): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 侧边栏拖拽到小于最小宽度后，是否自动隐藏。<br/>true：会自动隐藏<br/>false：不会自动隐藏<br/>默认值：true |

## controlButton

```TypeScript
controlButton(value: ButtonStyle)
```

设置侧边栏控制按钮的属性。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-controlButton(value: ButtonStyle): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-controlButton(value: ButtonStyle): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ButtonStyle](arkts-arkui-buttonstyle-i.md) | 是 | 侧边栏控制按钮的属性。 |

## divider

```TypeScript
divider(value: DividerStyle | null)
```

设置分割线的样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-divider(value: DividerStyle | null): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-divider(value: DividerStyle | null): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DividerStyle](arkts-arkui-dividerstyle-i.md) \| null | 是 | 分割线的样式。<br/>默认为DividerStyle：显示分割线。<br/>- null或undefined：行为不做处理，分割线样式与默认值保持一致。<br/>**说明：** <br/>API version 11及以下版本，null效果为不显示分割线。 |

## maxSideBarWidth

```TypeScript
maxSideBarWidth(value: number)
```

设置侧边栏最大宽度。设置为小于0的值时按默认值显示。值不能超过侧边栏容器本身宽度，超过则使用侧边栏容器本身宽度。

maxSideBarWidth优先于侧边栏子组件maxWidth，maxSideBarWidth未设置时默认值优先级高于侧边栏子组件maxWidth。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-maxSideBarWidth(value: number): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-maxSideBarWidth(value: number): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置侧边栏最大宽度。<br/>默认值：280vp<br/>单位：vp<br/>取值范围：[0, +∞) |

## maxSideBarWidth

```TypeScript
maxSideBarWidth(value: Length)
```

设置侧边栏最大宽度。设置为小于0的值时按默认值显示。值不能超过侧边栏容器本身宽度，超过则使用侧边栏容器本身宽度。与[maxSideBarWidth](SideBarContainerAttribute#maxSideBarWidth(value: number))相比，value参数新增了对百分比字符串和其他[像素单位](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)的支持。

maxSideBarWidth优先于侧边栏子组件maxWidth，maxSideBarWidth未设置时默认值优先级高于侧边栏子组件maxWidth。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-maxSideBarWidth(value: Length): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-maxSideBarWidth(value: Length): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 设置侧边栏最大宽度。<br/>默认值：280vp<br/>单位：vp<br/>取值范围：[0, +∞) |

## minContentWidth

```TypeScript
minContentWidth(value: Dimension)
```

设置SideBarContainer组件内容区可显示的最小宽度。

设置为小于0，内容区显示的最小宽度为360vp，未设置该属性时，组件内容区的可缩小到0。

Embed场景下，增大组件尺寸时仅增大内容区的尺寸。

缩小组件尺寸时，先缩小内容区的尺寸至minContentWidth。继续缩小组件尺寸时，保持内容区宽度minContentWidth不变，优先缩小侧边栏的尺寸。

当缩小侧边栏的尺寸至minSideBarWidth后，继续缩小组件尺寸时，

- 如果[autoHide](SideBarContainerAttribute#autoHide)属性为false，则会保持侧边栏宽度[minSideBarWidth](SideBarContainerAttribute#minSideBarWidth(value: number))和内容区宽度minContentWidth不变，但内容区会被截断显示；  
- 如果autoHide属性为true，则会优先隐藏侧边栏，然后继续缩小至内容区宽度minContentWidth后，内容区宽度保持不变，但内容区会被截断显示。

minContentWidth优先于侧边栏的[maxSideBarWidth](SideBarContainerAttribute#maxSideBarWidth(value: number))与sideBarWidth属性，minContentWidth未设置时默认值优先级低于设置的minSideBarWidth与maxSideBarWidth属性。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-minContentWidth(value: Dimension): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-minContentWidth(value: Dimension): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | 是 | SideBarContainer组件内容区可显示的最小宽度。<br/>默认值：360vp<br/>单位：vp |

## minSideBarWidth

```TypeScript
minSideBarWidth(value: number)
```

设置侧边栏最小宽度。设置为小于0的值时按默认值显示。值不能超过侧边栏容器本身宽度，超过则使用侧边栏容器本身宽度。

minSideBarWidth优先于侧边栏子组件minWidth，minSideBarWidth未设置时默认值优先级高于侧边栏子组件minWidth。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-minSideBarWidth(value: number): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-minSideBarWidth(value: number): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 侧边栏最小宽度。<br/>。<br>单位为：vp。取值范围：[0, +∞)。默认值：API version 9及以下版本默认值为200vp，API version 10的默认值为240vp。 |

## minSideBarWidth

```TypeScript
minSideBarWidth(value: Length)
```

设置侧边栏最小宽度。设置为小于0的值时按默认值显示。值不能超过侧边栏容器本身宽度，超过则使用侧边栏容器本身宽度。与[minSideBarWidth](SideBarContainerAttribute#minSideBarWidth(value: number))相比，value参数新增了对百分比字符串和其他[像素单位](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)的支持。

minSideBarWidth优先于侧边栏子组件minWidth，minSideBarWidth未设置时默认值优先级高于侧边栏子组件minWidth。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-minSideBarWidth(value: Length): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-minSideBarWidth(value: Length): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 侧边栏最小宽度。<br/>默认值：API version 9及以下版本默认值为200vp，API version 10的默认值为240vp。<br/>取值范围：[0, +∞) |

## onChange

```TypeScript
onChange(callback: (value: boolean) => void)
```

当侧边栏的状态在显示和隐藏之间切换时触发回调。

触发该事件的条件：

1. showSideBar属性值变换时。2. showSideBar属性自适应行为变化时。3. 分割线拖拽触发[autoHide](SideBarContainerAttribute#autoHide)时。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-onChange(callback: (value: boolean) => void): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-onChange(callback: (value: boolean) => void): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: boolean) =&gt; void | 是 | true表示显示，false表示隐藏。 |

## showControlButton

```TypeScript
showControlButton(value: boolean)
```

设置是否显示控制按钮。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-showControlButton(value: boolean): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-showControlButton(value: boolean): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否显示控制按钮。<br/>true：显示控制按钮<br/>false：不显示控制按钮<br/>默认值：true |

## showSideBar

```TypeScript
showSideBar(value: boolean)
```

设置是否显示侧边栏。

从API version 10开始，该属性支持[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-showSideBar(value: boolean): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-showSideBar(value: boolean): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否显示侧边栏。<br/>true：显示侧边栏<br/>false：不显示侧边栏<br/>默认值：true |

## showSideBarWithGesture

```TypeScript
showSideBarWithGesture(value: boolean)
```

设置是否支持通过手势滑动来显示或隐藏侧边栏。未通过该接口设置时，不支持通过手势滑动显示或隐藏侧边栏。
> **说明：**
> - 手势滑动生效范围为侧边栏+内容区（不含分割线），滑动距离达到100vp时改变侧边栏显示或隐藏状态，最大可滑动距离等于侧边栏宽度。  
>  
> - 当侧边栏位于容器左侧时：  
> > - 侧边栏隐藏时可向右滑动展开侧边栏。  
> > - 侧边栏显示时可向左滑动关闭侧边栏。  
>  
> - 当侧边栏位于容器右侧时：  
> > - 侧边栏隐藏时可向左滑动展开侧边栏。  
> > - 侧边栏显示时可向右滑动关闭侧边栏。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-showSideBarWithGesture(value: boolean): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-showSideBarWithGesture(value: boolean): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置是否支持通过手势滑动显示或隐藏侧边栏。<br/>true：支持通过手势滑动显示或隐藏侧边栏。<br/>false：不支持通过手势滑动显示或隐藏侧边栏。 |

## sideBarPosition

```TypeScript
sideBarPosition(value: SideBarPosition)
```

设置侧边栏显示位置。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-sideBarPosition(value: SideBarPosition): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-sideBarPosition(value: SideBarPosition): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SideBarPosition](arkts-arkui-sidebarposition-e.md) | 是 | 侧边栏显示位置。<br/>默认值：SideBarPosition.Start |

## sideBarWidth

```TypeScript
sideBarWidth(value: number)
```

设置侧边栏的宽度。设置为小于0的值时按默认值显示。受最小宽度和最大宽度限制，不在限制区域内取最近的点。

从API version 18开始，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md)双向绑定变量。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-sideBarWidth(value: number): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-sideBarWidth(value: number): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 侧边栏的宽度。<br/>默认值：240vp<br/>单位：vp<br/>取值范围：[0, +∞)<br/>**说明：** <br/>API version 10以下版本的默认值为200vp，API version 10及以上版本的默认值为240vp。 |

## sideBarWidth

```TypeScript
sideBarWidth(value: Length)
```

设置侧边栏的宽度。设置为小于0的值时按默认值显示。受最小宽度和最大宽度限制，不在限制区域内取最近的点。与[sideBarWidth](SideBarContainerAttribute#sideBarWidth(value: number))相比，value参数新增了对百分比字符串和其他[像素单位](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)的支持。

从API version 18开始，该参数支持[!!](../../../ui/state-management/arkts-new-binding.md)双向绑定变量。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarContainerAttribute-sideBarWidth(value: Length): SideBarContainerAttribute--><!--Device-SideBarContainerAttribute-sideBarWidth(value: Length): SideBarContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 侧边栏的宽度。<br/>默认值：240vp<br/>单位：vp<br/>取值范围：[0, +∞)<br/>**说明：** <br/>API version 9的默认值为200vp，API version 10及以上版本的默认值为240vp。 |

