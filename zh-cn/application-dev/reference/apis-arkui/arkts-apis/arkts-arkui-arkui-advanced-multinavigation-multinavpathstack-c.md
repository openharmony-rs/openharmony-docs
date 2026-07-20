# MultiNavPathStack

当前，MultiNavigation的路由栈仅支持由使用方自行创建，不支持通过回调方式获取。请勿使用[NavDestination](../arkts-components/arkts-arkui-navdestination.md)的[onReady](NavDestinationAttribute#onReady)等类似事件或接口来获取NavPathStack并进行栈操作，因为这可能会导致不可预知的问题。

**继承/实现关系：** MultiNavPathStack extends [NavPathStack](../arkts-components/arkts-arkui-navpathstack-c.md)

**起始版本：** 14

<!--Device-unnamed-export declare class MultiNavPathStack extends NavPathStack--><!--Device-unnamed-export declare class MultiNavPathStack extends NavPathStack-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { MultiNavPathStack, MultiNavigation, SplitPolicy } from '@kit.ArkUI';
```

<a id="clear"></a>
## clear

```TypeScript
clear(animated?: boolean): void
```

清除栈中所有页面。

> **说明：**

> 当调用[keepBottomPage](arkts-arkui-arkui-advanced-multinavigation-multinavpathstack-c.md#keepbottompage-1)接口并设置为true时，会保留栈底页面。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-clear(animated?: boolean): void--><!--Device-MultiNavPathStack-clear(animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

Creates an instance of MultiNavPathStack.

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-constructor()--><!--Device-MultiNavPathStack-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="disableanimation"></a>
## disableAnimation

```TypeScript
disableAnimation(disable: boolean): void
```

关闭（true）或打开（false）当前MultiNavigation中所有转场动画。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-disableAnimation(disable: boolean): void--><!--Device-MultiNavPathStack-disableAnimation(disable: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disable | boolean | 是 | 是否关闭转场动画。<br/>默认值：false<br/>true：关闭转场动画。<br/>false：不关闭转场动画。 |

<a id="getallpathname"></a>
## getAllPathName

```TypeScript
getAllPathName(): Array<string>
```

获取栈中所有NavDestination页面的名称。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-getAllPathName(): Array<string>--><!--Device-MultiNavPathStack-getAllPathName(): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回栈中所有NavDestination页面的名称。 |

<a id="getindexbyname"></a>
## getIndexByName

```TypeScript
getIndexByName(name: string): Array<number>
```

获取全部名为name的NavDestination页面的位置索引。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-getIndexByName(name: string): Array<number>--><!--Device-MultiNavPathStack-getIndexByName(name: string): Array<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | Indexes of all the matching navigation destination pages.<br>Value range of the number type: [0, +∞). |

<a id="getparambyindex"></a>
## getParamByIndex

```TypeScript
getParamByIndex(index: number): Object | undefined
```

获取index指定的NavDestination页面的参数信息。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-getParamByIndex(index: number): Object | undefined--><!--Device-MultiNavPathStack-getParamByIndex(index: number): Object | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestination页面的位置索引。<br/>取值范围：[0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | **Object**: parameter information of the matching navigation destination page.<br>**undefined**: returned when an invalid index is provided. |

<a id="getparambyname"></a>
## getParamByName

```TypeScript
getParamByName(name: string): Array<Object>
```

获取全部名为name的NavDestination页面的参数信息。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-getParamByName(name: string): Array<Object>--><!--Device-MultiNavPathStack-getParamByName(name: string): Array<Object>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Object&gt; | 返回全部名为name的NavDestination页面的参数信息。 |

<a id="keepbottompage"></a>
## keepBottomPage

```TypeScript
keepBottomPage(keepBottom: boolean): void
```

设置在调用pop和clear接口时是否保留栈底页面。

> **说明：**

> MultiNavigation将主页也当作了NavDestination页面入栈，所以调用pop或clear接口时会将栈底页面也出栈。  
> > 应用调用此接口并设置为true时，MultiNavigation会在调用pop和clear接口时保留栈底页面。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-keepBottomPage(keepBottom: boolean): void--><!--Device-MultiNavPathStack-keepBottomPage(keepBottom: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keepBottom | boolean | 是 | 是否保留栈底页面。<br/>默认值：false<br/>true：保留栈底页面。<br/>false：不保留栈底页面。 |

<a id="moveindextotop"></a>
## moveIndexToTop

```TypeScript
moveIndexToTop(index: number, animated?: boolean): void
```

将指定index的NavDestination页面移到栈顶。

> **说明：**

> 根据找到的第一个名为name的页面的不同，MultiNavigation会进行不同的处理：

> 1)当找到的是最上层主页或者全屏页，此时不做任何处理；

> 2)当找到的是最上层主页对应的详情页，则会将对应的详情页移到栈顶；

> 3)当找到的是非最上层的主页，则会将主页和对应所有详情页移到栈顶，详情页相对栈关系不变；

> 4)当找到的是非最上层的详情页，则会将主页和对应所有详情页移到栈顶，且将目标详情页移动到对应所有详情页的栈顶；

> 5)当找到的是非最上层的全屏页，则会将全屏页移动到栈顶。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-moveIndexToTop(index: number, animated?: boolean): void--><!--Device-MultiNavPathStack-moveIndexToTop(index: number, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestination页面的位置索引。<br/>取值范围：[0, +∞) |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |

<a id="movetotop"></a>
## moveToTop

```TypeScript
moveToTop(name: string, animated?: boolean): number
```

将由栈底开始第一个名为name的NavDestination页面移到栈顶。

> **说明：**

> 根据找到的第一个名为name的页面的不同，MultiNavigation会进行不同的处理：

> 1)当找到的是最上层主页或者全屏页，此时不做任何处理；

> 2)当找到的是最上层主页对应的详情页，则会将对应的详情页移到栈顶；

> 3)当找到的是非最上层的主页，则会将主页和对应所有详情页移到栈顶，详情页相对栈关系不变；

> 4)当找到的是非最上层的详情页，则会将主页和对应所有详情页移到栈顶，且将目标详情页移动到对应所有详情页的栈顶；

> 5)当找到的是非最上层的全屏页，则会将全屏页移动到栈顶。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-moveToTop(name: string, animated?: boolean): number--><!--Device-MultiNavPathStack-moveToTop(name: string, animated?: boolean): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 如果栈中存在名为name的NavDestination页面，则返回由栈底开始第一个名为name的NavDestination页面的索引，否则返回-1。 |

<a id="pop"></a>
## pop

```TypeScript
pop(animated?: boolean): NavPathInfo | undefined
```

弹出路由栈栈顶元素。

> **说明：**

> 当调用[keepBottomPage](arkts-arkui-arkui-advanced-multinavigation-multinavpathstack-c.md#keepbottompage-1)接口并设置为true时，会保留栈底页面。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-pop(animated?: boolean): NavPathInfo | undefined--><!--Device-MultiNavPathStack-pop(animated?: boolean): NavPathInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | Information about the navigation destination page at the top of the stack. |

<a id="pop-1"></a>
## pop

```TypeScript
pop(result?: Object, animated?: boolean): NavPathInfo | undefined
```

弹出路由栈栈顶元素，并触发onPop回调传入页面处理结果。

> **说明：**

> 当调用[keepBottomPage](arkts-arkui-arkui-advanced-multinavigation-multinavpathstack-c.md#keepbottompage-1)接口并设置为true时，会保留栈底页面。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-pop(result?: Object, animated?: boolean): NavPathInfo | undefined--><!--Device-MultiNavPathStack-pop(result?: Object, animated?: boolean): NavPathInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | Object | 否 | 页面自定义处理结果。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | Information about the navigation destination page at the top of the stack. |

<a id="poptoindex"></a>
## popToIndex

```TypeScript
popToIndex(index: number, animated?: boolean): void
```

回退路由栈到index指定的NavDestination页面。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-popToIndex(index: number, animated?: boolean): void--><!--Device-MultiNavPathStack-popToIndex(index: number, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestination页面的位置索引。<br/>取值范围：[0, +∞) |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |

<a id="poptoindex-1"></a>
## popToIndex

```TypeScript
popToIndex(index: number, result: Object, animated?: boolean): void
```

回退路由栈到index指定的NavDestination页面，并触发onPop回调传入页面处理结果。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-popToIndex(index: number, result: Object, animated?: boolean): void--><!--Device-MultiNavPathStack-popToIndex(index: number, result: Object, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestination页面的位置索引。<br/>取值范围：[0, +∞) |
| result | Object | 是 | 页面自定义处理结果。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |

<a id="poptoname"></a>
## popToName

```TypeScript
popToName(name: string, animated?: boolean): number
```

回退路由栈到由栈底开始第一个名为name的NavDestination页面。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-popToName(name: string, animated?: boolean): number--><!--Device-MultiNavPathStack-popToName(name: string, animated?: boolean): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the bottom of the navigation stack; returns **-1** if no such a page is found.<br>Value range: [-1, +∞). |

<a id="poptoname-1"></a>
## popToName

```TypeScript
popToName(name: string, result: Object, animated?: boolean): number
```

回退路由栈到由栈底开始第一个名为name的NavDestination页面，并触发onPop回调传入页面处理结果。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-popToName(name: string, result: Object, animated?: boolean): number--><!--Device-MultiNavPathStack-popToName(name: string, result: Object, animated?: boolean): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| result | Object | 是 | 页面自定义处理结果。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the bottom of the navigation stack; returns **-1** if no such a page is found.<br>Value range: [-1, +∞). |

<a id="pushpath"></a>
## pushPath

```TypeScript
pushPath(info: NavPathInfo, animated?: boolean, policy?: SplitPolicy): void
```

将指定的NavDestination页面信息入栈。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-pushPath(info: NavPathInfo, animated?: boolean, policy?: SplitPolicy): void--><!--Device-MultiNavPathStack-pushPath(info: NavPathInfo, animated?: boolean, policy?: SplitPolicy): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | 否 | 当前入栈页面的策略。默认值：DETAIL_PAGE |

<a id="pushpath-1"></a>
## pushPath

```TypeScript
pushPath(info: NavPathInfo, options?: NavigationOptions, policy?: SplitPolicy): void
```

将指定的NavDestination页面信息入栈，通过NavigationOptions设置页面栈操作选项。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-pushPath(info: NavPathInfo, options?: NavigationOptions, policy?: SplitPolicy): void--><!--Device-MultiNavPathStack-pushPath(info: NavPathInfo, options?: NavigationOptions, policy?: SplitPolicy): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigationoptions-i.md) | 否 | 页面栈操作选项。仅支持其中的animated字段。 |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | 否 | 当前入栈页面的策略。默认值：DETAIL_PAGE |

<a id="pushpathbyname"></a>
## pushPathByName

```TypeScript
pushPathByName(name: string, param: Object, animated?: boolean, policy?: SplitPolicy): void
```

将name指定的NavDestination页面信息入栈，传递的数据为param。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-pushPathByName(name: string, param: Object, animated?: boolean, policy?: SplitPolicy): void--><!--Device-MultiNavPathStack-pushPathByName(name: string, param: Object, animated?: boolean, policy?: SplitPolicy): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | NavDestination页面详细参数。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | 否 | 当前入栈页面的策略。默认值：DETAIL_PAGE |

<a id="pushpathbyname-1"></a>
## pushPathByName

```TypeScript
pushPathByName(
    name: string, param: Object, onPop?: base.Callback<PopInfo>, animated?: boolean, policy?: SplitPolicy): void
```

将name指定的NavDestination页面信息入栈，传递的数据为param，添加onPop回调接收入栈页面出栈时的返回结果，并进行处理。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-pushPathByName(
    name: string, param: Object, onPop?: base.Callback<PopInfo>, animated?: boolean, policy?: SplitPolicy): void--><!--Device-MultiNavPathStack-pushPathByName(
    name: string, param: Object, onPop?: base.Callback<PopInfo>, animated?: boolean, policy?: SplitPolicy): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | NavDestination页面详细参数。 |
| onPop | base.Callback&lt;PopInfo&gt; | 否 | Callback回调，用于页面出栈时触发该回调处理返回结果。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | 否 | 当前入栈页面的策略。默认值：DETAIL_PAGE |

<a id="removebyindexes"></a>
## removeByIndexes

```TypeScript
removeByIndexes(indexes: Array<number>): number
```

将页面栈内索引值在indexes中的NavDestination页面删除。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-removeByIndexes(indexes: Array<number>): number--><!--Device-MultiNavPathStack-removeByIndexes(indexes: Array<number>): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indexes | Array&lt;number&gt; | 是 | 待删除NavDestination页面的索引值数组。<br/>number类型的取值范围：[0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回删除的NavDestination页面数量。 |

<a id="removebyname"></a>
## removeByName

```TypeScript
removeByName(name: string): number
```

将页面栈内指定name的NavDestination页面删除。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-removeByName(name: string): number--><!--Device-MultiNavPathStack-removeByName(name: string): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 待删除NavDestination页面的名字。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回删除的NavDestination页面数量。 |

<a id="replacepath"></a>
## replacePath

```TypeScript
replacePath(info: NavPathInfo, animated?: boolean): void
```

将当前页面栈栈顶退出，将指定的NavDestination页面信息入栈，新页面的分栏策略继承原栈顶页面的策略。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-replacePath(info: NavPathInfo, animated?: boolean): void--><!--Device-MultiNavPathStack-replacePath(info: NavPathInfo, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |

<a id="replacepath-1"></a>
## replacePath

```TypeScript
replacePath(info: NavPathInfo, options?: NavigationOptions): void
```

将当前页面栈栈顶退出，将指定的NavDestination页面信息入栈，新页面的分栏策略继承原栈顶页面的策略，通过NavigationOptions设置页面栈操作选项。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-replacePath(info: NavPathInfo, options?: NavigationOptions): void--><!--Device-MultiNavPathStack-replacePath(info: NavPathInfo, options?: NavigationOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigationoptions-i.md) | 否 | 页面栈操作选项。仅支持其中的animated字段。 |

<a id="replacepathbyname"></a>
## replacePathByName

```TypeScript
replacePathByName(name: string, param: Object, animated?: boolean): void
```

将当前页面栈栈顶退出，将name指定的页面入栈，新页面的分栏策略继承原栈顶页面的策略。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-replacePathByName(name: string, param: Object, animated?: boolean): void--><!--Device-MultiNavPathStack-replacePathByName(name: string, param: Object, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | NavDestination页面详细参数。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>默认值：true<br/>true：支持转场动画。<br/>false：不支持转场动画。 |

<a id="sethomewidthrange"></a>
## setHomeWidthRange

```TypeScript
setHomeWidthRange(minPercent: number, maxPercent: number): void
```

设置主页宽度可拖动范围。应用不设置的情况下宽度为50%，且不可拖动。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-setHomeWidthRange(minPercent: number, maxPercent: number): void--><!--Device-MultiNavPathStack-setHomeWidthRange(minPercent: number, maxPercent: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minPercent | number | 是 | 最小主页宽度百分比。<br/>取值范围：[0, 100] |
| maxPercent | number | 是 | 最大主页宽度百分比。<br/>取值范围：[0, 100] |

<a id="setplaceholderpage"></a>
## setPlaceholderPage

```TypeScript
setPlaceholderPage(info: NavPathInfo): void
```

设置占位页面。

> **说明**

> 占位页面为特殊页面类型，当应用设置后，在一些大屏设备上会和主页默认形成左右分栏的效果，即左边主页，右边占位页。

> 当应用可绘制区域小于600vp、折叠屏由展开态切换为折叠态及平板横屏转竖屏等场景时，会自动将占位页出栈，只显示主页；  
> > 而当应用可绘制区域大于等于600vp、折叠屏由折叠态切换为展开态及平板竖屏转横屏等场景时，会自动补充占位页，形成分栏。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-setPlaceholderPage(info: NavPathInfo): void--><!--Device-MultiNavPathStack-setPlaceholderPage(info: NavPathInfo): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | 占位页页面信息。 |

<a id="size"></a>
## size

```TypeScript
size(): number
```

获取栈大小。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-size(): number--><!--Device-MultiNavPathStack-size(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Stack size.<br>Value range: [0, +∞). |

<a id="switchfullscreenstate"></a>
## switchFullScreenState

```TypeScript
switchFullScreenState(isFullScreen?: boolean): boolean
```

切换当前顶栈详情页面的显示模式。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MultiNavPathStack-switchFullScreenState(isFullScreen?: boolean): boolean--><!--Device-MultiNavPathStack-switchFullScreenState(isFullScreen?: boolean): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isFullScreen | boolean | 否 | 是否切换为全屏。默认值为false。true表示全屏模式，false表示分栏模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 切换成功或失败。<br/>true：切换成功。<br/>false：切换失败。 |

