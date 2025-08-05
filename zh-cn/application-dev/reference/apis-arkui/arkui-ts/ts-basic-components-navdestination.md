# NavDestination
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--SE: @jiangdayuan-->
<!--TSE: @lxl007-->

作为子页面的根容器，用于显示[Navigation](ts-basic-components-navigation.md)的内容区。

> **说明：**
>
> - 该组件从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 该组件从API version 11开始默认支持安全区避让特性(默认值为：expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.TOP, SafeAreaEdge.BOTTOM]))，开发者可以重写该属性覆盖默认行为，API version 11之前的版本需配合[expandSafeArea](ts-universal-attributes-expand-safe-area.md)属性实现安全区避让。
>
> - NavDestination组件必须配合Navigation使用，作为Navigation目的页面的根节点，单独使用只能作为普通容器组件，不具备路由相关属性能力。
>
> - 如果路由栈中间页面的生命周期发生变化，跳转之前的栈顶Destination的生命周期(onWillShow, onShown, onHidden, onWillDisappear)与跳转之后的栈顶Destination的生命周期(onWillShow, onShown, onHidden, onWillDisappear)均在最后触发。
>
> - NavDestination未设置主副标题并且没有返回键时，不显示标题栏。
>
> - 不要在NavDestination上添加[zIndex](ts-universal-attributes-z-order.md#zindex)属性，会覆盖掉系统设置的层级，可能导致出现显示异常。

## 子组件

> **说明：**
>
> - 子组件类型：系统组件和自定义组件，支持渲染控制类型（[if/else](../../../ui/state-management/arkts-rendering-control-ifelse.md)、[ForEach](../../../ui/state-management/arkts-rendering-control-foreach.md)和[LazyForEach](../../../ui/state-management/arkts-rendering-control-lazyforeach.md)）。
> - 子组件个数：多个。


## 接口

NavDestination()

创建[Navigation](ts-basic-components-navigation.md)子页面的根容器。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 属性

支持[通用属性](ts-component-general-attributes.md)。

不推荐设置位置、大小等布局相关属性，可能会造成页面显示异常。

### title

title(value: string | CustomBuilder | NavDestinationCommonTitle | NavDestinationCustomTitle | Resource, options?: NavigationTitleOptions)

设置页面标题。使用NavigationCustomTitle类型设置height高度时，[titleMode](ts-basic-components-navigation.md#titlemode)属性不会生效。字符串超长时，如果不设置副标题，先缩小再换行2行后以...截断。如果设置副标题，先缩小后以...截断。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明       |
| ------ | ------------------------------------------------------------ | ---- | ---------- |
| value  | string&nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8)&nbsp;\|&nbsp;[NavDestinationCommonTitle](#navdestinationcommontitle)&nbsp;\|&nbsp;[NavDestinationCustomTitle](#navdestinationcustomtitle)&nbsp;\|&nbsp;[Resource<sup>14+</sup>](ts-types.md#resource)  | 是   | 页面标题。 |
| options<sup>12+</sup> | [NavigationTitleOptions](ts-basic-components-navigation.md#navigationtitleoptions11) | 否   | 标题栏选项。 |

### hideTitleBar

hideTitleBar(value: boolean)

设置是否隐藏标题栏。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型    | 必填 | 说明                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| value  | boolean | 是   | 是否隐藏标题栏。<br/>默认值：false<br/>true：&nbsp;隐藏标题栏。<br/>false：&nbsp;显示标题栏。 |

### hideTitleBar<sup>13+</sup>

hideTitleBar(hide: boolean, animated: boolean)

设置是否隐藏标题栏。与[hideTitleBar](#hidetitlebar)相比，新增标题栏显隐时是否使用动画。

**原子化服务API：** 从API version 13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型    | 必填 | 说明                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| hide  | boolean | 是   | 是否隐藏标题栏。<br/>默认值：false<br/>true：隐藏标题栏。<br/>false：显示标题栏。 |
| animated  | boolean | 是   | 设置是否使用动画显隐标题栏。<br/>默认值：false<br/>true：使用动画显示隐藏标题栏。<br/>false：不使用动画显示隐藏标题栏。 |

### toolbarConfiguration<sup>13+</sup>

toolbarConfiguration(toolbarParam: Array&lt;ToolbarItem&gt; | CustomBuilder, options?: NavigationToolbarOptions)

设置工具栏内容。未调用本接口时不显示工具栏。

**原子化服务API：** 从API version 13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名       | 类型                                                         | 必填 | 说明                                                         |
| ------------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| toolbarParam | &nbsp;Array&lt;[ToolbarItem](ts-basic-components-navigation.md#toolbaritem10)&gt; &nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8) | 是   | 工具栏内容。<br/>使用Array&lt;[ToolbarItem](ts-basic-components-navigation.md#toolbaritem10)&gt;写法设置的工具栏有如下特性：<br/>-工具栏所有选项均分底部工具栏，在每个均分内容区布局文本和图标。<br/>-文本超长时，若工具栏选项个数小于5个，优先拓展选项的宽度，工具栏最大宽度与屏幕等宽，其次逐级缩小，缩小之后换行，最后截断。<br/>-竖屏最多支持显示5个图标，多余的图标会被放入自动生成的更多图标中，点击更多图标，可以展示剩余内容。横屏时，如果为[Split](ts-basic-components-navigation.md#navigationmode9枚举说明)模式，仍按照竖屏规则显示，如果为[Stack](ts-basic-components-navigation.md#navigationmode9枚举说明)模式需配合menus属性的Array&lt;[NavigationMenuItem](ts-basic-components-navigation.md#navigationmenuitem)&gt;使用，底部工具栏会自动隐藏，同时底部工具栏所有选项移动至页面右上角菜单。<br/>使用[CustomBuilder](ts-types.md#custombuilder8)写法为用户自定义工具栏选项，除均分底部工具栏外不具备以上功能。 |
| options      | [NavigationToolbarOptions](ts-basic-components-navigation.md#navigationtoolbaroptions11) | 否   | 工具栏选项。包含工具栏背景颜色、工具栏背景模糊样式及模糊选项、工具栏背景属性、工具栏布局方式、是否隐藏工具栏的文本、工具栏更多图标的菜单选项。                                                 |

> **说明：**
>
> 不支持通过SymbolGlyphModifier对象的fontSize属性修改图标大小、effectStrategy属性修改动效、symbolEffect属性修改动效类型。

### hideToolBar<sup>13+</sup>

hideToolBar(hide: boolean, animated?: boolean)

设置是否隐藏工具栏。

**原子化服务API：** 从API version 13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型    | 必填 | 说明                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| hide  | boolean | 是   | 是否隐藏工具栏。<br/>默认值：false<br/>true：隐藏工具栏。<br/>false：显示工具栏。 |
| animated  | boolean | 否   | 设置是否使用动画显隐工具栏。<br/>默认值：false<br/>true：使用动画显示隐藏工具栏。<br/>false：不使用动画显示隐藏工具栏。 |

### mode <sup>11+</sup>

mode(value: NavDestinationMode)

设置NavDestination类型，不支持动态修改。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                 | 必填 | 说明                                                         |
| ------ | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [NavDestinationMode](#navdestinationmode枚举说明11) | 是   | NavDestination类型。<br/>默认值：NavDestinationMode.STANDARD |

### backButtonIcon<sup>11+</sup>

backButtonIcon(value: ResourceStr | PixelMap | SymbolGlyphModifier)

> **说明：**
>
> 不支持通过SymbolGlyphModifier对象的fontSize属性修改图标大小、effectStrategy属性修改动效、symbolEffect属性修改动效类型。


设置标题栏返回键图标。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明               |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| value  | [ResourceStr](ts-types.md#resourcestr)&nbsp;\|&nbsp;[PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md)&nbsp;\|&nbsp;[SymbolGlyphModifier<sup>12+</sup>](ts-universal-attributes-attribute-modifier.md)  | 是   | 标题栏返回键图标。 |

### backButtonIcon<sup>19+</sup>

backButtonIcon(icon: ResourceStr | PixelMap | SymbolGlyphModifier, accessibilityText?: ResourceStr)

> **说明：**
>
> 不支持通过SymbolGlyphModifier对象的fontSize属性修改图标大小、effectStrategy属性修改动效、symbolEffect属性修改动效类型。


设置标题栏返回键图标和无障碍播报内容。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明               |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| icon  | [ResourceStr](ts-types.md#resourcestr)&nbsp;\|&nbsp;[PixelMap](../../apis-image-kit/arkts-apis-image-PixelMap.md)&nbsp;\|&nbsp;[SymbolGlyphModifier](ts-universal-attributes-attribute-modifier.md)  | 是   | 标题栏返回键图标。 |
| accessibilityText | [ResourceStr](ts-types.md#resourcestr) | 否 | 返回键无障碍播报内容。</br>默认值：系统语言是中文时为“返回”，系统语言是英文时为“back”。 |

### menus<sup>12+</sup>

menus(value: Array&lt;NavigationMenuItem&gt; | CustomBuilder)

> **说明：**
>
> 不支持通过SymbolGlyphModifier对象的fontSize属性修改图标大小、effectStrategy属性修改动效、symbolEffect属性修改动效类型。


设置页面右上角菜单。不设置时不显示菜单项。使用Array<[NavigationMenuItem](ts-basic-components-navigation.md#navigationmenuitem)&gt; 写法时，竖屏最多支持显示3个图标，横屏最多支持显示5个图标，多余的图标会被放入自动生成的更多图标。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明               |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| value  | Array<[NavigationMenuItem](ts-basic-components-navigation.md#navigationmenuitem)&gt;&nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8) | 是   | 页面右上角菜单。 |

### menus<sup>19+</sup>

menus(items: Array&lt;NavigationMenuItem&gt; | CustomBuilder, options?: NavigationMenuOptions)

> **说明：**
>
> 不支持通过SymbolGlyphModifier对象的fontSize属性修改图标大小、effectStrategy属性修改动效、symbolEffect属性修改动效类型。


设置页面右上角菜单。不设置时不显示菜单项。与[menus](#menus12)相比，新增菜单选项。使用Array<[NavigationMenuItem](ts-basic-components-navigation.md#navigationmenuitem)&gt; 写法时，竖屏最多支持显示3个图标，横屏最多支持显示5个图标，多余的图标会被放入自动生成的更多图标。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明               |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| items  | Array<[NavigationMenuItem](ts-basic-components-navigation.md#navigationmenuitem)&gt;&nbsp;\|&nbsp;[CustomBuilder](ts-types.md#custombuilder8) | 是   | 页面右上角菜单。 |
| options | [NavigationMenuOptions](ts-basic-components-navigation.md#navigationmenuoptions19) | 否   | 页面右上角菜单选项。 |

### ignoreLayoutSafeArea<sup>12+</sup>

ignoreLayoutSafeArea(types?: Array&lt;LayoutSafeAreaType&gt;, edges?: Array&lt;LayoutSafeAreaEdge&gt;)

控制组件的布局，使其扩展到非安全区域

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                               | 必填 | 说明                                                         |
| ------ | -------------------------------------------------- | ---- | ------------------------------------------------------------ |
| types  | Array <[LayoutSafeAreaType](ts-types.md#layoutsafeareatype12)> | 否   | 配置扩展安全区域的类型。<br />默认值：<br />[LayoutSafeAreaType.SYSTEM] |
| edges  | Array <[LayoutSafeAreaEdge](ts-types.md#layoutsafeareaedge12)> | 否   | 配置扩展安全区域的方向。<br /> 默认值：<br />[LayoutSafeAreaEdge.TOP, LayoutSafeAreaEdge.BOTTOM]。|

>  **说明：**
>   
>  组件设置ignoreLayoutSafeArea之后生效的条件为：   
>  设置LayoutSafeAreaType.SYSTEM时，组件的边界与非安全区域重合时组件能够延伸到非安全区域下。例如：设备顶部状态栏高度100，组件在屏幕中纵向方位的绝对偏移需要在0到100之间。  
>   
>  若组件延伸到非安全区域内，此时在非安全区域里触发的事件（例如：点击事件）等可能会被系统拦截，优先响应状态栏等系统组件。

### systemBarStyle<sup>12+</sup>

systemBarStyle(style: Optional&lt;SystemBarStyle&gt;)

当Navigation中显示当前NavDestination时，设置对应系统状态栏的样式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型         | 必填 | 说明               |
| ------ | -------------- | ---- | ------------------ |
| style  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)&lt;[SystemBarStyle](../arkts-apis-window-i.md#systembarstyle12)&gt; | 是   | 系统状态栏样式。 |

> **说明：**
>
> 1. 必须配合Navigation使用，作为其Navigation目的页面的根节点时才能生效。
> 2. 其他使用限制请参考Navigation对应的[systemBarStyle](ts-basic-components-navigation.md#systembarstyle12)属性说明。

### systemTransition<sup>14+</sup>
systemTransition(type: NavigationSystemTransitionType)

设置NavDestination系统转场动画，支持分别设置系统标题栏动画和内容动画。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                 | 必填 | 说明                                                         |
| ------ | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type  | [NavigationSystemTransitionType](#navigationsystemtransitiontype14枚举说明) | 是   | 系统转场动画类型。<br/>默认值：NavigationSystemTransitionType.DEFAULT |

### recoverable<sup>14+</sup>

recoverable(recoverable: Optional&lt;boolean&gt;)

配置NavDestination是否可恢复。如配置为可恢复，当应用进程异常退出并重新冷启动时，可自动创建该NavDestination。该功能需NavDestination对应的Navigation也配置了[可恢复属性](ts-basic-components-navigation.md#recoverable14)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型         | 必填 | 说明               |
| ------ | -------------- | ---- | ------------------ |
| recoverable  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)&lt;boolean&gt; | 是   | NavDestination是否可恢复，默认为不可恢复。<br/>默认值：false<br/>true：路由栈可恢复。<br/>false：路由栈不可恢复。 |

>  **使用说明：**
>
> 该接口需要配合Navigation的[recoverable](./ts-basic-components-navigation.md#recoverable14)接口使用。

### bindToScrollable<sup>14+</sup>
bindToScrollable(scrollers: Array&lt;Scroller&gt;)

绑定NavDestination组件和可滚动容器组件（支持[List](./ts-container-list.md)、[Scroll](./ts-container-scroll.md)、[Grid](./ts-container-grid.md)、[WaterFlow](./ts-container-waterflow.md)），当滑动可滚动容器组件时，会触发所有与其绑定的NavDestination组件的标题栏和工具栏的显示和隐藏动效，上滑隐藏，下滑显示。一个NavDestination可与多个可滚动容器组件绑定，一个可滚动容器组件也可与多个NavDestination绑定。使用示例参见[示例1](#示例1标题栏工具栏与可滚动类组件联动)。

> **说明：**
>
> - 只有NavDestination的标题栏或工具栏设置为可见时，联动效果才会生效。
> - 当多个可滚动容器组件绑定了同一个NavDestination组件时，滚动任何一个容器都会触发标题栏和工具栏的显示或隐藏效果。且当任何一个可滚动容器组件滑动到底部或顶部位置时，会立即触发标题栏和工具栏的显示动效。因此，为了获得最佳用户体验，不建议同时触发多个可滚动容器组件的滚动事件。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                 | 必填 | 说明                                                         |
| ------ | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| scrollers | Array<[Scroller](./ts-container-scroll.md#scroller)> | 是   | 可滚动容器组件的控制器。 |

### bindToNestedScrollable<sup>14+</sup>
bindToNestedScrollable(scrollInfos: Array&lt;NestedScrollInfo&gt;)

绑定NavDestination组件和嵌套的可滚动容器组件（支持[List](./ts-container-list.md)、[Scroll](./ts-container-scroll.md)、[Grid](./ts-container-grid.md)、[WaterFlow](./ts-container-waterflow.md)），当滑动父组件或子组件时，会触发所有与其绑定的NavDestination组件的标题栏和工具栏的显示和隐藏动效，上滑隐藏，下滑显示。一个NavDestination可与多个嵌套的可滚动容器组件绑定，嵌套的可滚动容器组件也可与多个NavDestination绑定。使用示例参见[示例1](#示例1标题栏工具栏与可滚动类组件联动)。

> **说明：**
>
> - 只有NavDestination的标题栏或工具栏设置为可见时，联动效果才会生效。
> - 当多个可滚动容器组件绑定了同一个NavDestination组件时，滚动任何一个容器都会触发标题栏和工具栏的显示或隐藏效果。且当任何一个可滚动容器组件滑动到底部或顶部位置时，会立即触发标题栏和工具栏的显示动效。因此，为了获得最佳用户体验，不建议同时触发多个可滚动容器组件的滚动事件。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                 | 必填 | 说明                                                         |
| ------ | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| scrollInfos | Array<[NestedScrollInfo](#nestedscrollinfo14)> | 是   | 嵌套的可滚动容器组件的控制器。 |

### hideBackButton<sup>15+</sup>

hideBackButton(hide: Optional&lt;boolean&gt;)

设置是否隐藏标题栏中的返回键。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型    | 必填 | 说明                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| hide  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)&lt;boolean&gt; | 是   | 是否隐藏标题栏中的返回键。 <br/>默认值：false<br/>true：隐藏返回键。<br/>false：显示返回键。 |

### customTransition<sup>15+</sup>

customTransition(delegate: NavDestinationTransitionDelegate)

设置NavDestination自定义转场动画。

> **说明：**
>
> 该属性与[systemTransition](#systemtransition14)同时设置时，后设置的属性生效。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型    | 必填 | 说明                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| delegate  | [NavDestinationTransitionDelegate](#navdestinationtransitiondelegate15) | 是   | NavDestination自定义动画的代理函数。 |

### preferredOrientation<sup>19+</sup>

preferredOrientation(orientation: Optional&lt;Orientation&gt;)

设置NavDestination对应的显示方向。转场到该NavDestination后，系统也会将应用主窗口切到该显示方向。

> **说明：**
>
> 该属性满足如下全部条件时才有效：
> 1. NavDestination属于应用主窗口页面，并且主窗口为全屏窗口；
> 2. NavDestination所属的Navigation的大小占满整个应用页面；
> 3. NavDestination类型为[STANDARD](#navdestinationmode枚举说明11)。
>
> 设置显示方向的实际效果依赖于具体的设备支持情况，具体参考窗口的[setPreferredOrientation](../arkts-apis-window-Window.md#setpreferredorientation9-1)接口。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型    | 必填 | 说明                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| orientation  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)&lt;[Orientation](#orientation19)&gt; | 是   | NavDestination页面对应的Orientation。 |

## Orientation<sup>19+</sup>

type Orientation = Orientation

Orientation实例对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

| 类型     | 说明       |
| ------ | ---------- |
| [Orientation](../arkts-apis-window-e.md#orientation9) | 返回Orientation实例对象。 |

### enableStatusBar<sup>19+</sup>

enableStatusBar(enabled: Optional&lt;boolean&gt;, animated?: boolean)

设置进入该NavDestination后，显示或者隐藏系统的状态栏。

> **说明：**
>
> 该属性满足如下全部条件时才生效：
> 1. NavDestination属于应用主窗口页面，并且主窗口为全屏窗口；
> 2. NavDestination所属的Navigation的大小占满整个页面；
> 3. NavDestination的大小占满整个Navigation组件；
> 4. NavDestination类型为[STANDARD](#navdestinationmode枚举说明11)。
>
> 设置系统状态栏的实际效果依赖于具体的设备支持情况，具体参考窗口的[setSpecificSystemBarEnabled](../arkts-apis-window-Window.md#setspecificsystembarenabled11)接口。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型    | 必填 | 说明                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| enabled  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)&lt;boolean&gt; | 是   | 进入该NavDestination后，系统状态栏的显示/隐藏状态。<br/>true：&nbsp;显示状态栏。<br/>false：&nbsp;隐藏状态栏。 |
| animated  | boolean | 否   | 是否使用动画的方式显示/隐藏系统状态栏，默认值为：false。<br/>true：使用动画的方式显示/隐藏系统状态栏。<br/>false：不使用动画的方式显示/隐藏系统状态栏。 |

### enableNavigationIndicator<sup>19+</sup>

enableNavigationIndicator(enabled: Optional&lt;boolean&gt;)

设置进入该NavDestination后，显示或者隐藏系统的导航条。

> **说明：**
>
> 该属性满足如下全部条件时才生效：
> 1. NavDestination属于应用主窗口页面，并且主窗口为全屏窗口；
> 2. NavDestination所属的Navigation的大小占满整个页面；
> 3. NavDestination的大小占满整个Navigation组件；
> 4. NavDestination类型为[STANDARD](#navdestinationmode枚举说明11)。
>
> 设置系统导航条的实际效果依赖于具体的设备支持情况，具体参考窗口的[setSpecificSystemBarEnabled](../arkts-apis-window-Window.md#setspecificsystembarenabled11)接口。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型    | 必填 | 说明                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| enabled  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)&lt;boolean&gt; | 是   | 进入该NavDestination后，系统导航条的显示/隐藏状态。 <br/>true：&nbsp;显示导航条。<br/>false：&nbsp;隐藏导航条。 |

## NavDestinationMode枚举说明<sup>11+</sup>

NavDestination类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 值 | 说明                                     |
| ---- | --- | ---------------------------------------- |
| STANDARD | 0 | 标准模式的NavDestination。                       |
| DIALOG | 1 | 默认透明，进出路由栈不影响下层NavDestination的生命周期。<br />API version 13之前，默认无系统转场动画。从API version 13开始，支持系统转场动画。  |

## NavigationSystemTransitionType<sup>14+</sup>枚举说明

系统转场动画类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 值   | 说明 |
| ----  | ---   | ----- |
| DEFAULT | 0 | 默认系统转场动画。<br/>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。|
| NONE| 1 | 无系统转场动画。<br/>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。|
| TITLE | 2 | 标题栏系统转场动画。<br/>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。|
| CONTENT | 3 | 内容区系统转场动画。<br/>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。|
| FADE<sup>15+</sup> | 4 | 渐变类型的系统转场动画。<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。 |
| EXPLODE<sup>15+</sup> | 5 | 中心缩放类型的系统转场动画。<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。 |
| SLIDE_RIGHT<sup>15+</sup> | 6 | 右侧平移类型的系统转场动画。<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。 |
| SLIDE_BOTTOM<sup>15+</sup> | 7 | 底部平移类型的系统转场动画。<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。 |

**说明：**
>
> 设置系统转场动画，支持分别设置系统标题栏动画和内容动画。
> 
> 系统默认转场动画中只有STANDARD页面的push和pop动画有单独的标题栏动画，存在如下限制：
> 1. 设置NavigationSystemTransitionType为TITLE时，系统转场只有标题栏动画。
> 2. 设置NavigationSystemTransitionType为CONTENT时，系统转场只有内容区动画。
>
> 设置NONE或者TITLE时没有系统转场动画，设置CONTENT和DEFAULT时默认系统转场动画。

## 事件

除支持[通用事件](ts-component-general-events.md)外，还支持如下事件：

### onShown<sup>10+</sup>

onShown(callback:&nbsp;()&nbsp;=&gt;&nbsp;void)

当该NavDestination页面显示时触发此回调。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### onHidden<sup>10+</sup>

onHidden(callback:&nbsp;()&nbsp;=&gt;&nbsp;void)

当该NavDestination页面隐藏时触发此回调。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### onWillAppear<sup>12+</sup>

onWillAppear(callback: Callback\<void>)

当该Destination挂载之前触发此回调。在该回调中允许修改路由栈，当前帧生效。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### onWillShow<sup>12+</sup>

onWillShow(callback: Callback\<void>)

当该Destination显示之前触发此回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### onWillHide<sup>12+</sup>

onWillHide(callback: Callback\<void>)

当该Destination隐藏之前触发此回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### onWillDisappear<sup>12+</sup>

onWillDisappear(callback: Callback\<void>)

当该Destination卸载之前触发的生命周期(有转场动画时，在转场动画开始之前触发)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### onBackPressed<sup>10+</sup>

onBackPressed(callback:&nbsp;()&nbsp;=&gt;&nbsp;boolean)

当与Navigation绑定的导航控制器中存在内容时，此回调生效。当点击返回键时，触发该回调。

返回值为true时，表示重写返回键逻辑，返回值为false时，表示回退到上一个页面。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### onReady<sup>11+</sup>

onReady(callback:&nbsp;[Callback](../../apis-basic-services-kit/js-apis-base.md#callback)<[NavDestinationContext](#navdestinationcontext11)>)

当NavDestination即将构建子组件之前会触发此回调。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### onResult<sup>15+</sup>

onResult(callback:&nbsp;Optional\<Callback\<ESObject\>\>)

NavDestination返回时触发该回调。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ---------------- |
|callback | [Optional](./ts-universal-attributes-custom-property.md)\<[Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<ESObject\>\>| 是 | 页面返回回调，入参为[pop](ts-basic-components-navigation.md#pop11)、[popToName](ts-basic-components-navigation.md#poptoname11)、[popToIndex](ts-basic-components-navigation.md#poptoindex11)接口传入的result参数。如果不传该参数，入参为undefined。|

### onActive<sup>17+</sup>

onActive(callback:&nbsp;Optional\<Callback\<NavDestinationActiveReason\>\>)

NavDestination处于激活态（处于栈顶可操作，且上层无特殊组件遮挡）时，触发该回调。

**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ---------------- |
|callback | [Optional](./ts-universal-attributes-custom-property.md#optionalt12)\<[Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[NavDestinationActiveReason](#navdestinationactivereason17)\>\>| 是 | NavDestination由非激活态变为激活态的原因。|

### onInactive<sup>17+</sup>

onInactive(callback: &nbsp;Optional\<Callback\<NavDestinationActiveReason\>\>)

NavDestination处于非激活态（处于非栈顶不可操作，或处于栈顶时上层有特殊组件遮挡）时，触发该回调。

**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ---------------- |
|callback | [Optional](./ts-universal-attributes-custom-property.md#optionalt12)\<[Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[NavDestinationActiveReason](#navdestinationactivereason17)\>\>| 是 | NavDestination由激活态变为非激活态的原因。|

### onNewParam<sup>19+</sup>

onNewParam(callback: &nbsp;Optional\<Callback\<ESObject\>\>)

当之前存在于栈中的NavDestination页面通过[launchMode.MOVE_TO_TOP_SINGLETON](./ts-basic-components-navigation.md#launchmode12枚举说明)或[launchMode.POP_TO_SINGLETON](./ts-basic-components-navigation.md#launchmode12枚举说明)移动到栈顶时，触发该回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ---- | ---------------- |
|callback | [Optional](./ts-universal-attributes-custom-property.md#optionalt12)\<[Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<ESObject\>\>| 是 | onNewParam触发时的回调函数，入参为路由跳转时传递到目标页面的数据。|

> **说明：**
>
> [replacePath](./ts-basic-components-navigation.md#replacepath11)、[replaceDestination](./ts-basic-components-navigation.md#replacedestination18)不会触发该回调。

## NavDestinationCommonTitle

NavDestination通用标题。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型     | 必填   | 说明     |
| ---- | ------ | ---- | ------ |
| main | string \| [Resource<sup>14+<sup>](ts-types.md#resource) | 是    | 设置主标题。 |
| sub  | string \| [Resource<sup>14+<sup>](ts-types.md#resource) | 是    | 设置副标题。 |

## NavDestinationCustomTitle

NavDestination自定义标题。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称      | 类型                                       | 必填   | 说明       |
| ------- | ---------------------------------------- | ---- | -------- |
| builder | [CustomBuilder](ts-types.md#custombuilder8) | 是    | 设置标题栏内容。 |
| height  | [TitleHeight](ts-appendix-enums.md#titleheight9) \| [Length](ts-types.md#length) | 是    | 设置标题栏高度。<br/>取值范围：[0, +∞)。 |

## NavDestinationContext<sup>11+</sup>

NavDestination上下文信息。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型     | 必填   |  说明     |
| ---- | ------ | ----- | ------ |
| pathInfo | [NavPathInfo](ts-basic-components-navigation.md#navpathinfo10) | 是 | 跳转NavDestination时指定的参数。 <br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| pathStack  | [NavPathStack](ts-basic-components-navigation.md#navpathstack10) | 是 | 当前NavDestination所处的导航控制器。 <br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| navDestinationId<sup>12+</sup> | string | 否 | 当前NavDestination的唯一ID，由系统自动生成，和组件通用属性id无关。 <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|

### getConfigInRouteMap<sup>12+</sup>

getConfigInRouteMap(): RouteMapConfig |undefined

获取当前NavDestination的路由配置信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值**

| 类型 | 说明 |
| --- | --- |
| [RouteMapConfig](#routemapconfig12) | 当前页面路由配置信息。 |
| undefined | 当该页面不是通过路由表配置时返回undefined。 |

## RouteMapConfig<sup>12+</sup>

路由配置信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型   |必填 | 说明 |
| ----  | ---   | ---- |----- |
| name  | string | 是 | 页面名称。|
| pageSourceFile| string | 是 | 页面在当前包中的路径。|
| data | Object | 是 | 页面自定义字段信息。|

## NestedScrollInfo<sup>14+</sup>

嵌套可滚动容器组件信息

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型   |必填 | 说明 |
| ----  | ---   | ---- |----- |
| parent | [Scroller](./ts-container-scroll.md#scroller) | 是 | 可滚动容器组件的控制器。 |
| child | [Scroller](./ts-container-scroll.md#scroller) | 是 | 可滚动容器组件的控制器，child对应的组件需要是parent对应组件的子组件，且组件间存在嵌套滚动关系。|

### NavDestinationActiveReason<sup>17+</sup>

NavDestination激活态或者非激活态变化的原因。

**原子化服务API：** 从API version 17开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 值 | 说明                                     |
| ---- | -- | ---------------------------------------- |
| TRANSITION | 0   | 通过页面跳转的方式使NavDestination激活态发生变化。                       |
| CONTENT_COVER | 1   | 通过全模态的开启和关闭使NavDestination激活态发生变化。  |
| SHEET | 2   | 通过半模态的开启或关闭使NavDestination激活态发生变化。 |
| DIALOG | 3   | 通过自定义Dialog开启或关闭使NavDestination激活态发生变化。 |
| OVERLAY | 4   | 通过OverlayManager开启或者关闭Overlay使NavDestination激活态发生变化。|
| APP_STATE | 5   | 通过前后台切换使NavDestination激活态发生变化。 |

## NavDestinationTransition<sup>15+</sup>

NavDestination自定义动画接口。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型   |必填 | 说明 |
| ----  | ---   | ---- |----- |
| onTransitionEnd | Callback\<void> | 否 | 转场动画结束时的回调函数。 |
| duration | number | 否 | 转场动画的持续时间，默认值为1000（毫秒）。 |
| curve | [Curve](ts-appendix-enums.md#curve) | 否 | 动画的曲线类型，默认值为[Curve.EaseInOut](ts-appendix-enums.md#curve)。 |
| delay | number | 否 | 转场动画的延迟。默认值为0（毫秒）。 |
| event | Callback\<void> | 是 | 指定转场动效的闭包函数，系统会根据闭包中对组件UI状态的修改，生成对应的过渡动画。参见[animateTo](../arkts-apis-uicontext-uicontext.md#animateto)中的event。 |

## NavDestinationTransitionDelegate<sup>15+</sup>

type NavDestinationTransitionDelegate = (operation: NavigationOperation, isEnter: boolean) => Array\<NavDestinationTransition> | undefined

NavDestination自定义转场动画的代理函数。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型     | 必填 | 说明                    |
|------|--------|----|-----------------------|
| operation | [NavigationOperation](ts-basic-components-navigation.md#navigationoperation11枚举说明) | 是  | 当前页面转场的操作类型。 |
| isEnter | boolean | 是  | 当前页面是否为入场页面。<br/>true：&nbsp;当前页面是入场页面。<br/>false：&nbsp;当前页面不是入场页面。 |

**返回值：**

| 类型      | 说明        |
|---------|-----------|
| Array<[NavDestinationTransition](#navdestinationtransition15)> \| undefined | NavDestination页面的自定义动画集合。如果返回undefined则做系统默认动画。 |

## 示例

### 示例1（标题栏工具栏与可滚动类组件联动）

以下示例主要演示NavDestination绑定可滚动容器组件来实现滚动内容时触发标题栏和工具栏显示隐藏的效果。

```ts
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Component
struct MyPageOne {
  private listScroller: Scroller = new Scroller();
  private scrollScroller: Scroller = new Scroller();
  private arr: number[] = [];

  aboutToAppear(): void {
    for (let i = 0; i < 30; i++) {
      this.arr.push(i);
    }
  }

  build() {
    NavDestination() {
      Scroll(this.scrollScroller) {
        Column() {
          List({ space: 0, initialIndex: 0, scroller: this.listScroller }) {
            ForEach(this.arr, (item: number, index: number) => {
              ListItem() {
                Text('' + item)
                  .height(100)
                  .fontSize(16)
                  .textAlign(TextAlign.Center)
                  .width('90%')
                  .margin({ left: '5%' })
                  .borderRadius(10)
                  .backgroundColor(Color.Gray)
              }
            }, (item: string) => item);
          }.width('100%').height('80%').scrollBar(BarState.Off)
          .nestedScroll({ scrollForward: NestedScrollMode.SELF_FIRST, scrollBackward: NestedScrollMode.SELF_FIRST })

          ForEach(this.arr, (item: number, index: number) => {
            ListItem() {
              Text('' + item)
                .height(100)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .width('90%')
                .margin({ top: '5%' })
                .borderRadius(10)
                .backgroundColor(Color.Pink)
            }
          }, (item: string) => item);
        }
      }
      .width('100%')
      .scrollBar(BarState.Off)
      .scrollable(ScrollDirection.Vertical)
      .edgeEffect(EdgeEffect.Spring)
    }
    .title('PageOne', { backgroundColor: Color.Yellow, barStyle: BarStyle.STACK })
    .toolbarConfiguration([
      {
        value: 'item1',
        symbolIcon: new SymbolGlyphModifier($r('sys.symbol.phone_badge_star'))
      }
    ], { backgroundColor: Color.Orange, barStyle: BarStyle.STACK })
    // 绑定有父子关系的可滚动容器组件
    .bindToNestedScrollable([{ parent: this.scrollScroller, child: this.listScroller }])
  }
}

@Component
struct MyPageTwo {
  private listScroller: Scroller = new Scroller();
  private arr: number[] = [];

  aboutToAppear(): void {
    for (let i = 0; i < 30; i++) {
      this.arr.push(i);
    }
  }

  build() {
    NavDestination() {
      List({ scroller: this.listScroller }) {
        ForEach(this.arr, (item: number, index: number) => {
          ListItem() {
            Text('' + item)
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .width('90%')
              .margin({ left: '5%' })
              .borderRadius(10)
              .backgroundColor(Color.Gray)
          }
        }, (item: string) => item);
      }.width('100%')
    }
    .title('PageTwo', { backgroundColor: Color.Yellow, barStyle: BarStyle.STACK })
    .toolbarConfiguration([
      {
        value: 'item1',
        symbolIcon: new SymbolGlyphModifier($r('sys.symbol.phone_badge_star'))
      }
    ], { backgroundColor: Color.Orange, barStyle: BarStyle.STACK })
    // 绑定可滚动容器组件
    .bindToScrollable([this.listScroller])
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  MyPageMap(name: string) {
    if (name === 'myPageOne') {
      MyPageOne();
    } else {
      MyPageTwo();
    }
  }

  build() {
    Navigation(this.stack) {
      Column() {
        Button('push PageOne').onClick(() => {
          this.stack.pushPath({ name: 'myPageOne' });
        })
        Button('push PageTwo').onClick(() => {
          this.stack.pushPath({ name: 'myPageTwo' });
        })
      }.height('40%').justifyContent(FlexAlign.SpaceAround)
    }.width('100%')
    .height('100%')
    .title({ main: 'MainTitle', sub: 'subTitle' })
    .navDestination(this.MyPageMap)
  }
}
```
![navdestination_bind_scrollable](figures/navdestination_bind_scrollable.gif)

### 示例2（设置NavDestination自定义转场）

以下示例主要演示NavDestination设置自定义转场动画属性[customTransition](#customtransition15)的效果。

```ts
@Entry
@Component
struct NavDestinationCustomTransition {
  stack: NavPathStack = new NavPathStack();

  @Builder
  pageMap(name: string) {
    if (name) {
      NavDest();
    }
  }

  aboutToAppear(): void {
    this.stack.pushPath({name: 'dest0'});
  }

  build() {
    Navigation(this.stack) {
      // empty
    }
    .navDestination(this.pageMap)
    .hideNavBar(true)
    .title('Main Page')
    .titleMode(NavigationTitleMode.Mini)
  }
}

declare type voidFunc = () => void;

@Component
struct NavDest {
  @State name: string = 'NA';
  @State destWidth: string = '100%';
  stack: NavPathStack = new NavPathStack();
  @State y: string = '0';

  build() {
    NavDestination() {
      Column() {
        Button('push next page', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.stack.pushPath({ name: this.name == 'PageOne' ? "PageTwo" : "PageOne" });
          })
      }
      .size({ width: '100%', height: '100%' })
    }
    .title(this.name)
    .translate({ y: this.y })
    .onReady((context) => {
      this.name = context.pathInfo.name;
      this.stack = context.pathStack;
    })
    .backgroundColor(this.name == 'PageOne' ? '#F1F3F5' : '#ff11dee5')
    .customTransition(
      (op: NavigationOperation, isEnter: boolean)
        : Array<NavDestinationTransition> | undefined => {
        console.log('[NavDestinationTransition]', 'reached delegate in frontend, op: ' + op + ', isEnter: ' + isEnter);

        let transitionOneEvent: voidFunc = () => { console.log('[NavDestinationTransition]', 'reached transitionOne, empty now!'); }
        let transitionOneFinishEvent: voidFunc = () => { console.log('[NavDestinationTransition]', 'reached transitionOneFinish, empty now!'); }
        let transitionOneDuration: number = 500;
        if (op === NavigationOperation.PUSH) {
          if (isEnter) {
            // ENTER_PUSH
            this.y = '100%';
            transitionOneEvent = () => {
              console.log('[NavDestinationTransition]', 'transitionOne, push & isEnter');
              this.y = '0';
            }
          } else {
            // EXIT_PUSH
            this.y = '0';
            transitionOneEvent = () => {
              console.log('[NavDestinationTransition]', 'transitionOne, push & !isEnter');
              this.y = '0';
            }
            transitionOneDuration = 450;
          }
        } else if (op === NavigationOperation.POP) {
          if (isEnter) {
            // ENTER_POP
            this.y = '0';
            transitionOneEvent = () => {
              console.log('[NavDestinationTransition]', 'transitionOne, pop & isEnter');
              this.y = '0';
            }
          } else {
            // EXIT_POP
            this.y = '0';
            transitionOneEvent = () => {
              console.log('[NavDestinationTransition]', 'transitionOne, pop & !isEnter');
              this.y = '100%';
            }
          }
        } else {
          console.log('[NavDestinationTransition]', '----- NOT-IMPL BRANCH of NAV-DESTINATION CUSTOM TRANSITION -----');
        }

        let transitionOne: NavDestinationTransition = {
          duration: transitionOneDuration,
          delay: 0,
          curve: Curve.Friction,
          event: transitionOneEvent,
          onTransitionEnd: transitionOneFinishEvent
        };

        let transitionTwoEvent: voidFunc = () => { console.log('[NavDestinationTransition]', 'reached transitionTwo, empty now!'); }
        let transitionTwo: NavDestinationTransition = {
          duration: 1000,
          delay: 0,
          curve: Curve.EaseInOut,
          event: transitionTwoEvent,
          onTransitionEnd: () => { console.log('[NavDestinationTransition]', 'reached Two\'s finish'); }
        };

        return [
          transitionOne,
          transitionTwo,
        ];
      })
  }
}
```
![navdestination_custom_transition](figures/navdestination_custom_transition.gif)

### 示例3（设置指定的NavDestination系统转场）

以下示例主要演示NavDestination设置系统转场动画[systemTransition](#systemtransition14)为Fade、Explode、SlideBottom与SlideRight时的转场效果。

```ts
@Entry
@Component
struct NavDestinationSystemTransition {
  @Provide stack: NavPathStack = new NavPathStack()
  @Provide homePageTransitionType: NavigationSystemTransitionType = NavigationSystemTransitionType.DEFAULT;

  @Builder
  pageMap(name: string) {
    if (name === 'Fade') {
      Fade();
    } else if (name === 'Explode') {
      Explode();
    } else if (name === 'SlideRight') {
      SlideRight();
    } else if (name === 'SlideBottom') {
      SlideBottom();
    } else {
      Dest();
    }
  }

  aboutToAppear(): void {
    this.stack.pushPath({name: 'Dest'});
  }

  build() {
    Navigation(this.stack) {
      // empty
    }
    .navDestination(this.pageMap)
    .hideNavBar(true)
  }
}

@Component
struct Dest {
  @Consume stack: NavPathStack;
  @Consume homePageTransitionType: NavigationSystemTransitionType;
  @State name: string = 'NA';

  build() {
    NavDestination() {
      HomeBody();
    }
    .title('Navigation System Animation')
    .onReady((context) => {
      this.name = context.pathInfo.name;
    })
    .systemTransition(this.homePageTransitionType)
  }
}

@Component
struct Fade {
  @Consume stack: NavPathStack;
  @State name: string = 'NA';

  build() {
    NavDestination() {
      DestBody({
        name: this.name
      })
    }
    .title(this.name)
    .onReady((context) => {
      this.name = context.pathInfo.name;
    })
    .systemTransition(NavigationSystemTransitionType.FADE)
  }
}

@Component
struct Explode {
  @Consume stack: NavPathStack;
  @State name: string = 'NA';

  build() {
    NavDestination() {
      DestBody({
        name: this.name
      })
    }
    .title(this.name)
    .onReady((context) => {
      this.name = context.pathInfo.name;
    })
    .systemTransition(NavigationSystemTransitionType.EXPLODE)
  }
}

@Component
struct SlideRight {
  @Consume stack: NavPathStack;
  @State name: string = 'NA';

  build() {
    NavDestination() {
      DestBody({
        name: this.name
      })
    }
    .title(this.name)
    .onReady((context) => {
      this.name = context.pathInfo.name;
    })
    .systemTransition(NavigationSystemTransitionType.SLIDE_RIGHT)
  }
}

@Component
struct SlideBottom {
  @Consume stack: NavPathStack;
  @State name: string = 'NA';

  build() {
    NavDestination() {
      DestBody({
        name: this.name
      })
    }
    .title(this.name)
    .onReady((context) => {
      this.name = context.pathInfo.name;
    })
    .systemTransition(NavigationSystemTransitionType.SLIDE_BOTTOM)
  }
}

@Component
struct DestBody {
  name: string = 'NA';

  columnTextSize: number = 22;
  columnTextFontWeight: FontWeight = FontWeight.Bolder;
  columnWidth: string = '65%';
  columnPadding: number = 22;
  columnMargin: number = 10;
  columnBorderRadius: number = 10;

  build() {
    Column() {
      Column()
        .width('85')
        .height(50)
        .backgroundColor(Color.White)
      Column() {
        Text(this.name)
          .fontSize(this.columnTextSize)
          .fontWeight(this.columnTextFontWeight)
      }
      .width(this.columnWidth)
      .padding(this.columnPadding)
      .margin(this.columnMargin)
      .borderRadius(this.columnBorderRadius)
      .shadow(ShadowStyle.OUTER_DEFAULT_LG)
    }
  }
}

@Component
struct HomeBody {
  @Consume stack: NavPathStack;
  @Consume homePageTransitionType: NavigationSystemTransitionType;

  columnTextSize: number = 22;
  columnTextFontWeight: FontWeight = FontWeight.Bolder;
  columnWidth: string = '85%';
  columnPadding: number = 22;
  columnMargin: number = 10;
  columnBorderRadius: number = 10;
  columnShadow: ShadowStyle = ShadowStyle.OUTER_DEFAULT_MD;

  build() {
    Column() {
      Search({ value: 'Search' })
        .width(this.columnWidth)

      Column() {
        Text('fade')
          .fontSize(this.columnTextSize)
          .fontWeight(this.columnTextFontWeight)
      }
      .width(this.columnWidth)
      .padding(this.columnPadding)
      .margin(this.columnMargin)
      .borderRadius(this.columnBorderRadius)
      .shadow(this.columnShadow)
      .onClick(() => {
        this.homePageTransitionType = NavigationSystemTransitionType.FADE;
        this.stack.pushPath({name: 'Fade'});
      })

      Column() {
        Text('explode')
          .fontSize(this.columnTextSize)
          .fontWeight(this.columnTextFontWeight)
      }
      .width(this.columnWidth)
      .padding(this.columnPadding)
      .margin(this.columnMargin)
      .borderRadius(this.columnBorderRadius)
      .shadow(this.columnShadow)
      .onClick(() => {
        this.homePageTransitionType = NavigationSystemTransitionType.EXPLODE;
        this.stack.pushPath({name: 'Explode'});
      })

      Column() {
        Text('slide right')
          .fontSize(this.columnTextSize)
          .fontWeight(this.columnTextFontWeight)
      }
      .width(this.columnWidth)
      .padding(this.columnPadding)
      .margin(this.columnMargin)
      .borderRadius(this.columnBorderRadius)
      .shadow(this.columnShadow)
      .onClick(() => {
        this.homePageTransitionType = NavigationSystemTransitionType.SLIDE_RIGHT;
        this.stack.pushPath({name: 'SlideRight'});
      })

      Column() {
        Text('slide bottom')
          .fontSize(this.columnTextSize)
          .fontWeight(this.columnTextFontWeight)
      }
      .width(this.columnWidth)
      .padding(this.columnPadding)
      .margin(this.columnMargin)
      .borderRadius(this.columnBorderRadius)
      .shadow(this.columnShadow)
      .onClick(() => {
        this.homePageTransitionType = NavigationSystemTransitionType.SLIDE_BOTTOM;
        this.stack.pushPath({name: 'SlideBottom'});
      })
    }
  }
}
```
![navdestination_fade](figures/navdestination_fade_transition.gif)
![navdestination_explode](figures/navdestination_explode_transition.gif)
![navdestination_slide_bottom](figures/navdestination_slide_bottom_transition.gif)
![navdestination_slide_right](figures/navdestination_slide_right_transition.gif)

### 示例4（NavDestination配置页面方向和对应状态栏、导航条显隐）

以下示例主要演示每个NavDestination可以配置指定的页面方向和状态栏，导航条显隐状态。

```ts
import { window } from '@kit.ArkUI';

@Component
struct PortraitPage {
  @State info: string = '';
  private stack: NavPathStack | undefined = undefined;
  build() {
    NavDestination() {
      Stack({alignContent: Alignment.Center}) {
        Button('push LANDSCAPE page').onClick(() => {
          this.stack?.pushPath({name: 'landscape'});
        })
      }.width('100%').height('100%')
    }
    .width('100%').height('100%')
    .title('PortraitPage')
    .preferredOrientation(window.Orientation.PORTRAIT) // 竖屏方向
    .enableStatusBar(true) // 显示状态栏
    .enableNavigationIndicator(true) // 显示导航条
    .backgroundColor('#ffbaece9')
    .onResult((result: ESObject)=>{
      this.info = result as string;
    })
    .onReady((ctx: NavDestinationContext) => {
      this.stack = ctx.pathStack;
    })
  }
}

@Component
struct LandscapePage {
  private stack: NavPathStack | undefined = undefined;
  build() {
    NavDestination() {
      Stack({alignContent: Alignment.Center}) {
        Button('push PORTRAIT page').onClick(() => {
          this.stack?.pushPath({name: 'portrait'});
        })
      }.width('100%').height('100%')
    }
    .width('100%').height('100%')
    .title('LandscapePage')
    .preferredOrientation(window.Orientation.LANDSCAPE) // 横屏方向
    .enableStatusBar(false) // 隐藏状态栏
    .enableNavigationIndicator(false) // 隐藏导航条
    .backgroundColor('#ffecb8b8')
    .ignoreLayoutSafeArea([LayoutSafeAreaType.SYSTEM], [LayoutSafeAreaEdge.TOP, LayoutSafeAreaEdge.BOTTOM])
    .onReady((ctx: NavDestinationContext) => {
      this.stack = ctx.pathStack;
    })
  }
}

@Entry
@Component
struct ExamplePage {
  private stack: NavPathStack = new NavPathStack();

  aboutToAppear(): void {
    this.stack.pushPath({name: "portrait"});
  }

  @Builder
  MyPageMap(name: string) {
    if (name === 'portrait') {
      PortraitPage();
    } else {
      LandscapePage();
    }
  }

  build() {
    Navigation(this.stack) {
    }
    .width('100%')
    .height('100%')
    .hideNavBar(true)
    .navDestination(this.MyPageMap)
  }
}
```
![navdestination_orientation](figures/navdestination_orientation.gif)

NavDestination其他用法可参考[Navigation示例](ts-basic-components-navigation.md#示例)。
