# MultiNavPathStack

MultiNavigation的路由栈仅支持由使用方自行创建，不支持通过回调方式获取。请勿使用NavDestination的 onReady等类似事件或接口来获取NavPathStack并进行栈操作，因为这可能会导致不可预知的问题。

**继承/实现关系：** MultiNavPathStack extends [NavPathStack](../arkts-components/arkts-arkui-navpathstack-c.md)

**起始版本：** 14

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SplitPolicy, MultiNavigation, MultiNavPathStack } from '@kit.ArkUI';
```

## clear

```TypeScript
clear(animated?: boolean): void
```

清除栈中所有页面。

> **说明：**

> 当调用[keepBottomPage](#keepbottompage)接口并设置为true时，会保留栈底页面。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |

## constructor

```TypeScript
constructor()
```

创建MultiNavPathStack路由栈实例。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disableAnimation

```TypeScript
disableAnimation(disable: boolean): void
```

关闭（true）或打开（false）当前MultiNavigation中所有转场动画。适用于需要提升页面切换性能或实现自定义转场效果的场景。

> **说明：**
> 
> 此配置会影响以下栈操作方法的动画效果：pushPath、pushPathByName、replacePath、replacePathByName、pop、popToName、
> popToIndex、moveToTop、moveIndexToTop、clear。配置立即生效，在MultiNavigation生命周期内持续有效。
> 建议在批量栈操作前调用disableAnimation(true)关闭动画以提升性能，操作完成后调用disableAnimation(false)恢复动画。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disable | boolean | 是 | 是否关闭转场动画。默认值：false true：关闭转场动画。false：不关闭转场动画。 |

## getAllPathName

```TypeScript
getAllPathName(): Array<string>
```

获取栈中所有NavDestination页面的名称。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;string & gt; | 返回栈中所有NavDestination页面的名称，数组元素按栈底到栈顶的顺序排列。 |

## getIndexByName

```TypeScript
getIndexByName(name: string): Array<number>
```

获取全部名为name的NavDestination页面的位置索引。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;number & gt; | Indexes of all the matching navigation destination pages. |

## getParamByIndex

```TypeScript
getParamByIndex(index: number): Object | undefined
```

获取index指定的NavDestination页面的参数信息。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestination页面的位置索引。取值范围：[0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| unknown \| undefined | Object**: 返回对应NavDestination页面的参数信息，具体字段由pushPath或pushPathByName时传入的param决定。 |

## getParamByName

```TypeScript
getParamByName(name: string): Array<Object>
```

获取全部名为name的NavDestination页面的参数信息。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;Object & gt; | 返回全部名为name的NavDestination页面的参数信息。 |

## keepBottomPage

```TypeScript
keepBottomPage(keepBottom: boolean): void
```

设置在调用pop和clear接口时是否保留栈底页面。

> **说明：**

> MultiNavigation将主页也当作了NavDestination页面入栈，所以调用pop或clear接口时会将栈底页面也出栈。
> 
> 应用调用此接口并设置为true时，MultiNavigation会在调用pop和clear接口时保留栈底页面。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keepBottom | boolean | 是 | 是否保留栈底页面。默认值：false true：保留栈底页面。false：不保留栈底页面。 |

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestination页面的位置索引。取值范围：[0, +∞)。超出范围时操作不生效。 |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |

## moveToTop

```TypeScript
moveToTop(name: string, animated?: boolean): number
```

将由栈底开始第一个名为name的NavDestination页面移到栈顶。

> **说明：**

> 根据指定的index页面的不同，MultiNavigation会进行不同的处理：

> 1)当指定的是最上层主页或者全屏页的index，此时不做任何处理；

> 2)当指定的是最上层主页对应的详情页的index，则会将对应的详情页移到栈顶；

> 3)当指定的是非最上层的主页的index，则会将主页和对应所有详情页移到栈顶，详情页相对栈关系不变；

> 4)当指定的是非最上层的详情页的index，则会将主页和对应所有详情页移到栈顶，且将目标详情页移动到对应所有详情页的栈顶；

> 5)当指定的是非最上层的全屏页的index，则会将全屏页移动到栈顶。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 如果栈中存在名为name的NavDestination页面，则返回由栈底开始第一个名为name的NavDestination页面的索引，否则返回-1。 |

## pop

```TypeScript
pop(animated?: boolean): NavPathInfo | undefined
```

弹出路由栈栈顶元素。

> **说明：**

> 当调用[keepBottomPage](#keepbottompage)接口并设置为true时，会保留栈底页面。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) \| undefined | 返回栈顶NavDestination页面的信息。栈为空时返回undefined。 |

## pop

```TypeScript
pop(result?: Object, animated?: boolean): NavPathInfo | undefined
```

弹出路由栈栈顶元素，并触发onPop回调传入页面处理结果。

> **说明：**

> 当调用[keepBottomPage](#keepbottompage)接口并设置为true时，会保留栈底页面。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | Object | 否 | 页面自定义处理结果。具体内容由开发者自定义，建议包含明确的业务标识和处理结果数据。该结果将传递给入栈时设置的onPop回调函数。省略时不传递结果数据。 |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) \| undefined | 返回栈顶NavDestination页面的信息。栈为空时返回undefined。 |

## popToIndex

```TypeScript
popToIndex(index: number, animated?: boolean): void
```

回退路由栈到index指定的NavDestination页面。当index无效（超出范围）时，不执行回退操作。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestination页面的位置索引。取值范围：[0, +∞)。超出范围时操作不生效。 |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |

## popToIndex

```TypeScript
popToIndex(index: number, result: Object, animated?: boolean): void
```

回退路由栈到index指定的NavDestination页面，并触发onPop回调传入页面处理结果。当index无效（超出范围）时，不执行回退操作。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestination页面的位置索引。取值范围：[0, +∞)。超出范围时操作不生效。 |
| result | Object | 是 | 页面自定义处理结果。具体内容由开发者自定义，建议包含明确的业务标识和处理结果数据。 |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |

## popToName

```TypeScript
popToName(name: string, animated?: boolean): number
```

回退路由栈到由栈底开始第一个名为name的NavDestination页面。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the bottom of the navigation stack; returns **-1** if no such a page is found. |

## popToName

```TypeScript
popToName(name: string, result: Object, animated?: boolean): number
```

回退路由栈到由栈底开始第一个名为name的NavDestination页面，并触发onPop回调传入页面处理结果。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| result | Object | 是 | 页面自定义处理结果。具体内容由开发者自定义，建议包含明确的业务标识和处理结果数据。该结果将传递给入栈时设置的onPop回调函数。 |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Returns the index of the first navigation destination page that matches **name** from the bottom of the navigation stack; returns **-1** if no such a page is found. |

## pushPath

```TypeScript
pushPath(info: NavPathInfo, animated?: boolean, policy?: SplitPolicy): void
```

将指定的NavDestination页面信息入栈。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | 否 | 当前入栈页面的策略。默认值：DETAIL_PAGE |

## pushPath

```TypeScript
pushPath(info: NavPathInfo, options?: NavigationOptions, policy?: SplitPolicy): void
```

将指定的NavDestination页面信息入栈，通过NavigationOptions设置页面栈操作选项。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigationoptions-i.md) | 否 | 页面栈操作选项。仅支持其中的animated字段，使用其他字段将被忽略。省略时使用默认动画配置。 |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | 否 | 当前入栈页面的策略。默认值：DETAIL_PAGE |

## pushPathByName

```TypeScript
pushPathByName(name: string, param: Object, animated?: boolean, policy?: SplitPolicy): void
```

将name指定的NavDestination页面信息入栈，传递的数据为param。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。需要与NavDestinationBuildFunction中注册的页面名称一致。 |
| param | Object | 是 | NavDestination页面详细参数，用于向目标页面传递自定义数据。具体字段规格请参考NavDestination相关文档。 |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | 否 | 当前入栈页面的策略。默认值：DETAIL_PAGE |

## pushPathByName

```TypeScript
pushPathByName(
    name: string, param: Object, onPop?: base.Callback<PopInfo>, animated?: boolean, policy?: SplitPolicy): void
