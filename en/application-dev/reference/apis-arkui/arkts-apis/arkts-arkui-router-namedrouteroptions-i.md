# NamedRouterOptions

```TypeScript
interface NamedRouterOptions
```

Describes the named route options.

**Since:** 10

<!--Device-router-interface NamedRouterOptions--><!--Device-router-interface NamedRouterOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## name

```TypeScript
name: string
```

Name of the target named route page, which must be a registered named route name.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NamedRouterOptions-name: string--><!--Device-NamedRouterOptions-name: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## params

```TypeScript
params?: Object
```

Data that needs to be passed to the target page during redirection. The received data becomes invalid when the page is switched to another page. After navigating to the target page, use **router.getParams()** to obtain the passed parameters. In addition, in the web-like paradigm, parameters can also be used directly on the page, for example, **this.keyValue** (where **keyValue** is the value of a key in the **params** parameter during navigation). If the target page already has this parameter, its value will be overwritten by the passed parameter value.

**NOTE:** 

The **params** parameter can only pass serializable parameters. It cannot pass methods or objects returned by system APIs (for example, the **PixelMap** object defined and returned by media APIs). Passing non-serializable parameters may cause parameter transfer failure or application running exceptions. You are advised to extract the basic-type attributes that need to be passed from objects returned by system APIs, and construct an object-type object for passing.

**Type:** Object

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NamedRouterOptions-params?: Object--><!--Device-NamedRouterOptions-params?: Object-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

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

<!--Device-NamedRouterOptions-recoverable?: boolean--><!--Device-NamedRouterOptions-recoverable?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite
