# isChangePermitted

## Modules to Import

```TypeScript
import { wallpaper } from '@kit.BasicServicesKit';
```

## isChangePermitted

```TypeScript
function isChangePermitted(callback: AsyncCallback<boolean>): void
```

Checks whether to allow the application to change the wallpaper for the current user. Returns true if the application is allowed to set a wallpaper for the current user. returns false otherwise.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.MiscServices.Wallpaper

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | the callback of isChangePermitted. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.isChangePermitted((error: BusinessError, data: Boolean) => {
    if (error) {
        console.error(`failed to isChangePermitted because: ${JSON.stringify(error)}`);
        return;
    }
    console.info(`success to isChangePermitted: ${JSON.stringify(data)}`);
});
```


<a id="ischangepermitted-1"></a>

## isChangePermitted

```TypeScript
function isChangePermitted(): Promise<boolean>
```

Checks whether to allow the application to change the wallpaper for the current user. Returns true if the application is allowed to set a wallpaper for the current user. returns false otherwise.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.MiscServices.Wallpaper

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | the promise returned by the function. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

wallpaper.isChangePermitted().then((data: Boolean) => {
    console.info(`success to isChangePermitted: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
    console.error(`failed to isChangePermitted because: ${JSON.stringify(error)}`);
});
```