```

将name指定的NavDestination页面信息入栈，传递的数据为param，添加onPop回调接收入栈页面出栈时的返回结果，并进行处理。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。需要与NavDestinationBuildFunction中注册的页面名称一致。 |
| param | Object | 是 | NavDestination页面详细参数，用于向目标页面传递自定义数据。具体字段规格请参考NavDestination相关文档。 |
| onPop | base.Callback&lt;[PopInfo](../arkts-components/arkts-arkui-popinfo-i.md)&gt; | 否 | Callback回调，用于页面出栈时触发该回调处理返回结果。省略时不触发回调处理。 可通过pop方法、popToName方法、popToIndex方法的result参数传递数据给此回调。 |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |
| policy | [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | 否 | 当前入栈页面的策略。默认值：DETAIL_PAGE |

## removeByIndexes

```TypeScript
removeByIndexes(indexes: Array<number>): number
```

将页面栈内索引值在indexes中的NavDestination页面删除。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indexes | Array & lt;number & gt; | 是 | 待删除NavDestination页面的索引值数组。number类型的取值范围：[0, +∞)。超出范围时操作不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回删除的NavDestination页面数量。 |

## removeByName

```TypeScript
removeByName(name: string): number
```

将页面栈内指定name的NavDestination页面删除。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 待删除NavDestination页面的名字。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回删除的NavDestination页面数量。 |

## replacePath

```TypeScript
replacePath(info: NavPathInfo, animated?: boolean): void
```

将当前页面栈栈顶退出，将指定的NavDestination页面信息入栈，新页面的分栏策略继承原栈顶页面的策略。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |

## replacePath

```TypeScript
replacePath(info: NavPathInfo, options?: NavigationOptions): void
```

将当前页面栈栈顶退出，将指定的NavDestination页面信息入栈，新页面的分栏策略继承原栈顶页面的策略，通过NavigationOptions设置页面栈操作选项。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigationoptions-i.md) | 否 | 页面栈操作选项。仅支持其中的animated字段。 |

## replacePathByName

```TypeScript
replacePathByName(name: string, param: Object, animated?: boolean): void
```

将当前页面栈栈顶退出，将name指定的页面入栈，新页面的分栏策略继承原栈顶页面的策略。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | NavDestination页面详细参数。 |
| animated | boolean | 否 | 是否支持转场动画。默认值：true true：支持转场动画。false：不支持转场动画。 |

## setHomeWidthRange

```TypeScript
setHomeWidthRange(minPercent: number, maxPercent: number): void
```

设置主页宽度可拖动范围。应用不设置的情况下宽度为50%，且不可拖动。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minPercent | number | 是 | 最小主页宽度百分比。取值范围：[0, 100]，且需小于等于maxPercent。 |
| maxPercent | number | 是 | 最大主页宽度百分比。取值范围：[0, 100]，且需大于等于minPercent。 |

## setPlaceholderPage

```TypeScript
setPlaceholderPage(info: NavPathInfo): void
```

设置占位页面。

> **说明：**

> 占位页面为特殊页面类型，当应用设置后，在支持分栏显示的大屏设备上会和主页默认形成左右分栏的效果，即左边主页，右边占位页。
> 
> 当应用可绘制区域小于600vp、折叠屏由展开态切换为折叠态及平板横屏转竖屏等场景时，会自动将占位页出栈，只显示主页；
> 
> 而当应用可绘制区域大于等于600vp、折叠屏由折叠态切换为展开态及平板竖屏转横屏等场景时，会自动补充占位页，形成分栏。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | 占位页页面信息，用于设置占位页。占位页在大屏设备上会与主页形成左右分栏效果。 |

## size

```TypeScript
size(): number
```

获取栈大小。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Stack size. |

## switchFullScreenState

```TypeScript
switchFullScreenState(isFullScreen?: boolean): boolean
```

切换当前栈顶详情页面的显示模式。适用于视频播放、图片浏览等需要全屏展示的场景。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isFullScreen | boolean | 否 | 是否切换为全屏模式。默认值：false true：全屏模式；false：分栏模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 切换成功或失败。 |
