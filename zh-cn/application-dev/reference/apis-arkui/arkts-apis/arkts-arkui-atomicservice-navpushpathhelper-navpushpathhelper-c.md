# NavPushPathHelper

当跳转的目标NavDestination在不同的hsp分包且未被主包依赖时，首次运行原子化服务只会下载安装主包。此时需要使用 NavPushPathHelper先下载安装相应hsp分包，再将指定的NavDestination页面信息入栈或替换当前栈顶页面，从 而使Navigation支持动态加载hsp分包后再跳转。

> **说明：**
> 
> 该组件从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { NavPushPathHelper } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(navPathStack: NavPathStack)
```

NavPushPathHelper的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navPathStack | [NavPathStack](../arkts-components/arkts-arkui-navpathstack-c.md) | 是 | Navigation路由栈。 |

## pushDestination

```TypeScript
pushDestination(moduleName: string, info: NavPathInfo, animated?: boolean): Promise<void>
```

先判断分包是否存在，若不存在，则通过moduleName下载分包，再将info指定的NavDestination页面信息入栈，使 用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 目标NavDestination所在分包的moduleName。 |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| animated | boolean | 否 | 是否支持转场动画。 默认值：true。 true：支持转场动画。 false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100005](../errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |
| [300001](../errorcode-router.md#300001-navigation跳转前静默安装hsp分包失败) | hsp silent install fail. |

## pushDestination

```TypeScript
pushDestination(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

先判断分包是否存在，若不存在，则通过moduleName下载分包，再将info指定的NavDestination页面信息入栈，使 用Promise异步回调。具体根据options中指定不同的LaunchMode，有不同的行为。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 目标NavDestination所在分包的moduleName。 |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigationoptions-i.md) | 否 | 页面栈操作选项。默认值为{ launchMode: LaunchMode.STANDARD, animated: true }。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100005](../errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |
| [300001](../errorcode-router.md#300001-navigation跳转前静默安装hsp分包失败) | hsp silent install fail. |

## pushDestinationByName

```TypeScript
pushDestinationByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise<void>
```

先判断分包是否存在，若不存在，则通过moduleName下载分包，再将name指定的NavDestination页面信息入栈，传 递的数据为param，使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 目标NavDestination所在分包的moduleName。 |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | NavDestination页面详细参数。 |
| animated | boolean | 否 | 是否支持转场动画。 默认值：true。 true：支持转场动画。 false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100005](../errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |
| [300001](../errorcode-router.md#300001-navigation跳转前静默安装hsp分包失败) | hsp silent install fail. |

## pushDestinationByName

```TypeScript
pushDestinationByName(moduleName: string, name: string, param: Object,
    onPop: Callback<PopInfo>, animated?: boolean): Promise<void>
```

先判断分包是否存在，若不存在，则通过moduleName下载分包，再将name指定的NavDestination页面信息入栈，传 递的数据为param，添加用于页面出栈时处理返回结果的onPop回调，使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 目标NavDestination所在分包的moduleName。 |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | NavDestination页面的参数对象，用于向目标页面传递数据。 |
| onPop | Callback&lt;[PopInfo](../arkts-components/arkts-arkui-popinfo-i.md)&gt; | 是 | Callback回调，用于页面出栈时处理返回结果。 |
| animated | boolean | 否 | 是否支持转场动画。 默认值：true。 true：支持转场动画。 false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [100005](../errorcode-router.md#100005-navigation跳转时未注册builder函数) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navigation跳转时目标页面不存在navdestination组件) | NavDestination not found. |
| [300001](../errorcode-router.md#300001-navigation跳转前静默安装hsp分包失败) | hsp silent install fail. |

## pushPath

```TypeScript
pushPath(moduleName: string, info: NavPathInfo, animated?: boolean): Promise<void>
```

先判断分包是否存在，若不存在，则通过moduleName下载分包，再将info指定的NavDestination页面信息入栈，使 用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 目标NavDestination所在分包的moduleName。 |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| animated | boolean | 否 | 是否支持转场动画。 默认值：true。 true：支持转场动画。 false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [300001](../errorcode-router.md#300001-navigation跳转前静默安装hsp分包失败) | hsp silent install fail. |

## pushPath

```TypeScript
pushPath(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

先判断分包是否存在，若不存在，则通过moduleName下载分包，再将info指定的NavDestination页面信息入栈，使 用Promise异步回调。具体根据options中指定的LaunchMode不同，执行不同的跳转行为。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 目标NavDestination所在分包的moduleName。 |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | NavDestination页面的信息。 |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigationoptions-i.md) | 否 | 页面栈操作选项。默认值为{ launchMode: LaunchMode.STANDARD, animated: true }。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [300001](../errorcode-router.md#300001-navigation跳转前静默安装hsp分包失败) | hsp silent install fail. |

## pushPathByName

```TypeScript
pushPathByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise<void>
```

先判断分包是否存在，若不存在，则通过moduleName下载分包，再将name指定的NavDestination页面信息入栈，传 递的数据为param，使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 目标NavDestination所在分包的moduleName。 |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | NavDestination页面详细参数。 |
| animated | boolean | 否 | 是否支持转场动画。 默认值：true。 true：支持转场动画。 false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [300001](../errorcode-router.md#300001-navigation跳转前静默安装hsp分包失败) | hsp silent install fail. |

## pushPathByName

```TypeScript
pushPathByName(moduleName: string, name: string, param: Object,
    onPop: Callback<PopInfo>, animated?: boolean): Promise<void>
```

先判断分包是否存在，若不存在，则通过moduleName下载分包，再将name指定的NavDestination页面信息入栈，传 递的数据为param，添加onPop回调接收入栈页面出栈时的返回结果，并进行处理，使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 目标NavDestination所在分包的moduleName。 |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | NavDestination页面详细参数。 |
| onPop | Callback&lt;[PopInfo](../arkts-components/arkts-arkui-popinfo-i.md)&gt; | 是 | Callback回调，用于页面出栈时处理返回结果。 |
| animated | boolean | 否 | 是否支持转场动画。 默认值：true。 true：支持转场动画。 false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [300001](../errorcode-router.md#300001-navigation跳转前静默安装hsp分包失败) | hsp silent install fail. |

## replacePath

```TypeScript
replacePath(moduleName: string, info: NavPathInfo, animated?: boolean): Promise<void>
```

先判断分包是否存在，若不存在，则通过moduleName下载分包，再将当前页面栈栈顶退出，将info指定的 NavDestination页面信息入栈，使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 目标NavDestination所在分包的moduleName。 |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | 新栈顶页面参数信息。 |
| animated | boolean | 否 | 是否支持转场动画。 默认值：true。 true：支持转场动画。 false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [300001](../errorcode-router.md#300001-navigation跳转前静默安装hsp分包失败) | hsp silent install fail. |

## replacePath

```TypeScript
replacePath(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

先判断分包是否存在，若不存在，则通过moduleName下载分包，再将当前页面栈栈顶退出，将info指定的 NavDestination页面信息入栈，使用Promise异步回调。具体根据options中指定不同的LaunchMode，有不同的行为。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 目标NavDestination所在分包的moduleName。 |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | 是 | 新栈顶页面参数信息。 |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigationoptions-i.md) | 否 | 页面栈操作选项。默认值为{ launchMode: LaunchMode.STANDARD, animated: true }。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [300001](../errorcode-router.md#300001-navigation跳转前静默安装hsp分包失败) | hsp silent install fail. |

## replacePathByName

```TypeScript
replacePathByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise<void>
```

先判断分包是否存在，若不存在，则通过moduleName下载分包，再将当前页面栈栈顶退出，将name指定的 NavDestination页面信息入栈，传递的数据为param，使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 目标NavDestination所在分包的moduleName。 |
| name | string | 是 | NavDestination页面名称。 |
| param | Object | 是 | NavDestination页面详细参数。 |
| animated | boolean | 否 | 是否支持转场动画。 默认值：true。 true：支持转场动画。 false：不支持转场动画。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [300001](../errorcode-router.md#300001-navigation跳转前静默安装hsp分包失败) | hsp silent install fail. |
