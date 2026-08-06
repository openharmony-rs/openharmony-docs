# NavigationAttribute

除支持[通用属性]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_外，还支持以下属性：

**继承/实现关系：** NavigationAttribute extends [CommonMethod](../../../apis-na/arkts-apis/arkts-na-component/common-commonmethod-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface NavigationAttribute extends CommonMethod--><!--Device-unnamed-export declare interface NavigationAttribute extends CommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
default attributeModifier(modifier: AttributeModifier<NavigationAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

动态设置Navigation组件的属性方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default attributeModifier(modifier: AttributeModifier<NavigationAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-NavigationAttribute-default attributeModifier(modifier: AttributeModifier<NavigationAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| AttributeModifier&lt;CommonMethod&gt; \| undefined | 是 | 在当前组件上 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## backButtonIcon

```TypeScript
default backButtonIcon(icon: string | PixelMap | Resource | SymbolGlyphModifier | undefined, accessibilityText?: ResourceStr | undefined): this
```

设置标题栏中返回键图标和无障碍播报内容。 > **说明：** > > 不支持通过[SymbolGlyphModifier]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_对象的 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_属性修改图标大小、 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_属性修改 > 动效、\_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_属性修 > 改动效类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default backButtonIcon(icon: string | PixelMap | Resource | SymbolGlyphModifier | undefined, accessibilityText?: ResourceStr | undefined): this--><!--Device-NavigationAttribute-default backButtonIcon(icon: string | PixelMap | Resource | SymbolGlyphModifier | undefined, accessibilityText?: ResourceStr | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | string \| PixelMap \| Resource \| SymbolGlyphModifier \| undefined | 是 | 标题栏中返回键图标。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，显示返回键图标。 |
| accessibilityText | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 否 | 需要播报的内容。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，无播报内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## customNavContentTransition

```TypeScript
default customNavContentTransition(delegate: ((from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation) => NavigationAnimatedTransition | undefined) | undefined): this
```

自定义转场动画回调。取值为undefined时，不使用回调函数。 > **说明：** > > 从API version 20开始，该接口支持在 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > 中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default customNavContentTransition(delegate: ((from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation) => NavigationAnimatedTransition | undefined) | undefined): this--><!--Device-NavigationAttribute-default customNavContentTransition(delegate: ((from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation) => NavigationAnimatedTransition | undefined) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | ((from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation) =&gt; NavigationAnimatedTransition \| undefined) \| undefined | 是 | 自定义转场动画的回调函数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_from：退场Destination的页面信息。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_to：进场Destination的页面信息。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_operation：当前页面转场的类型。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当回调函数返回[NavigationAnimatedTransition]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_时，表示自定义转场动画协议；返回undefined时表示未定义，执行默认转场动效。 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，不使用自定义转场动画回调函数，执行默认转场动效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | Returns the instance of the NavigationAttribute. |

## divider

```TypeScript
default divider(style: NavigationDividerStyle | null): this
```

设置Navigation双栏模式下的分割线样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default divider(style: NavigationDividerStyle | null): this--><!--Device-NavigationAttribute-default divider(style: NavigationDividerStyle | null): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 是 | navigation divider style in split mode.\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 23 - 24 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | - 返回Navigation属性对象 |

## enableDragBar

```TypeScript
default enableDragBar(isEnabled: boolean | undefined): this
```

控制分栏场景下是否显示拖拽条。该属性在PC/2in1设备上不生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default enableDragBar(isEnabled: boolean | undefined): this--><!--Device-NavigationAttribute-default enableDragBar(isEnabled: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean \| undefined | 是 | 是否开启拖拽条，默认为无拖拽条样式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：有拖拽条样式；false：无拖拽条样式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_参数非法或为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | Returns the instance of the NavigationAttribute. |

## enableModeChangeAnimation

```TypeScript
default enableModeChangeAnimation(isEnabled: boolean | undefined): this
```

控制是否开启单双栏切换时的动效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default enableModeChangeAnimation(isEnabled: boolean | undefined): this--><!--Device-NavigationAttribute-default enableModeChangeAnimation(isEnabled: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean \| undefined | 是 | 是否开启单双栏切换动效。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：true\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：开启单双栏切换动效；false：关闭单双栏切换动效。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_参数非法或为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | Returns the instance of the NavigationAttribute. |

## enableToolBarAdaptation

```TypeScript
default enableToolBarAdaptation(enable: boolean | undefined): this
```

设置是否启用Navigation和NavDestination的工具栏[toolbarConfiguration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_自适应能力。关闭 此能力后，底部工具栏[toolbarConfiguration]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_将不会再移动至页面右上角的菜单中。该接口不适配于自定义菜单，使用该 接口需采用[NavigationMenuItem]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_接口来定义[菜单]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default enableToolBarAdaptation(enable: boolean | undefined): this--><!--Device-NavigationAttribute-default enableToolBarAdaptation(enable: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean \| undefined | 是 | 是否启用Navigation和NavDestination的工具栏自适应能力。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：true\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：启用Navigation和NavDestination的工具栏自适应能力。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_false：不启用Navigation和NavDestination的工具栏自适应能力。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_参数非法或为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableVisibilityLifecycleWithContentCover

```TypeScript
default enableVisibilityLifecycleWithContentCover(isEnabled: boolean | undefined): this
```

设置是否启用[NavDestination]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_页面 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_生命周期与全模态的联动触发。 > **说明：** > > 从API version 23开始，该接口支持在 > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_ > 中调用。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default enableVisibilityLifecycleWithContentCover(isEnabled: boolean | undefined): this--><!--Device-NavigationAttribute-default enableVisibilityLifecycleWithContentCover(isEnabled: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean \| undefined | 是 | 是否启用NavDestination页面onShown、onHidden生命周期与全模态的联动触发。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：true\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：全模态拉起时，会触发当前NavDestination页面的onHidden生命周期；全模态关闭时会触发当前NavDestination页面的onShown生命周期\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_false：NavDestination页面onHidden、onShown生命周期不会因为全模态的拉起、关闭而触发。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | - Returns the instance of the NavigationAttribute. |

## hideBackButton

```TypeScript
default hideBackButton(value: boolean | undefined): this
```

设置是否隐藏标题栏中的返回键。返回键仅在[titleMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_设置为NavigationTitleMode.Mini时才生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default hideBackButton(value: boolean | undefined): this--><!--Device-NavigationAttribute-default hideBackButton(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hideNavBar

```TypeScript
default hideNavBar(value: boolean | undefined): this
```

设置是否隐藏导航页。设置为true时，隐藏Navigation的导航页，包括标题栏、内容区和工具栏。如果此时路由栈中存在NavDestination页面，则直接显示栈顶NavDestination页面，反之显示空白。 从API version 9开始到API version 10仅在双栏模式下生效。从API version 11开始在单栏、双栏与自适应模式均生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default hideNavBar(value: boolean | undefined): this--><!--Device-NavigationAttribute-default hideNavBar(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hideTitleBar

```TypeScript
default hideTitleBar(value: boolean | undefined): this
```

Hide navigation title bar

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default hideTitleBar(value: boolean | undefined): this--><!--Device-NavigationAttribute-default hideTitleBar(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hideTitleBar

```TypeScript
default hideTitleBar(hide: boolean | undefined, animated: boolean | undefined): this
```

设置是否隐藏标题栏。与 [hideTitleBar]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 相比，新增标题栏显隐时是否使用动画。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default hideTitleBar(hide: boolean | undefined, animated: boolean | undefined): this--><!--Device-NavigationAttribute-default hideTitleBar(hide: boolean | undefined, animated: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean \| undefined | 是 |  |
| animated | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hideToolBar

```TypeScript
default hideToolBar(value: boolean | undefined): this
```

Hide tool bar

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default hideToolBar(value: boolean | undefined): this--><!--Device-NavigationAttribute-default hideToolBar(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hideToolBar

```TypeScript
default hideToolBar(hide: boolean | undefined, animated: boolean | undefined): this
```

设置是否隐藏工具栏。与 [hideToolBar]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 相比，新增工具栏显隐时是否使用动画。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default hideToolBar(hide: boolean | undefined, animated: boolean | undefined): this--><!--Device-NavigationAttribute-default hideToolBar(hide: boolean | undefined, animated: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean \| undefined | 是 |  |
| animated | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## ignoreLayoutSafeArea

```TypeScript
default ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType> | undefined, edges?: Array<LayoutSafeAreaEdge> | undefined): this
```

控制组件的布局，使其扩展到非安全区域。 > **说明：** > > - 组件设置ignoreLayoutSafeArea之后生效的条件为： > > 设置LayoutSafeAreaType.SYSTEM时，组件的边界与非安全区域重合时组件能够延伸到非安全区域下。 > > - 若组件扩展到非安全区域内，此时在非安全区域里触发的事件（例如：点击事件）等可能会被系统拦截，优先响应状态栏等系统组件。 > > - 组件想要扩展到非安全区域内，需隐藏或者设置标题栏和工具栏为[STACK]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType> | undefined, edges?: Array<LayoutSafeAreaEdge> | undefined): this--><!--Device-NavigationAttribute-default ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType> | undefined, edges?: Array<LayoutSafeAreaEdge> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| undefined | 否 | 配置扩展安全区域的类型。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_[LayoutSafeAreaType.SYSTEM] |
| edges | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| undefined | 否 | 配置扩展安全区域的方向。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 默认值：<br /   >[LayoutSafeAreaEdge.TOP, LayoutSafeAreaEdge.BOTTOM]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## menus

```TypeScript
default menus(items: Array<NavigationMenuItem> | CustomBuilder | undefined, options?: NavigationMenuOptions | undefined): this
```

设置页面右上角菜单。不设置时不显示菜单项。使用Array&lt;[NavigationMenuItem]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_&gt; 写法时，竖屏最多支持显示3个图标，横屏最多支持显示5个图标，多余的 图标会被放入自动生成的更多图标。 &gt; **说明：** > > 不支持通过[SymbolGlyphModifier]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_对象的 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_属性修改图标大小、 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_属性修改 > 动效、\_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_属性修 > 改动效类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default menus(items: Array<NavigationMenuItem> | CustomBuilder | undefined, options?: NavigationMenuOptions | undefined): this--><!--Device-NavigationAttribute-default menus(items: Array<NavigationMenuItem> | CustomBuilder | undefined, options?: NavigationMenuOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| CustomBuilder \| undefined | 是 |  |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 否 | 菜单选项。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按NavigationMenuOptions中的默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## minContentWidth

```TypeScript
default minContentWidth(value: Dimension | undefined): this
```

设置导航页内容区最小宽度（双栏模式下生效）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default minContentWidth(value: Dimension | undefined): this--><!--Device-NavigationAttribute-default minContentWidth(value: Dimension | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 导航页内容区最小宽度。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：360\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_单位：vp\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Auto模式断点计算：默认600vp，minNavBarWidth(240vp) + minContentWidth (360vp) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## mode

```TypeScript
default mode(value: NavigationMode | undefined): this
```

设置导航页的显示模式，支持单栏（Stack）、分栏（Split）和自适应（Auto）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default mode(value: NavigationMode | undefined): this--><!--Device-NavigationAttribute-default mode(value: NavigationMode | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## navBarPosition

```TypeScript
default navBarPosition(value: NavBarPosition | undefined): this
```

设置导航页位置。仅在[mode]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_设置为NavigationMode.Auto或NavigationMode.Split时生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default navBarPosition(value: NavBarPosition | undefined): this--><!--Device-NavigationAttribute-default navBarPosition(value: NavBarPosition | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## navBarWidth

```TypeScript
default navBarWidth(value: Length | Bindable<Length> | undefined): this
```

设置导航页宽度。仅在[mode]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_设置为NavigationMode.Auto或NavigationMode.Split时生效。 从API version 18开始，该参数支持\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_双向绑定变量。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default navBarWidth(value: Length | Bindable<Length> | undefined): this--><!--Device-NavigationAttribute-default navBarWidth(value: Length | Bindable<Length> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| Bindable&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## navBarWidthRange

```TypeScript
default navBarWidthRange(value: [
        Dimension,
        Dimension
    ] | undefined): this
```

设置导航页最小和最大宽度（双栏模式下生效）。未设置该接口时，最小宽度默认为240vp，最大宽度默认为组件宽度的40%，且不大于432vp，即导航页和内容区之间的分割线可以在此范围内进行拖拽。拖拽分割线使导航页宽度变化时，内容区 的内容会被压缩。 分割线的拖拽范围： | 条件| 拖拽范围 | | ----| ----------- | |navBarWidthRange和minContentWidth同时设置 | 满足minContentWidth所设置的值后，在navBarWidthRange所设置的范围内进行拖拽 | |navBarWidthRange和minContentWidth均不设置 | 在navBarWidthRange默认的最小和最大范围内进行拖拽 | |仅设置navBarWidthRange属性 | 在navBarWidthRange所设置的范围内进行拖拽，最大拖拽范围不能超过minContentWidth的默认值 | |仅设置minContentWidth属性 | 在navBarWidthRange默认的最小和最大范围内进行拖拽 | |仅设置navBarWidth属性 | 不支持拖拽 |

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default navBarWidthRange(value: [        Dimension,        Dimension    ] | undefined): this--><!--Device-NavigationAttribute-default navBarWidthRange(value: [        Dimension,        Dimension    ] | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [         Dimension,         Dimension     ] \| undefined | 是 | 导航页最小和最大宽度。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_参数非法或为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## navDestination

```TypeScript
default navDestination(builder: PageMapBuilder | undefined): this
```

创建NavDestination组件。使用builder函数，基于name和param构造NavDestination组件。builder下只能有一个根节点。builder中允许在NavDestination组件外包含一层自定 义组件， 但自定义组件不允许设置属性和事件，否则仅显示空白。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default navDestination(builder: PageMapBuilder | undefined): this--><!--Device-NavigationAttribute-default navDestination(builder: PageMapBuilder | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 创建NavDestination组件。name：NavDestination页面名称。param：开发者设置的NavDestination页面详细参数，unknown可以是用户自定义的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | Returns the instance of the NavigationAttribute. |

## onNavBarStateChange

```TypeScript
default onNavBarStateChange(callback: ((isVisible: boolean) => void) | undefined): this
```

导航页显示状态切换时触发该回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default onNavBarStateChange(callback: ((isVisible: boolean) => void) | undefined): this--><!--Device-NavigationAttribute-default onNavBarStateChange(callback: ((isVisible: boolean) => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ((isVisible: boolean) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onNavigationModeChange

```TypeScript
default onNavigationModeChange(callback: ((mode: NavigationMode) => void) | undefined): this
```

当Navigation首次显示或者单双栏状态发生变化时触发该回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default onNavigationModeChange(callback: ((mode: NavigationMode) => void) | undefined): this--><!--Device-NavigationAttribute-default onNavigationModeChange(callback: ((mode: NavigationMode) => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ((mode: NavigationMode) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onTitleModeChange

```TypeScript
default onTitleModeChange(callback: ((titleMode: NavigationTitleMode) => void) | undefined): this
```

当[titleMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_为NavigationTitleMode.Free时，随着可滚动组件的滑动标题栏模式发生变化时触发此回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default onTitleModeChange(callback: ((titleMode: NavigationTitleMode) => void) | undefined): this--><!--Device-NavigationAttribute-default onTitleModeChange(callback: ((titleMode: NavigationTitleMode) => void) | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ((titleMode: NavigationTitleMode) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## recoverable

```TypeScript
default recoverable(recoverable: boolean | undefined): this
```

配置Navigation是否可恢复。如配置为可恢复，当应用进程异常退出并重新冷启动时，可自动创建该Navigation，并恢复至异常退出时的路由栈。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default recoverable(recoverable: boolean | undefined): this--><!--Device-NavigationAttribute-default recoverable(recoverable: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recoverable | boolean \| undefined | 是 | Navigation是否可恢复，默认为不可恢复。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：路由栈可恢复；false：路由栈不可恢复。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_参数非法或为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | Returns the instance of the NavigationAttribute. |

## setNavigationOptions

```TypeScript
default setNavigationOptions(pathInfos?: NavPathStack, homeDestination?: HomePathInfo, moduleInfo?: NavigationModuleInfo): this
```

设置Navigation配置项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default setNavigationOptions(pathInfos?: NavPathStack, homeDestination?: HomePathInfo, moduleInfo?: NavigationModuleInfo): this--><!--Device-NavigationAttribute-default setNavigationOptions(pathInfos?: NavPathStack, homeDestination?: HomePathInfo, moduleInfo?: NavigationModuleInfo): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Navigation页面栈。 |
| homeDestination | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 自定义Navigation首页信息。 |
| moduleInfo | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 导航的页面路径和模块信息 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回导航属性的实例。 |

## setNavigationOptions

```TypeScript
default setNavigationOptions(pathInfos?: NavPathStack,  moduleInfo?: NavigationModuleInfo): this
```

设置导航选项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default setNavigationOptions(pathInfos?: NavPathStack,  moduleInfo?: NavigationModuleInfo): this--><!--Device-NavigationAttribute-default setNavigationOptions(pathInfos?: NavPathStack,  moduleInfo?: NavigationModuleInfo): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathInfos | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 导航栈 |
| moduleInfo | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 导航的pageInfo和模块信息 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回导航属性的实例。 |

## splitPlaceholder

```TypeScript
default splitPlaceholder<T extends Object>(placeholder: ComponentContent<T>): this
```

Navigation双栏模式下，支持设置右侧页面显示默认占位页，占位页仅作为UI展示页，不可获焦和响应事件。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default splitPlaceholder<T extends Object>(placeholder: ComponentContent<T>): this--><!--Device-NavigationAttribute-default splitPlaceholder<T extends Object>(placeholder: ComponentContent<T>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| placeholder | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 设置Navigation双栏模式下右侧的默认占位页。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | - Returns the instance of the NavigationAttribute. |

## systemBarStyle

```TypeScript
default systemBarStyle(style: SystemBarStyle | undefined): this
```

当Navigation中显示Navigation首页时，设置对应系统状态栏的样式。 > **说明：** > > > 从API version 20开始，该接口支持在 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > 中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default systemBarStyle(style: SystemBarStyle | undefined): this--><!--Device-NavigationAttribute-default systemBarStyle(style: SystemBarStyle | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 系统状态栏样式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，无样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## title

```TypeScript
default title(value: ResourceStr | CustomBuilder | NavigationCommonTitle | NavigationCustomTitle | undefined, options?: NavigationTitleOptions | undefined): this
```

设置页面标题。 > **说明：** > > 从API version 12开始，该接口支持在 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > 中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default title(value: ResourceStr | CustomBuilder | NavigationCommonTitle | NavigationCustomTitle | undefined, options?: NavigationTitleOptions | undefined): this--><!--Device-NavigationAttribute-default title(value: ResourceStr | CustomBuilder | NavigationCommonTitle | NavigationCustomTitle | undefined, options?: NavigationTitleOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| CustomBuilder \| NavigationCommonTitle \| NavigationCustomTitle \| undefined | 是 |  |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 否 | 标题栏选项。 包含标题栏背景颜色、标题栏背景模糊样式及模糊选项、标题栏背景属性、标题栏布局方式、标题栏起始端内间距、标题栏结束端内间距、主标题属性修改器、子标题属性修改器、是否响应悬停态。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按NavigationTitleOptions中的默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## titleMode

```TypeScript
default titleMode(value: NavigationTitleMode | undefined): this
```

设置页面标题栏显示模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default titleMode(value: NavigationTitleMode | undefined): this--><!--Device-NavigationAttribute-default titleMode(value: NavigationTitleMode | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## toolbarConfiguration

```TypeScript
default toolbarConfiguration(value: Array<ToolbarItem> | CustomBuilder | undefined, options?: NavigationToolbarOptions | undefined): this
```

设置工具栏内容。不设置时不显示工具栏。 > **说明：** > > 从API version 20开始，该接口支持在 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > 中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavigationAttribute-default toolbarConfiguration(value: Array<ToolbarItem> | CustomBuilder | undefined, options?: NavigationToolbarOptions | undefined): this--><!--Device-NavigationAttribute-default toolbarConfiguration(value: Array<ToolbarItem> | CustomBuilder | undefined, options?: NavigationToolbarOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; \| CustomBuilder \| undefined | 是 | 工具栏内容，使用Array&lt;[ToolbarItem]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_&gt;设置的工具栏有如下特性：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_工具栏所有选项均分底部工具栏，在每个均分内容区布局文本和图标。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_6\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_竖屏模式最多支持显示5个图标，多余的图标会被放入自动生成的更多图标。横屏模式时，如果为[Split]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_模式，仍按照竖屏模式显示，如果为[Stack]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_模式需配合menus属性的Array&lt;[NavigationMenuItem]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_&gt;使用，底部工具栏会自动隐藏，同时底部工具栏所有选项移动至页面右上角菜单。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_7\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_使用\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_写法为用户自定义工具栏选项，不具备以上功能。<br/   >取值为undefined时，无工具栏。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 否 | 工具栏选项。 包含工具栏背景颜色、工具栏背景模糊样式及模糊选项、工具栏背景属性、工具栏布局方式、是否隐藏工具栏的文本、工具栏更多图标的菜单选项。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按NavigationToolbarOptions中的默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

