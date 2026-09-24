# TabContent属性/事件

```TypeScript
declare class TabContentAttribute extends CommonMethod<TabContentAttribute>
```

除支持通用属性外，还支持以下属性：

除支持通用事件外，还支持以下事件：

**继承/实现关系：** TabContentAttribute extends CommonMethod<TabContentAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillHide

```TypeScript
onWillHide(event: VoidCallback)
```

逻辑回调，TabContent将要隐藏的时候触发该回调。场景包括TabContent切换，页面切换，窗口前后台切换。

> **说明：** 

> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | TabContent将要隐藏的回调函数。 |

## onWillShow

```TypeScript
onWillShow(event: VoidCallback)
```

逻辑回调，TabContent将要显示的时候触发该回调。场景包括TabContent首次显示，TabContent切换，页面切换，窗口前后台切换。

> **说明：** 

> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | TabContent将要显示的回调函数。 |

## tabBar

```TypeScript
tabBar(options: string | Resource | CustomBuilder | TabBarOptions)
```

设置TabBar上显示内容。

设置的内容超出tabBar页签时进行裁切。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; [TabBarOptions](arkts-arkui-tabcontent-comp-tabbaroptions-i.md) | 是 | TabBar上显示内容。<br>CustomBuilder：?构造器，内部可以传入组件（API version 8版本以上适用）。<br>**适用版本：** 18 |

<a id="tabbar-1"></a>

## tabBar

```TypeScript
tabBar(value: SubTabBarStyle | BottomTabBarStyle)
```

设置TabBar上显示内容。底部样式没有下划线效果。当图标资源加载失败或不存在时，显示灰色图块。

如果icon采用svg格式图源，需删除其内置的宽高属性。否则，icon大小将使用svg图源内置的宽高属性值。

设置的内容超出TabBar页签时进行裁切。

> **说明：** 

> - 子页签（[SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md)）样式：通常为文字+下划线或文字+背板的页签风格，允许设置文本样式，建议放置在顶部或者底部使用。切换页签时默认支持动画跳转效果。适用于资讯类应用的顶部分类（如"关注、视频、数码"）、功能模块的二级导航场景。
> 
> - 底部页签/侧边页签（[BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md)）样式：无下划线和背板效果，页签样式通常为图标+文字的组合方式。切换页签时默认无动画跳转效果。底部页签通常用于应用主导航（如首页、发现、推荐）。侧边页签适用于宽屏场景，可设置vertical(true)启用纵向布局，让页签在侧边显示，默认左侧显示。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) &#124; [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) | 是 | TabBar上显示的内容，支持子页签样式或底部页签样式。<br>SubTabBarStyle：?子页签样式。<br> BottomTabBarStyle：?底部页签和侧边页签样式，底部样式没有下划线效果。 |

<a id="tabbar-2"></a>

## tabBar

```TypeScript
tabBar(content: ComponentContent | SubTabBarStyle | BottomTabBarStyle | string | Resource | CustomBuilder | 
    TabBarOptions)
```

设置TabBar上显示内容。

使用BottomTabBarStyle或TabBarOptions类型作为入参并设置icon，当图标资源加载失败或不存在时，显示灰色图块。如果icon采用svg格式图源，需删除其内置的宽高属性。否则，icon大小将使用svg图源内置的宽高属性值。

设置的内容超出TabBar页签时进行裁切。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent &#124; [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) &#124; [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; [TabBarOptions](arkts-arkui-tabcontent-comp-tabbaroptions-i.md) | 是 | Content displayed on the tab bar.<br>**ComponentContent**: encapsulation of the component content, which can be customized.<br>**SubTabBarStyle**: subtab style.<br>**BottomTabBarStyle**: style of the bottom and side tabs. The bottom style does not have the underline effect.<br>**string**: string type.<br>**Resource**: resource reference for importing strings from system or application resources.<br>**CustomBuilder**: builder that can take components as arguments.<br>**TabBarOptions**: options for configuring images and text content on the tabs. |
