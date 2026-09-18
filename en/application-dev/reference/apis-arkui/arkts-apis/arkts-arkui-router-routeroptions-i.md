# RouterOptions

Describes the page routing options.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## params

```TypeScript
params?: Object
```

Data that needs to be passed to the target page during redirection. The received data becomes invalid when the page is switched to another page. The target page can use **router.getParams()** to obtain the passed parameters, for example, **this.keyValue** (**keyValue** is the value of a key in **params**). In the web-like paradigm, these parameters can be directly used on the target page. If the field specified by **key** already exists on the target page, the passed value of the key will be displayed.

**NOTE:** 

The **params** parameter can only carry serializable data. Objects returned by methods and system APIs (for example, **PixelMap** objects defined and returned by media APIs) cannot be passed. To pass such objects, extract from them the basic type attributes to be passed, and then construct objects of the object type.

**Type:** Object

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## url

```TypeScript
url: string
```

URL of the target page, in either of the following formats:

- Absolute path of the page. The value is available in the pages list in the **config.json** file, for example:  
- pages/index/index  
- pages/detail/detail  
- special value. If the value of **url** is **"/"**, the application navigates to the home page. By default, the  
home page is set to the first item in the **src** value array.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite
