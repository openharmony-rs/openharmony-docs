# NavPushPathHelper

On the initial launch, the atomic service only downloads and installs the main package and its dependencies. Therefore, if the NavDestination resides in a different HSP subpackage that is not a dependency of the main package, you'll need to use **NavPushPathHelper** to download and install the corresponding HSP subpackage first. After that, push the specified **NavDestination** page information onto the stack. This way, you enable Navigation to support dynamic loading of the HSP subpackage before the navigation occurs.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { NavPushPathHelper } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(navPathStack: NavPathStack)
```

A constructor used to create a **NavPushPathHelper** object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| navPathStack | [NavPathStack](../arkts-components/arkts-arkui-navpathstack-c.md) | Yes | Navigation stack. |

## pushDestination

```TypeScript
pushDestination(moduleName: string, info: NavPathInfo, animated?: boolean): Promise<void>
```

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the NavDestination page specified by the **info** parameter onto the navigation stack. This API uses a promise to handle asynchronous operations.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name of the package where the NavDestination page is located. |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | Yes | Information about the NavDestination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |
| [100005](../errorcode-router.md#100005-builder-function-not-registered-during-navigation) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navdestination-not-found) | NavDestination not found. |
| [300001](../errorcode-router.md#300001-silent-installation-of-the-hsp-failed-before-navigation) | hsp silent install fail. |

## pushDestination

```TypeScript
pushDestination(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the NavDestination page specified by the **info** parameter onto the navigation stack. This API uses a promise to handle asynchronous operations.

Depending on the LaunchMode specified in the **options** parameter, different behaviors will be triggered.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name of the package where the NavDestination page is located. |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | Yes | Information about the NavDestination page. |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigationoptions-i.md) | No | Navigation options. The default value is **{ launchMode: LaunchMode.STANDARD, animated: true }**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |
| [100005](../errorcode-router.md#100005-builder-function-not-registered-during-navigation) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navdestination-not-found) | NavDestination not found. |
| [300001](../errorcode-router.md#300001-silent-installation-of-the-hsp-failed-before-navigation) | hsp silent install fail. |

## pushDestinationByName

```TypeScript
pushDestinationByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise<void>
```

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the NavDestination page specified by the **name** parameter onto the navigation stack, along with the data specified by **param**. This API uses a promise to handle asynchronous operations.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name of the package where the NavDestination page is located. |
| name | string | Yes | Name of the NavDestination page. |
| param | Object | Yes | Settings of the NavDestination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |
| [100005](../errorcode-router.md#100005-builder-function-not-registered-during-navigation) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navdestination-not-found) | NavDestination not found. |
| [300001](../errorcode-router.md#300001-silent-installation-of-the-hsp-failed-before-navigation) | hsp silent install fail. |

## pushDestinationByName

```TypeScript
pushDestinationByName(moduleName: string, name: string, param: Object,
    onPop: Callback<PopInfo>, animated?: boolean): Promise<void>
```

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the NavDestination page specified by the **name** parameter onto the navigation stack, along with the data specified by **param**. The **onPop** callback handles the return results when the page is popped from the stack. This API uses a promise to handle asynchronous operations.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name of the package where the NavDestination page is located. |
| name | string | Yes | Name of the NavDestination page. |
| param | Object | Yes | Settings of the NavDestination page. |
| onPop | Callback&lt;[PopInfo](../arkts-components/arkts-arkui-popinfo-i.md)&gt; | Yes | Callback used to handle the result returned when the page is popped out of the stack. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal error. |
| [100005](../errorcode-router.md#100005-builder-function-not-registered-during-navigation) | Builder function not registered. |
| [100006](../errorcode-router.md#100006-navdestination-not-found) | NavDestination not found. |
| [300001](../errorcode-router.md#300001-silent-installation-of-the-hsp-failed-before-navigation) | hsp silent install fail. |

## pushPath

```TypeScript
pushPath(moduleName: string, info: NavPathInfo, animated?: boolean): Promise<void>
```

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the NavDestination page specified by the **info** parameter onto the navigation stack. This API uses a promise to handle asynchronous operations.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name of the package where the NavDestination page is located. |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | Yes | Information about the NavDestination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [300001](../errorcode-router.md#300001-silent-installation-of-the-hsp-failed-before-navigation) | hsp silent install fail. |

## pushPath

```TypeScript
pushPath(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the NavDestination page specified by the **info** parameter onto the navigation stack. This API uses a promise to handle asynchronous operations.

Depending on the LaunchMode specified in the **options** parameter, different behaviors will be triggered.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name of the package where the NavDestination page is located. |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | Yes | Information about the NavDestination page. |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigationoptions-i.md) | No | Navigation options. The default value is **{ launchMode: LaunchMode.STANDARD, animated: true }**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [300001](../errorcode-router.md#300001-silent-installation-of-the-hsp-failed-before-navigation) | hsp silent install fail. |

## pushPathByName

```TypeScript
pushPathByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise<void>
```

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the NavDestination page specified by the **name** parameter onto the navigation stack, along with the data specified by **param**. This API uses a promise to handle asynchronous operations.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name of the package where the NavDestination page is located. |
| name | string | Yes | Name of the NavDestination page. |
| param | Object | Yes | Settings of the NavDestination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [300001](../errorcode-router.md#300001-silent-installation-of-the-hsp-failed-before-navigation) | hsp silent install fail. |

## pushPathByName

```TypeScript
pushPathByName(moduleName: string, name: string, param: Object,
    onPop: Callback<PopInfo>, animated?: boolean): Promise<void>
```

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pushes the NavDestination page specified by the **name** parameter onto the navigation stack, along with the data specified by **param**. The **onPop** callback handles the return results when the page is popped from the stack. This API uses a promise to handle asynchronous operations.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name of the package where the NavDestination page is located. |
| name | string | Yes | Name of the NavDestination page. |
| param | Object | Yes | Settings of the NavDestination page. |
| onPop | Callback&lt;[PopInfo](../arkts-components/arkts-arkui-popinfo-i.md)&gt; | Yes | Callback used to receive the result. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [300001](../errorcode-router.md#300001-silent-installation-of-the-hsp-failed-before-navigation) | hsp silent install fail. |

## replacePath

```TypeScript
replacePath(moduleName: string, info: NavPathInfo, animated?: boolean): Promise<void>
```

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pops the top page from the current navigation stack and pushes the NavDestination page specified by the **info** parameter onto the stack. This API uses a promise to handle asynchronous operations.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name of the package where the NavDestination page is located. |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | Yes | Parameters of the page to replace the top of the navigation stack. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [300001](../errorcode-router.md#300001-silent-installation-of-the-hsp-failed-before-navigation) | hsp silent install fail. |

## replacePath

```TypeScript
replacePath(moduleName: string, info: NavPathInfo, options?: NavigationOptions): Promise<void>
```

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pops the top page from the current navigation stack. This API uses a promise to handle asynchronous operations.

Depending on the LaunchMode specified in the **options** parameter, different behaviors will be triggered.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name of the package where the NavDestination page is located. |
| info | [NavPathInfo](../arkts-components/arkts-arkui-navpathinfo-c.md) | Yes | Parameters of the page to replace the top of the navigation stack. |
| options | [NavigationOptions](../arkts-components/arkts-arkui-navigationoptions-i.md) | No | Navigation options. The default value is **{ launchMode: LaunchMode.STANDARD, animated: true }**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [300001](../errorcode-router.md#300001-silent-installation-of-the-hsp-failed-before-navigation) | hsp silent install fail. |

## replacePathByName

```TypeScript
replacePathByName(moduleName: string, name: string, param: Object, animated?: boolean): Promise<void>
```

Checks for the target subpackage and, if it is not present, initiates a download using the specified module name. Once the subpackage is downloaded, the API pops the top page from the current navigation stack and pushes the page specified by the **name** parameter onto the stack. This API uses a promise to handle asynchronous operations.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name of the package where the NavDestination page is located. |
| name | string | Yes | Name of the NavDestination page. |
| param | Object | Yes | Settings of the NavDestination page. |
| animated | boolean | No | Whether to support the transition animation.<br>Default value: **true**. <br>**true**: The transition animation is supported. <br>**false**: The transition animation is not supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [300001](../errorcode-router.md#300001-silent-installation-of-the-hsp-failed-before-navigation) | hsp silent install fail. |
