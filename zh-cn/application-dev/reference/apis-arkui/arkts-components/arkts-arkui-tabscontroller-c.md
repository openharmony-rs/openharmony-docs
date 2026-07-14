# TabsController

Tabs组件的控制器，用于控制Tabs组件进行页签切换。不支持一个TabsController控制多个Tabs组件。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## changeIndex

```TypeScript
changeIndex(value: number): void
```

控制Tabs切换到指定页签。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 页签在Tabs里的索引值，索引值从0开始。<br/>**说明：** <br/>设置小于0或大于最大数量的值时，取默认值0。 |

## constructor

```TypeScript
constructor()
```

TabsController的构造函数。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## preloadItems

```TypeScript
preloadItems(indices: Optional<Array<number>>): Promise<void>
```

控制Tabs预加载指定子节点。调用该接口后会一次性加载所有指定的子节点，因此为了性能考虑，建议分批加载子节点。

> **说明：**

> - Tabs的preloadItems需要在Tabs创建之后去调用，首次预加载推荐在Tabs的[onAppear](arkts-arkui-commonmethod-c.md#onappear-1)生命周期中去控制。
>
> - 如果TabsController对象未绑定任何Tabs组件，直接调用该接口，会抛出JS异常。因此使用该接口时，建议通过try-catch捕获异常。
>
> - 使用preloadItems预加载标签页时，若需自定义TabBar上的显示内容，推荐使用ComponentContent实现，使用示例请参考
> [示例9](../../../../reference/apis-arkui/arkui-ts/ts-container-tabcontent.md#示例9通过componentcontent设置tabbar)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indices | Optional&lt;Array&lt;number&gt;&gt; | 是 | 需预加载的子节点的下标数组。<br/>默认值：空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 预加载完成后触发的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter invalid. Possible causes:<br> 1. The parameter type is not Array&lt;number&gt;.<br> 2. The parameter is an empty array.<br> 3. The parameter contains an invalid index. |

## setTabBarOpacity

```TypeScript
setTabBarOpacity(opacity: number): void
```

设置TabBar的不透明度。

> **说明：**

> 当使用
> [bindTabsToScrollable](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindtabstoscrollable13)或
> [bindTabsToNestedScrollable](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindtabstonestedscrollable13)
> 等接口绑定了Tabs组件和可滚动容器组件后，在滑动可滚动容器组件时，会触发所有与其绑定的Tabs组件的TabBar的显示和隐藏动效，调用setTabBarOpacity接口设置的TabBar不透明度会失效。因此不建议同时使用
> bindTabsToScrollable、bindTabsToNestedScrollable和setTabBarOpacity接口。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本13开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| opacity | number | 是 | 设置TabBar的不透明度，取值范围为[0.0, 1.0]，设置的值小于0.0时，按0.0处理，设置的值大于1.0时，按1.0处理。<br> 默认值：1.0。 |

## setTabBarTranslate

```TypeScript
setTabBarTranslate(translate: TranslateOptions): void
```

设置TabBar的平移距离。

> **说明：**

> 当使用
> [bindTabsToScrollable](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindtabstoscrollable13)或
> [bindTabsToNestedScrollable](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindtabstonestedscrollable13)
> 等接口绑定了Tabs组件和可滚动容器组件后，在滑动可滚动容器组件时，会触发所有与其绑定的Tabs组件的TabBar的显示和隐藏动效，调用setTabBarTranslate接口设置的TabBar平移距离会失效。因此不建议同时使
> 用bindTabsToScrollable、bindTabsToNestedScrollable和setTabBarTranslate接口。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本13开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| translate | TranslateOptions | 是 | 设置TabBar的平移距离。 |

