# NamedRouterOptions

Describes the named route options.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## name

```TypeScript
name: string
```

Name of the target named route.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## params

```TypeScript
params?: Object
```

Data that needs to be passed to the target page during redirection. The target page can use **router.getParams()** to obtain the passed parameters, for example, **this.keyValue** (**keyValue** is the value of a key in **params**). In the web-like paradigm, these parameters can be directly used on the target page. If the field specified by **key** already exists on the target page, the passed value of the key will be displayed.

**NOTE:** 

The **params** parameter cannot pass objects returned by methods and system APIs, for example, **PixelMap** objects defined and returned by media APIs. To pass such objects, extract from them the basic type attributes to be passed, and then construct objects of the object type.

**Type:** Object

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Lite
