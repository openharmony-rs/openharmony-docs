# TabContent properties/events

```TypeScript
declare class TabContentAttribute extends CommonMethod<TabContentAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md), the following events are supported.

**Inheritance/Implementation:** TabContentAttribute extends CommonMethod&lt;TabContentAttribute&gt;

**Since:** 7

<!--Device-unnamed-declare class TabContentAttribute extends CommonMethod<TabContentAttribute>--><!--Device-unnamed-declare class TabContentAttribute extends CommonMethod<TabContentAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onWillHide

```TypeScript
onWillHide(event: VoidCallback)
```

Called when the tab content is about to be hidden. The scenarios include the tab switching, page switching, and window switching between the foreground and background.

> **NOTE:** 
> 
> This API can be called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabContentAttribute-onWillHide(event: VoidCallback): TabContentAttribute--><!--Device-TabContentAttribute-onWillHide(event: VoidCallback): TabContentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback for when the tab content is about to be hidden. |

## onWillShow

```TypeScript
onWillShow(event: VoidCallback)
```

Called when the tab content is about to be displayed. The scenarios include the first-time display, tab switching, page switching, and window switching between the foreground and background.

> **NOTE:** 
> 
> This API can be called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TabContentAttribute-onWillShow(event: VoidCallback): TabContentAttribute--><!--Device-TabContentAttribute-onWillShow(event: VoidCallback): TabContentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback for when the tab content is about to be displayed. |

<a id="tabbar1"></a>

## tabBar

```TypeScript
tabBar(options: string | Resource | CustomBuilder | TabBarOptions)
```

Sets the content displayed on the tab bar.

If the content exceeds the space provided by the tab bar, it will be clipped.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabContentAttribute-tabBar(options: string | Resource | CustomBuilder | TabBarOptions): TabContentAttribute--><!--Device-TabContentAttribute-tabBar(options: string | Resource | CustomBuilder | TabBarOptions): TabContentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; [TabBarOptions](arkts-arkui-tabcontent-comp-tabbaroptions-i.md) | Yes | Content displayed on the tab bar.<br>**CustomBuilder**: builder, to which components can be passed (applicable to API version 8 and later versions).<br>**Since:** 18 |

<a id="tabbar2"></a>

## tabBar

```TypeScript
tabBar(value: SubTabBarStyle | BottomTabBarStyle)
```

Sets the content displayed on the tab bar. The bottom tab style does not include an indicator. If the icon resource fails to be loaded or does not exist, a gray block is displayed.

If the icon uses an SVG image, you need to delete the built-in width and height attributes of the image. Otherwise, the width and height attribute values built in the SVG image source are used.

If the content exceeds the space provided by the tab bar, it will be clipped.

> **NOTE:** 
> 
> - Subtab style ([SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md)): Generally, the tab bar is in the style of text +underline or text + background. The text style can be set. It is recommended that the tab bar be placed at the top or bottom. By default, the animation transition effect is displayed when a tab is switched. This style is applicable to the top categories (such as Following, Video, Digital) of information apps and level-2 navigation scenarios of functional modules.
> 
> - [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md): icon + text, without underline or board. By default, no animation transition effect is displayed when a tab is switched. Bottom tabs are usually used for the main navigation of an app (such as Home, Discover, and Recommended). Side tabs are applicable to wide-screen scenarios. You can set
> **vertical(true)** to enable the vertical layout so that the tabs are displayed on the side. By default, the tabs
> are displayed on the left.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TabContentAttribute-tabBar(value: SubTabBarStyle | BottomTabBarStyle): TabContentAttribute--><!--Device-TabContentAttribute-tabBar(value: SubTabBarStyle | BottomTabBarStyle): TabContentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) &#124; [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) | Yes | Content displayed on the tab bar. The approved sample style of the sub tab bar or bottom tab bar is supported.<br>**SubTabBarStyle**: subtab style. <br>**BottomTabBarStyle**: style of the bottom and side tabs. The bottom style does not have the underline effect. |

<a id="tabbar3"></a>

## tabBar

```TypeScript
tabBar(content: ComponentContent | SubTabBarStyle | BottomTabBarStyle | string | Resource | CustomBuilder | 
    TabBarOptions)
