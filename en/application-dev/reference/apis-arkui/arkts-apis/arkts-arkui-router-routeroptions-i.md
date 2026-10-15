# RouterOptions

```TypeScript
interface RouterOptions
```

Describes the page routing options.

> **NOTE:** 
> 
> The page routing stack supports a maximum of 32 pages.

**Since:** 8

<!--Device-router-interface RouterOptions--><!--Device-router-interface RouterOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## params

```TypeScript
params?: Object
```

Data that needs to be passed to the target page during redirection. The received data becomes invalid when the page is switched to another page. After navigation to the target page, use **router.getParams()** to obtain the passed parameters. In addition, in the web-like paradigm, parameters can also be used directly on the page, for example, **this.keyValue** (where **keyValue** is the value of a key in the **params** parameter during navigation). If the target page already has this parameter, its value will be overwritten by the passed parameter value.

**NOTE:** 

The **params** parameter can only pass serializable parameters. It cannot pass methods or objects returned by system APIs (for example, the **PixelMap** object defined and returned by media APIs). Passing non-serializable parameters may cause parameter transfer failure or application running exceptions. You are advised to extract the basic-type attributes that need to be passed from the objects returned by system APIs, and construct an object- type object for passing.

**Type:** Object

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RouterOptions-params?: Object--><!--Device-RouterOptions-params?: Object-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## recoverable

```TypeScript
recoverable?: boolean
```

Whether the corresponding page is recoverable.

Default value: **true**.

**true**: The corresponding page is recoverable.

**false**: The corresponding page is not recoverable.

**NOTE:** 

If an application is switched to the background and is later closed by the system due to resource constraints or other reasons, a page marked as recoverable can be restored by the system when the application is brought back to the foreground. For more details, see [UIAbility Backup and Restore](../../../application-models/ability-recover-guideline.md).

**Type:** boolean

**Since:** 14

<!--Device-RouterOptions-recoverable?: boolean--><!--Device-RouterOptions-recoverable?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## url

```TypeScript
url: string
```

URL of the target page, which can be in either of the following formats:

- Absolute page path, provided by the **pages** list in the configuration file, for example:

  - pages/index/index

  - pages/detail/detail

- Special value. If the value of **url** is **"/"**, the home page is redirected to. The home page defaults to the first data item in the **src** array of the page navigation configuration.

If a nonexistent or invalid URL path is passed in, the navigation fails. For details about the error codes, see the error code description of each API.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RouterOptions-url: string--><!--Device-RouterOptions-url: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite
