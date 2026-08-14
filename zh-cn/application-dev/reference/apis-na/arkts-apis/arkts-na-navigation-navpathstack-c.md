# NavPathStack

Navigation导航控制器，以栈的数据结构管理Navigation中所有的子页面，并提供栈操作的方法用于控制Navigation中子页面的切换。 从API version 12开始，NavPathStack允许被继承，派生类对象可以替代基类NavPathStack对象使用。使用示例参见 示例10。 > **说明：** > > 1.连续调用多个导航控制器操作方法时，中间过程会被忽略，显示最终的栈操作结果。 > 例如：在Page1页面先pop再push一个Page1，系统会认为操作前和操作后的结果一致而不进行任何操作，如果需要强行push一个Page1实例，可以设置 > [NavigationOption](arkts-na-navigation-navigationoptions-i.md#NavigationOptions)中的launchMode属性值为LaunchMode.NEW_INSTANCE模式。 > > 2.不建议开发者通过监听页面生命周期的方式管理自己的导航控制器。 > > 3.在应用处于后台状态下，调用NavPathStack的栈操作方法，会在应用再次回到前台状态时触发刷新。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class NavPathStack--><!--Device-unnamed-export declare class NavPathStack-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clear

```TypeScript
clear(animated?: boolean): void
```

清除栈中所有页面。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-clear(animated?: boolean): void--><!--Device-NavPathStack-clear(animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

## constructor

```TypeScript
constructor()
```

创建NavPathStack对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-constructor()--><!--Device-NavPathStack-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disableAnimation

```TypeScript
disableAnimation(value: boolean): void
```

关闭（true）或打开（false）当前Navigation中所有转场动画。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-disableAnimation(value: boolean): void--><!--Device-NavPathStack-disableAnimation(value: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否关闭转场动画，&lt;br/&gt;默认值：false&lt;br/&gt;true：关闭转场动画。&lt;br/&gt;false：不关闭转场动画。 |

## getAllPathName

```TypeScript
getAllPathName(): Array<string>
```

获取栈中所有NavDestination页面的名称。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-getAllPathName(): Array<string>--><!--Device-NavPathStack-getAllPathName(): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回栈中所有NavDestination页面的名称。 |

## getIndexByName

```TypeScript
getIndexByName(name: string): Array<int>
```

获取全部名为name的NavDestination页面的位置索引。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-getIndexByName(name: string): Array<int>--><!--Device-NavPathStack-getIndexByName(name: string): Array<int>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;int&gt; | 返回全部名为name的NavDestination页面的位置索引。 当路由栈中不存在此name，返回空数组。索引取值范围为[0, 路由栈大小-1] |

## getParamByIndex

```TypeScript
getParamByIndex(index: int): Object | null | undefined
```

获取index指定的NavDestination页面的参数信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-getParamByIndex(index: int): Object | null | undefined--><!--Device-NavPathStack-getParamByIndex(index: int): Object | null | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | NavDestination页面的位置索引。 索引值从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | Returns the detailed parameter of the NavDestination if it exists in the stack, otherwise returns undefined; |

## getParamByName

```TypeScript
getParamByName(name: string): Array<Object | null | undefined>
```

获取所有名为name的NavDestination页面的参数信息，按页面索引从小到大排序。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-getParamByName(name: string): Array<Object | null | undefined>--><!--Device-NavPathStack-getParamByName(name: string): Array<Object | null | undefined>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Object \| null \| undefined&gt; | Returns the detailed parameter of all the NavDestinations. |

## getParent

```TypeScript
getParent(): NavPathStack | null
```

获取父NavPathStack。 当出现Navigation嵌套Navigation的情况时（可以是直接嵌套，也可以是间接嵌套），内部Navigation的NavPathStack能够获取到外层Navigation的NavPathStack。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-getParent(): NavPathStack | null--><!--Device-NavPathStack-getParent(): NavPathStack | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavPathStack](arkts-na-navigation-navpathstack-c.md) | Returns the parent of the current stack. If no parent, it returns null. |

## getPathStack

```TypeScript
getPathStack(): Array<NavPathInfo>
```

获取当前路由栈中的路由页面信息数组。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-getPathStack(): Array<NavPathInfo>--><!--Device-NavPathStack-getPathStack(): Array<NavPathInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[NavPathInfo](arkts-na-navigation-navpathinfo-c.md)&gt; | 当前路由栈中的路由页面信息数组。 |

## moveIndexToTop

```TypeScript
moveIndexToTop(index: int, animated?: boolean): void
```

将index指定的NavDestination页面移到栈顶。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-moveIndexToTop(index: int, animated?: boolean): void--><!--Device-NavPathStack-moveIndexToTop(index: int, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | NavDestination页面的位置索引。索引值从0开始。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

## moveToTop

```TypeScript
moveToTop(name: string, animated?: boolean): int
```

将由栈底开始第一个名为name的NavDestination页面移到栈顶。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-moveToTop(name: string, animated?: boolean): int--><!--Device-NavPathStack-moveToTop(name: string, animated?: boolean): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 如果栈中存在名为name的NavDestination页面，则返回由栈底开始第一个名为name的NavDestination页面的当前索引，否则返回-1。 |

## pop

```TypeScript
pop(animated?: boolean): NavPathInfo | undefined
```

弹出路由栈栈顶元素。 > **说明：** > > 连续调用多个导航控制器方法时，中间被pop的页面会被缓存，后续push同名页面时会优先复用该页面，不会走新的页面创建流程。 > 例如： > pathStack: NavPathStack = new NavPathStack() > // 初始页面栈为：[A] > pathStack.pop() > pathStack.pushPath(A) > pathStack.pushPath(B) > // 操作后页面栈为：[A B] > 此时A页面会被复用，不会走新的创建流程。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-pop(animated?: boolean): NavPathInfo | undefined--><!--Device-NavPathStack-pop(animated?: boolean): NavPathInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt; &lt;br&gt;默认值： true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavPathInfo](arkts-na-navigation-navpathinfo-c.md) | Returns the top NavPathInfo if the stack is not empty, otherwise returns undefined. |

## pop

```TypeScript
pop(result: Object, animated?: boolean): NavPathInfo | undefined
```

弹出路由栈栈顶元素，并触发onPop回调传入页面处理结果。 > **说明：** > > 连续调用多个导航控制器方法时，中间被pop的页面会被缓存，后续push同名页面时会优先复用该页面，不会走新的页面创建流程。 > 例如： > pathStack: NavPathStack = new NavPathStack() > // 初始页面栈为：[A] > pathStack.pop() > pathStack.pushPath(A) > pathStack.pushPath(B) > // 操作后页面栈为：[A B] > 此时A页面会被复用，不会走新的创建流程。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-pop(result: Object, animated?: boolean): NavPathInfo | undefined--><!--Device-NavPathStack-pop(result: Object, animated?: boolean): NavPathInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | Object | 是 | 页面自定义处理结果。不支持boolean类型。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt; &lt;br&gt;默认值： true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavPathInfo](arkts-na-navigation-navpathinfo-c.md) | Returns the top NavPathInfo if the stack is not empty, otherwise returns undefined. |

## popToIndex

```TypeScript
popToIndex(index: int, animated?: boolean): void
```

回退路由栈到index指定的NavDestination页面。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-popToIndex(index: int, animated?: boolean): void--><!--Device-NavPathStack-popToIndex(index: int, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | NavDestination页面的位置索引。索引值从0开始。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

## popToIndex

```TypeScript
popToIndex(index: int, result: Object, animated?: boolean): void
```

回退路由栈到index指定的NavDestination页面，并触发onPop回调传入页面处理结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-popToIndex(index: int, result: Object, animated?: boolean): void--><!--Device-NavPathStack-popToIndex(index: int, result: Object, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | NavDestination页面的位置索引。索引值从0开始。 |
| result | Object | 是 | 页面自定义处理结果。不支持boolean类型。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

## popToName

```TypeScript
popToName(name: string, animated?: boolean): int
```

回退路由栈到由栈底开始第一个名为name的NavDestination页面。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-popToName(name: string, animated?: boolean): int--><!--Device-NavPathStack-popToName(name: string, animated?: boolean): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 如果栈中存在名为name的NavDestination页面，则返回由栈底开始第一个名为name的NavDestination页面的索引，否则返回-1。 |

## popToName

```TypeScript
popToName(name: string, result: Object, animated?: boolean): int
```

回退路由栈到由栈底开始第一个名为name的NavDestination页面，并触发onPop回调传入页面处理结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-popToName(name: string, result: Object, animated?: boolean): int--><!--Device-NavPathStack-popToName(name: string, result: Object, animated?: boolean): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| result | Object | 是 | 页面自定义处理结果。不支持boolean类型。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 如果栈中存在名为name的NavDestination页面，则返回由栈底开始第一个名为name的NavDestination页面的索引，否则返回-1。 |

## pushDestination

```TypeScript
pushDestination(info: NavPathInfo, animated?: boolean): Promise<void>
```

将info指定的NavDestination页面信息入栈，使用Promise异步回调返回接口调用结果。 > **说明：** > > 不建议在[aboutToAppear](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear)中使用栈 > 操作，此时的页面还未构建完成，会导致白屏或跳转失败等问题。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-pushDestination(info: NavPathInfo, animated?: boolean): Promise<void>--><!--Device-NavPathStack-pushDestination(info: NavPathInfo, animated?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-na-navigation-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [100005](../../apis-arkui/errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../../apis-arkui/errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |

## pushDestination

```TypeScript
pushDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

将info指定的NavDestination页面信息入栈，使用Promise异步回调返回接口调用结果，具体根据options中指定不同的[LaunchMode](arkts-na-navigation-launchmode-e.md#LaunchMode)，来实现不同的行为。 > **说明：** > > 不建议在[aboutToAppear](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear)中使用栈 > 操作，此时的页面还未构建完成，会导致白屏或跳转失败等问题。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-pushDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>--><!--Device-NavPathStack-pushDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-na-navigation-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| options | [NavigationOptions](arkts-na-navigation-navigationoptions-i.md) | 否 | 路由栈操作选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异常返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [100005](../../apis-arkui/errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../../apis-arkui/errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |

## pushDestinationByName

```TypeScript
pushDestinationByName(name: string, param: Object, animated?: boolean): Promise<void>
```

将name指定的NavDestination页面信息入栈，传递的数据为param，使用Promise异步回调返回接口调用结果。 > **说明：** > > 不建议在[aboutToAppear](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear)中使用栈 > 操作，此时的页面还未构建完成，会导致白屏或跳转失败等问题。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-pushDestinationByName(name: string, param: Object, animated?: boolean): Promise<void>--><!--Device-NavPathStack-pushDestinationByName(name: string, param: Object, animated?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | 开发者设置的NavDestination页面详细参数。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异常返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [100005](../../apis-arkui/errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../../apis-arkui/errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |

## pushDestinationByName

```TypeScript
pushDestinationByName(name: string, param: Object, onPop: Callback<PopInfo>, animated?: boolean): Promise<void>
```

将name指定的NavDestination页面信息入栈，传递的数据为param，并且添加用于页面出栈时处理返回结果的onPop回调，使用Promise异步回调返回接口调用结果。 > **说明：** > > 不建议在[aboutToAppear](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear)中使用栈 > 操作，此时的页面还未构建完成，会导致白屏或跳转失败等问题。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-pushDestinationByName(name: string, param: Object, onPop: Callback<PopInfo>, animated?: boolean): Promise<void>--><!--Device-NavPathStack-pushDestinationByName(name: string, param: Object, onPop: Callback<PopInfo>, animated?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | 开发者设置的NavDestination页面详细参数。 |
| onPop | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;[PopInfo](arkts-na-navigation-popinfo-i.md)&gt; | 是 | Callback回调，用于页面出栈时处理返回结果。仅 [pop](#pop)、 [popToName](#popToName)、 [popToIndex](#popToIndex)中设置result参数后触发。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异常返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [100005](../../apis-arkui/errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../../apis-arkui/errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |

## pushPath

```TypeScript
pushPath(info: NavPathInfo, animated?: boolean): void
```

将info指定的NavDestination页面信息入栈。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-pushPath(info: NavPathInfo, animated?: boolean): void--><!--Device-NavPathStack-pushPath(info: NavPathInfo, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-na-navigation-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;传入参数非法时，按true处理。 |

## pushPath

```TypeScript
pushPath(info: NavPathInfo, options?: NavigationOptions): void
```

将info指定的NavDestination页面信息入栈，具体根据options中指定不同的[LaunchMode](arkts-na-navigation-launchmode-e.md#LaunchMode)，来实现不同的行为。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-pushPath(info: NavPathInfo, options?: NavigationOptions): void--><!--Device-NavPathStack-pushPath(info: NavPathInfo, options?: NavigationOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-na-navigation-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| options | [NavigationOptions](arkts-na-navigation-navigationoptions-i.md) | 否 | 路由栈操作选项。 |

## pushPathByName

```TypeScript
pushPathByName(name: string, param: Object | null | undefined, animated?: boolean): void
```

将name指定的NavDestination页面信息入栈，传递的数据为param。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-pushPathByName(name: string, param: Object | null | undefined, animated?: boolean): void--><!--Device-NavPathStack-pushPathByName(name: string, param: Object | null | undefined, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object \| null \| undefined | 是 | 开发者设置的NavDestination页面详细参数，unknown可以是用户自定义的类型。&lt;br/&gt;取值为undefined时，页面信 息无效。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

## pushPathByName

```TypeScript
pushPathByName(name: string, param: Object, onPop: Callback<PopInfo>, animated?: boolean): void
```

将name指定的NavDestination页面信息入栈，传递的数据为param，添加onPop回调接收入栈页面出栈时的返回结果，并进行处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-pushPathByName(name: string, param: Object, onPop: Callback<PopInfo>, animated?: boolean): void--><!--Device-NavPathStack-pushPathByName(name: string, param: Object, onPop: Callback<PopInfo>, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | 开发者设置的NavDestination页面详细参数。 |
| onPop | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;[PopInfo](arkts-na-navigation-popinfo-i.md)&gt; | 是 | Callback回调，用于页面出栈时触发该回调处理返回结果。仅 [pop](#pop)、 [popToName](#popToName)、 [popToIndex](#popToIndex)中设置result参数后触发。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

## removeByIndexes

```TypeScript
removeByIndexes(indexes: Array<int>): int
```

将路由栈内索引值在indexes中的NavDestination页面删除。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-removeByIndexes(indexes: Array<int>): int--><!--Device-NavPathStack-removeByIndexes(indexes: Array<int>): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indexes | Array&lt;int&gt; | 是 | 待删除NavDestination页面的索引值数组。索引值从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回删除的NavDestination页面数量。 |

## removeByName

```TypeScript
removeByName(name: string): int
```

将路由栈内指定name的NavDestination页面删除。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-removeByName(name: string): int--><!--Device-NavPathStack-removeByName(name: string): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 删除的NavDestination页面的名字。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回删除的NavDestination页面数量。 |

## removeByNavDestinationId

```TypeScript
removeByNavDestinationId(navDestinationId: string): boolean
```

将路由栈内指定navDestinationId的NavDestination页面删除。navDestinationId可以在NavDestination的 [onReady](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onready11)回调中获取，也可以在 [NavDestinationInfo](../../apis-arkui/arkts-apis/arkts-arkui-uiobserver-navdestinationinfo-i.md#NavDestinationInfo)中获取。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-removeByNavDestinationId(navDestinationId: string): boolean--><!--Device-NavPathStack-removeByNavDestinationId(navDestinationId: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navDestinationId | string | 是 | 删除的NavDestination页面的唯一标识符navDestinationId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否成功删除该页面，&lt;br/&gt;true：删除成功。&lt;br/&gt;false：删除失败。 |

## replaceDestination

```TypeScript
replaceDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

替换路由栈操作。使用Promise异步回调返回接口调用结果，具体根据options中指定不同的[LaunchMode](arkts-na-navigation-launchmode-e.md#LaunchMode)，来实现不同的行为。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-replaceDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>--><!--Device-NavPathStack-replaceDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-na-navigation-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| options | [NavigationOptions](arkts-na-navigation-navigationoptions-i.md) | 否 | 路由栈操作选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异常返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../../apis-arkui/errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [100005](../../apis-arkui/errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../../apis-arkui/errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |

## replacePath

```TypeScript
replacePath(info: NavPathInfo, animated?: boolean): void
```

将当前路由栈栈顶退出，将info指定的NavDestination页面信息入栈。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-replacePath(info: NavPathInfo, animated?: boolean): void--><!--Device-NavPathStack-replacePath(info: NavPathInfo, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-na-navigation-navpathinfo-c.md) | 是 | 新栈顶页面参数信息。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

## replacePath

```TypeScript
replacePath(info: NavPathInfo, options?: NavigationOptions): void
```

替换路由栈操作，具体根据options中指定不同的[LaunchMode](arkts-na-navigation-launchmode-e.md#LaunchMode)，来实现不同的行为。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-replacePath(info: NavPathInfo, options?: NavigationOptions): void--><!--Device-NavPathStack-replacePath(info: NavPathInfo, options?: NavigationOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-na-navigation-navpathinfo-c.md) | 是 | 新栈顶页面参数信息。 |
| options | [NavigationOptions](arkts-na-navigation-navigationoptions-i.md) | 否 | 路由栈操作选项。 |

## replacePathByName

```TypeScript
replacePathByName(name: string, param: Object, animated?: boolean): void
```

将当前路由栈栈顶退出，将name指定的页面入栈。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-replacePathByName(name: string, param: Object, animated?: boolean): void--><!--Device-NavPathStack-replacePathByName(name: string, param: Object, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | 开发者设置的NavDestination页面详细参数。 |
| animated | boolean | 否 | 是否支持转场动画。&lt;br/&gt;true：支持转场动画；false：不支持转场动画。&lt;br/&gt;默认值：true |

## setInterception

```TypeScript
setInterception(interception: NavigationInterception): void
```

设置Navigation页面跳转拦截回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-setInterception(interception: NavigationInterception): void--><!--Device-NavPathStack-setInterception(interception: NavigationInterception): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| interception | [NavigationInterception](arkts-na-navigation-navigationinterception-i.md) | 是 | 设置Navigation跳转拦截对象。 |

## setPathStack

```TypeScript
setPathStack(pathStack: Array<NavPathInfo>, animated?: boolean): void
```

将当前路由栈中的路由页面信息数组更新为指定内容，并实现路由转场。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-setPathStack(pathStack: Array<NavPathInfo>, animated?: boolean): void--><!--Device-NavPathStack-setPathStack(pathStack: Array<NavPathInfo>, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathStack | Array&lt;[NavPathInfo](arkts-na-navigation-navpathinfo-c.md)&gt; | 是 | 设置当前路由栈中的路由页面信息数组。&lt;br/&gt;**说明：**&lt;br/&gt;数组长度无限制。 |
| animated | boolean | 否 | 是否开启转场动画。&lt;br/&gt;true：开启转场动画；false：不开启转场动画。&lt;br /&gt; 默认值：true |

## size

```TypeScript
size(): int
```

获取栈大小。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NavPathStack-size(): int--><!--Device-NavPathStack-size(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回栈大小。&lt;br/&gt;取值范围：[0, +∞) |