```

Sets the content displayed on the tab bar.

If the **BottomTabBarStyle** or **TabBarOptions** type is used as the input parameter and the **icon** is set, a gray block is displayed when the icon resource fails to be loaded or does not exist. If the **icon** uses the SVG image source, you need to delete the built-in width and height attributes of the image source. Otherwise, the width and height attribute values built in the SVG image source are used.

If the content exceeds the space provided by the tab bar, it will be clipped.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TabContentAttribute-tabBar(content: ComponentContent | SubTabBarStyle | BottomTabBarStyle | string | Resource | CustomBuilder |     TabBarOptions): TabContentAttribute--><!--Device-TabContentAttribute-tabBar(content: ComponentContent | SubTabBarStyle | BottomTabBarStyle | string | Resource | CustomBuilder |     TabBarOptions): TabContentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | ComponentContent &#124; [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) &#124; [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md) &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) &#124; [TabBarOptions](arkts-arkui-tabcontent-comp-tabbaroptions-i.md) | Yes | Content displayed on the tab bar.<br>**ComponentContent**: encapsulation of the component content, which can be customized. <br>**NOTE:** <br>1. Custom content does not support the **labelStyle** attribute. <br>2. If the custom content exceeds the content box of the tab page, the excess part is not displayed. <br>3. If the custom content is within the content box of the tab page, it is aligned in the center. <br>4. If the custom content is abnormal or no display component is available, a blank area is displayed. <br>**SubTabBarStyle**: subtab style. <br>**BottomTabBarStyle**: style of the bottom and side tabs. The bottom style does not have the underline effect. <br>**string**: string type. <br>**Resource**: resource reference for importing strings from system or application resources. <br>**CustomBuilder**: builder that can take components as arguments. <br>**TabBarOptions**: options for configuring images and text content on the tabs. |

## tabBarVisibility

```TypeScript
tabBarVisibility(visibility: TabVisibility, displayMode?: TabBarDisplayMode)
```

Sets the default visibility of the tab.

> **NOTE:** 
> 
> - When **visibility** is **TabVisibility.HIDDEN** and **displayMode** is **TabBarDisplayMode.SIDEBAR**, the tab is not displayed in the sidebar but remains visible in the bottom tab bar.
> - When **visibility** is **TabVisibility.HIDDEN** and **displayMode** is **TabBarDisplayMode.BOTTOM_TABBAR**, the tab is not displayed in the bottom tab bar but remains visible in the sidebar.
> - When **visibility** is **TabVisibility.HIDDEN** and **displayMode** is not set, the tab is not displayed in both display modes.
> - Hidden tab content can still be switched and displayed using **TabsController.changeIndex()** or by modifying the **index** state variable.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-TabContentAttribute-tabBarVisibility(visibility: TabVisibility, displayMode?: TabBarDisplayMode): TabContentAttribute--><!--Device-TabContentAttribute-tabBarVisibility(visibility: TabVisibility, displayMode?: TabBarDisplayMode): TabContentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| visibility | [TabVisibility](arkts-arkui-tabcontent-comp-tabvisibility-e.md) | Yes | Visibility of the tab.<br>Default value: **TabVisibility.VISIBLE**. |
| displayMode | [TabBarDisplayMode](arkts-arkui-tabs-comp-tabbardisplaymode-e.md) | No | Display mode corresponding to the visibility.<br>When not set, **visibility** applies to both the sidebar and bottom tab bar.<br>When set to **TabBarDisplayMode.SIDEBAR**, **visibility** applies only to the sidebar.<br>When set to **TabBarDisplayMode.BOTTOM_TABBAR**, **visibility** applies only to the bottom tab bar. |
