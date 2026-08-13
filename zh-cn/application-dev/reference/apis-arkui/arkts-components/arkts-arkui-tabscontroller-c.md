# TabsController

Tabs组件的控制器，用于控制Tabs组件进行页签切换。不支持一个TabsController控制多个Tabs组件。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-unnamed-declare class TabsController--><!--Device-unnamed-declare class TabsController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## changeIndex

```TypeScript
changeIndex(value: number): void
```

控制Tabs切换到指定页签。在需要通过按钮、下拉菜单或其他控件实现页签跳转功能时使用，例如点击“上一页”/“下一页”按钮切换页签。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsController-changeIndex(value: number): void--><!--Device-TabsController-changeIndex(value: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 页签在Tabs里的索引值，索引值从0开始。取值范围：[0, 页签总数-1]。设置范围外的值时按0处理。 |

## constructor

```TypeScript
constructor()
```

TabsController的构造函数。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsController-constructor()--><!--Device-TabsController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## preloadItems

```TypeScript
preloadItems(indices: Optional<Array<number>>): Promise<void>
```

控制Tabs预加载指定子节点。调用该接口后会一次性加载所有指定的子节点，因此为了性能考虑，建议分批加载子节点。适用于需要提前加载某些页签以提高切换性能的场景，如某些页签内容较复杂或资源较多时，可预加载以优化用户体验。 > **说明：** > - Tabs的preloadItems需要在Tabs创建之后去调用，首次预加载推荐在Tabs的onAppear生命周期中去控制。 > > - 如果TabsController对象未绑定任何Tabs组件，直接调用该接口，会抛出JS异常。因此使用该接口时，建议通过try-catch捕获异常。 > > - 使用preloadItems预加载标签页时，若需自定义TabBar上的显示内容，推荐使用ComponentContent实现，使用示例请参考 > [示例9](../../../reference/apis-arkui/arkui-ts/ts-container-tabcontent.md#示例9通过componentcontent设置tabbar)。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TabsController-preloadItems(indices: Optional<Array<number>>): Promise<void>--><!--Device-TabsController-preloadItems(indices: Optional<Array<number>>): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indices | Optional&lt;Array&lt;number&gt;&gt; | 是 | 需预加载的子节点的下标数组。&lt;br/&gt;默认值：空数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter invalid. Possible causes: &lt;br&gt; 1. The parameter type is not Array&lt;number&gt;. &lt;br&gt; 2. The parameter is an empty array. &lt;br&gt; 3. The parameter contains an invalid index. |

## setTabBarOpacity

```TypeScript
setTabBarOpacity(opacity: number): void
```

设置TabBar的不透明度。适用于需要调整TabBar显示透明度的场景，如TabBar渐隐渐显效果、降低TabBar视觉干扰突出内容等。 > **说明：** > 当使用 > [bindTabsToScrollable](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindTabsToScrollable)或 > [bindTabsToNestedScrollable](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindTabsToNestedScrollable) > 等接口绑定了Tabs组件和可滚动容器组件后，在滑动可滚动容器组件时，会触发所有与其绑定的Tabs组件的TabBar的显示和隐藏动效，调用setTabBarOpacity接口设置的TabBar不透明度会失效。因此不建议同时使用 > bindTabsToScrollable、bindTabsToNestedScrollable和setTabBarOpacity接口。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-TabsController-setTabBarOpacity(opacity: number): void--><!--Device-TabsController-setTabBarOpacity(opacity: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| opacity | number | 是 | 设置TabBar的不透明度，值为1.0表示完全不透明，值为0.0表示完全透明。取值范围为[0.0, 1.0]，设置的值小于0.0时，按0.0处理，设置的值大于1.0时，按1.0处理。&lt;br&gt; 默认值：1.0。 |

## setTabBarTranslate

```TypeScript
setTabBarTranslate(translate: TranslateOptions): void
```

设置TabBar的平移距离。适用于需要实现TabBar动态位置调整的场景，如TabBar滑动隐藏显示效果、配合页面滚动实现沉浸式体验等。 > **说明：** > 当使用 > [bindTabsToScrollable](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindTabsToScrollable)或 > [bindTabsToNestedScrollable](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindTabsToNestedScrollable) > 等接口绑定了Tabs组件和可滚动容器组件后，在滑动可滚动容器组件时，会触发所有与其绑定的Tabs组件的TabBar的显示和隐藏动效，调用setTabBarTranslate接口设置的TabBar平移距离会失效。因此不建议同时使 > 用bindTabsToScrollable、bindTabsToNestedScrollable和setTabBarTranslate接口。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-TabsController-setTabBarTranslate(translate: TranslateOptions): void--><!--Device-TabsController-setTabBarTranslate(translate: TranslateOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| translate | TranslateOptions | 是 | 设置TabBar的平移距离。 |

