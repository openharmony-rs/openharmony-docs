# NavPathStack

Navigation导航控制器，以栈的数据结构管理Navigation中所有的子页面，并提供栈操作的方法用于控制Navigation中子页面的切换。

从API version 12开始，NavPathStack允许被继承，派生类对象可以替代基类NavPathStack对象使用。使用示例参见[示例10](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#示例10定义导航控制器派生类)。

> **说明：**  
>  
> 1.连续调用多个导航控制器操作方法时，中间过程会被忽略，显示最终的栈操作结果。

> 例如：在Page1页面先pop再push一个Page1，系统会认为操作前和操作后的结果一致而不进行任何操作，如果需要强行push一个Page1实例，可以设置  
> [NavigationOption](arkts-arkui-navigationoptions-i.md)中的launchMode属性值为LaunchMode.NEW_INSTANCE模式。  
>  
> 2.不建议开发者通过监听页面生命周期的方式管理自己的导航控制器。  
>  
> 3.在应用处于后台状态下，调用NavPathStack的栈操作方法，会在应用再次回到前台状态时触发刷新。

**起始版本：** 10

<!--Device-unnamed-declare class NavPathStack--><!--Device-unnamed-declare class NavPathStack-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="clear"></a>
## clear

```TypeScript
clear(animated?: boolean): void
```

清除栈中所有页面。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-clear(animated?: boolean): void--><!--Device-NavPathStack-clear(animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true<br>**起始版本：** 11 |

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

创建NavPathStack对象。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-constructor()--><!--Device-NavPathStack-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="disableanimation"></a>
## disableAnimation

```TypeScript
disableAnimation(value: boolean): void
```

关闭（true）或打开（false）当前Navigation中所有转场动画。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-disableAnimation(value: boolean): void--><!--Device-NavPathStack-disableAnimation(value: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否关闭转场动画，<br/>默认值：false<br/>true：关闭转场动画。<br/>false：不关闭转场动画。 |

<a id="getallpathname"></a>
## getAllPathName

```TypeScript
getAllPathName(): Array<string>
```

获取栈中所有NavDestination页面的名称。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-getAllPathName(): Array<string>--><!--Device-NavPathStack-getAllPathName(): Array<string>-End-->

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

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-getIndexByName(name: string): Array<number>--><!--Device-NavPathStack-getIndexByName(name: string): Array<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 返回全部名为name的NavDestination页面的位置索引。 当路由栈中不存在此name，返回空数组。索引取值范围为[0, 路由栈大小-1] |

<a id="getparambyindex"></a>
## getParamByIndex

```TypeScript
getParamByIndex(index: number): unknown | undefined
```

获取index指定的NavDestination页面的参数信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-getParamByIndex(index: number): unknown | undefined--><!--Device-NavPathStack-getParamByIndex(index: number): unknown | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestination页面的位置索引。 索引值从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| unknown | **unknown**: parameter information of the corresponding navigation destination page. **unknown** can represent a user-defined type.<br>**undefined**: an invalid index is provided. |

<a id="getparambyname"></a>
## getParamByName

```TypeScript
getParamByName(name: string): Array<unknown>
```

获取所有名为name的NavDestination页面的参数信息，按页面索引从小到大排序。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-getParamByName(name: string): Array<unknown>--><!--Device-NavPathStack-getParamByName(name: string): Array<unknown>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;unknown&gt; | 返回全部名为name的NavDestination页面的参数信息，unknown可以是用户自定义的类型。 |

<a id="getparent"></a>
## getParent

```TypeScript
getParent(): NavPathStack | null
```

获取父NavPathStack。

当出现Navigation嵌套Navigation的情况时（可以是直接嵌套，也可以是间接嵌套），内部Navigation的NavPathStack能够获取到外层Navigation的NavPathStack。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-getParent(): NavPathStack | null--><!--Device-NavPathStack-getParent(): NavPathStack | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavPathStack](arkts-arkui-navpathstack-c.md) | Navigation path stack of the outer **Navigation** component in which the current **Navigation** component is nested. If there is no outer **Navigation** component., **null** is returned. |

<a id="getpathstack"></a>
## getPathStack

```TypeScript
getPathStack(): Array<NavPathInfo>
```

获取当前路由栈中的路由页面信息数组。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-getPathStack(): Array<NavPathInfo>--><!--Device-NavPathStack-getPathStack(): Array<NavPathInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;NavPathInfo&gt; | 当前路由栈中的路由页面信息数组。 |

<a id="moveindextotop"></a>
## moveIndexToTop

```TypeScript
moveIndexToTop(index: number, animated?: boolean): void
```

将index指定的NavDestination页面移到栈顶。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-moveIndexToTop(index: number, animated?: boolean): void--><!--Device-NavPathStack-moveIndexToTop(index: number, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestination页面的位置索引。索引值从0开始。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true<br>**起始版本：** 11 |

<a id="movetotop"></a>
## moveToTop

```TypeScript
moveToTop(name: string, animated?: boolean): number
```

将由栈底开始第一个名为name的NavDestination页面移到栈顶。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-moveToTop(name: string, animated?: boolean): number--><!--Device-NavPathStack-moveToTop(name: string, animated?: boolean): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 如果栈中存在名为name的NavDestination页面，则返回由栈底开始第一个名为name的NavDestination页面的当前索引，否则返回-1。 |

<a id="pop"></a>
## pop

```TypeScript
pop(animated?: boolean): NavPathInfo | undefined
```

弹出路由栈栈顶元素。

> **说明：**  
>  
> 连续调用多个导航控制器方法时，中间被pop的页面会被缓存，后续push同名页面时会优先复用该页面，不会走新的页面创建流程。

> 例如：

> pathStack: NavPathStack = new NavPathStack()

> // 初始页面栈为：[A]

> pathStack.pop()

> pathStack.pushPath(A)

> pathStack.pushPath(B)

> // 操作后页面栈为：[A B]

> 此时A页面会被复用，不会走新的创建流程。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-pop(animated?: boolean): NavPathInfo | undefined--><!--Device-NavPathStack-pop(animated?: boolean): NavPathInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavPathInfo](arkts-arkui-navpathinfo-c.md) | **NavPathInfo**: information about the navigation destination page at the top of the stack.<br>**undefined**: the routing stack is empty. |

<a id="pop-1"></a>
## pop

```TypeScript
pop(result: Object, animated?: boolean): NavPathInfo | undefined
```

弹出路由栈栈顶元素，并触发onPop回调传入页面处理结果。

> **说明：**  
>  
> 连续调用多个导航控制器方法时，中间被pop的页面会被缓存，后续push同名页面时会优先复用该页面，不会走新的页面创建流程。

> 例如：

> pathStack: NavPathStack = new NavPathStack()

> // 初始页面栈为：[A]

> pathStack.pop()

> pathStack.pushPath(A)

> pathStack.pushPath(B)

> // 操作后页面栈为：[A B]

> 此时A页面会被复用，不会走新的创建流程。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-pop(result: Object, animated?: boolean): NavPathInfo | undefined--><!--Device-NavPathStack-pop(result: Object, animated?: boolean): NavPathInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | Object | 是 | 页面自定义处理结果。不支持boolean类型。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NavPathInfo](arkts-arkui-navpathinfo-c.md) | **NavPathInfo**: information about the navigation destination page at the top of the stack.<br>**undefined**: the routing stack is empty. |

<a id="poptoindex"></a>
## popToIndex

```TypeScript
popToIndex(index: number, animated?: boolean): void
```

回退路由栈到index指定的NavDestination页面。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-popToIndex(index: number, animated?: boolean): void--><!--Device-NavPathStack-popToIndex(index: number, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestination页面的位置索引。索引值从0开始。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true<br>**起始版本：** 11 |

<a id="poptoindex-1"></a>
## popToIndex

```TypeScript
popToIndex(index: number, result: Object, animated?: boolean): void
```

回退路由栈到index指定的NavDestination页面，并触发onPop回调传入页面处理结果。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-popToIndex(index: number, result: Object, animated?: boolean): void--><!--Device-NavPathStack-popToIndex(index: number, result: Object, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | NavDestination页面的位置索引。索引值从0开始。 |
| result | Object | 是 | 页面自定义处理结果。不支持boolean类型。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true |

<a id="poptoname"></a>
## popToName

```TypeScript
popToName(name: string, animated?: boolean): number
```

回退路由栈到由栈底开始第一个名为name的NavDestination页面。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-popToName(name: string, animated?: boolean): number--><!--Device-NavPathStack-popToName(name: string, animated?: boolean): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 如果栈中存在名为name的NavDestination页面，则返回由栈底开始第一个名为name的NavDestination页面的索引，否则返回-1。 |

<a id="poptoname-1"></a>
## popToName

```TypeScript
popToName(name: string, result: Object, animated?: boolean): number
```

回退路由栈到由栈底开始第一个名为name的NavDestination页面，并触发onPop回调传入页面处理结果。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-popToName(name: string, result: Object, animated?: boolean): number--><!--Device-NavPathStack-popToName(name: string, result: Object, animated?: boolean): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| result | Object | 是 | 页面自定义处理结果。不支持boolean类型。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 如果栈中存在名为name的NavDestination页面，则返回由栈底开始第一个名为name的NavDestination页面的索引，否则返回-1。 |

<a id="pushdestination"></a>
## pushDestination

```TypeScript
pushDestination(info: NavPathInfo, animated?: boolean): Promise<void>
```

将info指定的NavDestination页面信息入栈，使用Promise异步回调返回接口调用结果。

> **说明：**  
>  
> 不建议在[aboutToAppear](arkts-arkui-basecustomcomponent-c.md#abouttoappear-1)中使用栈操作，此时的页面还未构建完成，会导致白屏或跳转失败等问题。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-pushDestination(info: NavPathInfo, animated?: boolean): Promise<void>--><!--Device-NavPathStack-pushDestination(info: NavPathInfo, animated?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameters types.3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100005](../errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |

<a id="pushdestination-1"></a>
## pushDestination

```TypeScript
pushDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

将info指定的NavDestination页面信息入栈，使用Promise异步回调返回接口调用结果，具体根据options中指定不同的[LaunchMode](arkts-arkui-launchmode-e.md)，来实现不同的行为。

> **说明：**  
>  
> 不建议在[aboutToAppear](arkts-arkui-basecustomcomponent-c.md#abouttoappear-1)中使用栈操作，此时的页面还未构建完成，会导致白屏或跳转失败等问题。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-pushDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>--><!--Device-NavPathStack-pushDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| options | [NavigationOptions](arkts-arkui-navigationoptions-i.md) | 否 | 路由栈操作选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异常返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameters types.3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100005](../errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |

<a id="pushdestinationbyname"></a>
## pushDestinationByName

```TypeScript
pushDestinationByName(name: string, param: Object, animated?: boolean): Promise<void>
```

将name指定的NavDestination页面信息入栈，传递的数据为param，使用Promise异步回调返回接口调用结果。

> **说明：**  
>  
> 不建议在[aboutToAppear](arkts-arkui-basecustomcomponent-c.md#abouttoappear-1)中使用栈操作，此时的页面还未构建完成，会导致白屏或跳转失败等问题。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-pushDestinationByName(name: string, param: Object, animated?: boolean): Promise<void>--><!--Device-NavPathStack-pushDestinationByName(name: string, param: Object, animated?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | 开发者设置的NavDestination页面详细参数。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异常返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameters types.3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100005](../errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |

<a id="pushdestinationbyname-1"></a>
## pushDestinationByName

```TypeScript
pushDestinationByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback<PopInfo>, animated?: boolean): Promise<void>
```

将name指定的NavDestination页面信息入栈，传递的数据为param，并且添加用于页面出栈时处理返回结果的onPop回调，使用Promise异步回调返回接口调用结果。

> **说明：**  
>  
> 不建议在[aboutToAppear](arkts-arkui-basecustomcomponent-c.md#abouttoappear-1)中使用栈操作，此时的页面还未构建完成，会导致白屏或跳转失败等问题。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-pushDestinationByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback<PopInfo>, animated?: boolean): Promise<void>--><!--Device-NavPathStack-pushDestinationByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback<PopInfo>, animated?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | 开发者设置的NavDestination页面详细参数。 |
| onPop | import('../api/@ohos.base').Callback&lt;PopInfo&gt; | 是 | Callback回调，用于页面出栈时处理返回结果。仅[pop](arkts-arkui-navpathstack-c.md#pop-1)、[popToName](arkts-arkui-navpathstack-c.md#poptoname-1)、[popToIndex](arkts-arkui-navpathstack-c.md#poptoindex-1)中设置result参数后触发。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异常返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameters types.3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100005](../errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |

<a id="pushpath"></a>
## pushPath

```TypeScript
pushPath(info: NavPathInfo, animated?: boolean): void
```

将info指定的NavDestination页面信息入栈。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-pushPath(info: NavPathInfo, animated?: boolean): void--><!--Device-NavPathStack-pushPath(info: NavPathInfo, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>传入参数非法时，按true处理。<br>**起始版本：** 11 |

<a id="pushpath-1"></a>
## pushPath

```TypeScript
pushPath(info: NavPathInfo, options?: NavigationOptions): void
```

将info指定的NavDestination页面信息入栈，具体根据options中指定不同的[LaunchMode](arkts-arkui-launchmode-e.md)，来实现不同的行为。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-pushPath(info: NavPathInfo, options?: NavigationOptions): void--><!--Device-NavPathStack-pushPath(info: NavPathInfo, options?: NavigationOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| options | [NavigationOptions](arkts-arkui-navigationoptions-i.md) | 否 | 路由栈操作选项。 |

<a id="pushpathbyname"></a>
## pushPathByName

```TypeScript
pushPathByName(name: string, param: unknown, animated?: boolean): void
```

将name指定的NavDestination页面信息入栈，传递的数据为param。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-pushPathByName(name: string, param: unknown, animated?: boolean): void--><!--Device-NavPathStack-pushPathByName(name: string, param: unknown, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | unknown | 是 | 开发者设置的NavDestination页面详细参数，unknown可以是用户自定义的类型。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true<br>**起始版本：** 11 |

<a id="pushpathbyname-1"></a>
## pushPathByName

```TypeScript
pushPathByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback<PopInfo>, animated?: boolean): void
```

将name指定的NavDestination页面信息入栈，传递的数据为param，添加onPop回调接收入栈页面出栈时的返回结果，并进行处理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-pushPathByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback<PopInfo>, animated?: boolean): void--><!--Device-NavPathStack-pushPathByName(name: string, param: Object, onPop: import('../api/@ohos.base').Callback<PopInfo>, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | 开发者设置的NavDestination页面详细参数。 |
| onPop | import('../api/@ohos.base').Callback&lt;PopInfo&gt; | 是 | Callback回调，用于页面出栈时触发该回调处理返回结果。仅[pop](arkts-arkui-navpathstack-c.md#pop-1)、[popToName](arkts-arkui-navpathstack-c.md#poptoname-1)、[popToIndex](arkts-arkui-navpathstack-c.md#poptoindex-1)中设置result参数后触发。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true |

<a id="removebyindexes"></a>
## removeByIndexes

```TypeScript
removeByIndexes(indexes: Array<number>): number
```

将路由栈内索引值在indexes中的NavDestination页面删除。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-removeByIndexes(indexes: Array<number>): number--><!--Device-NavPathStack-removeByIndexes(indexes: Array<number>): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indexes | Array&lt;number&gt; | 是 | 待删除NavDestination页面的索引值数组。索引值从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回删除的NavDestination页面数量。 |

<a id="removebyname"></a>
## removeByName

```TypeScript
removeByName(name: string): number
```

将路由栈内指定name的NavDestination页面删除。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-removeByName(name: string): number--><!--Device-NavPathStack-removeByName(name: string): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 删除的NavDestination页面的名字。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回删除的NavDestination页面数量。 |

<a id="removebynavdestinationid"></a>
## removeByNavDestinationId

```TypeScript
removeByNavDestinationId(navDestinationId: string): boolean
```

将路由栈内指定navDestinationId的NavDestination页面删除。navDestinationId可以在NavDestination的[onReady](NavDestinationAttribute#onReady)回调中获取，也可以在[NavDestinationInfo](../arkts-apis/arkts-arkui-uiobserver-navdestinationinfo-i.md)中获取。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-removeByNavDestinationId(navDestinationId: string): boolean--><!--Device-NavPathStack-removeByNavDestinationId(navDestinationId: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navDestinationId | string | 是 | 删除的NavDestination页面的唯一标识符navDestinationId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否成功删除该页面，<br/>true：删除成功。<br/>false：删除失败。 |

<a id="replacedestination"></a>
## replaceDestination

```TypeScript
replaceDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

替换路由栈操作。使用Promise异步回调返回接口调用结果，具体根据options中指定不同的[LaunchMode](arkts-arkui-launchmode-e.md)，来实现不同的行为。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-replaceDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>--><!--Device-NavPathStack-replaceDestination(info: NavPathInfo, options?: NavigationOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| options | [NavigationOptions](arkts-arkui-navigationoptions-i.md) | 否 | 路由栈操作选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 异常返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified.2. Incorrect parameters types.3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100005](../errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |

<a id="replacepath"></a>
## replacePath

```TypeScript
replacePath(info: NavPathInfo, animated?: boolean): void
```

将当前路由栈栈顶退出，将info指定的NavDestination页面信息入栈。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-replacePath(info: NavPathInfo, animated?: boolean): void--><!--Device-NavPathStack-replacePath(info: NavPathInfo, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navpathinfo-c.md) | 是 | 新栈顶页面参数信息。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true |

<a id="replacepath-1"></a>
## replacePath

```TypeScript
replacePath(info: NavPathInfo, options?: NavigationOptions): void
```

替换路由栈操作，具体根据options中指定不同的[LaunchMode](arkts-arkui-launchmode-e.md)，来实现不同的行为。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-replacePath(info: NavPathInfo, options?: NavigationOptions): void--><!--Device-NavPathStack-replacePath(info: NavPathInfo, options?: NavigationOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NavPathInfo](arkts-arkui-navpathinfo-c.md) | 是 | 新栈顶页面参数信息。 |
| options | [NavigationOptions](arkts-arkui-navigationoptions-i.md) | 否 | 路由栈操作选项。 |

<a id="replacepathbyname"></a>
## replacePathByName

```TypeScript
replacePathByName(name: string, param: Object, animated?: boolean): void
```

将当前路由栈栈顶退出，将name指定的页面入栈。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-replacePathByName(name: string, param: Object, animated?: boolean): void--><!--Device-NavPathStack-replacePathByName(name: string, param: Object, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | 开发者设置的NavDestination页面详细参数。 |
| animated | boolean | 否 | 是否支持转场动画。<br/>true：支持转场动画；false：不支持转场动画。<br/>默认值：true |

<a id="setinterception"></a>
## setInterception

```TypeScript
setInterception(interception: NavigationInterception): void
```

设置Navigation页面跳转拦截回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-setInterception(interception: NavigationInterception): void--><!--Device-NavPathStack-setInterception(interception: NavigationInterception): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| interception | [NavigationInterception](arkts-arkui-navigationinterception-i.md) | 是 | 设置Navigation跳转拦截对象。 |

<a id="setpathstack"></a>
## setPathStack

```TypeScript
setPathStack(pathStack: Array<NavPathInfo>, animated?: boolean): void
```

将当前路由栈中的路由页面信息数组更新为指定内容，并实现路由转场。

> **说明：**  
>  
> 1. 开发者可以在原有栈的基础上批量添加或删除页面。批量入栈的页面中，只有可见的页面会触发创建，其他页面虽已入栈但不会立即创建，当这些页面变为可见时，才会触发创建。  
>  
> 2. 通过批量入栈功能更新的路由栈，各页面的生命周期事件触发顺序为从栈顶到底部依次触发，这与其它入栈接口从栈底到顶部的触发顺序不同。  
>  
> 3. 开发者可以通过[NavPathInfo](arkts-arkui-navpathinfo-c.md)中的页面唯一标识符navDestinationId来操作已有页面，该id由系统默认生成且全局唯一（可以通过  
> [getPathStack](arkts-arkui-navpathstack-c.md#getpathstack-1)接口获取，不可主动赋新值）。若该id在当前路由栈中不存在，则表示新增页面，若在当前路由栈中存在，同时对应的name相同，则表示复用已  
> 有页面。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-setPathStack(pathStack: Array<NavPathInfo>, animated?: boolean): void--><!--Device-NavPathStack-setPathStack(pathStack: Array<NavPathInfo>, animated?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathStack | Array&lt;NavPathInfo&gt; | 是 | 设置当前路由栈中的路由页面信息数组。<br/>**说明：**<br/>数组长度无限制。 |
| animated | boolean | 否 | 是否开启转场动画。<br/>true：开启转场动画；false：不开启转场动画。<br /> 默认值：true |

<a id="size"></a>
## size

```TypeScript
size(): number
```

获取栈大小。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavPathStack-size(): number--><!--Device-NavPathStack-size(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Stack size.<br>Value range: [0, +∞) |

