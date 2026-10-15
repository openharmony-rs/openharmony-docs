# back

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

<a id="back1"></a>

## back

```TypeScript
function back(options?: RouterOptions): void
```

Returns to the previous page or a specified page, and removes all pages between the current page and the specified page. If [showAlertBeforeBackPage](arkts-arkui-router-showalertbeforebackpage-f.md) has been called to enable the return confirm dialog box, a confirm dialog box will be displayed before the return operation is executed. The return is performed only after the user confirms; if the user cancels, the return is not performed.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 8

**Deprecated since:** 18

**Substitutes:** [back](arkts-arkui-arkui-uicontext-router-c.md#back1)(options?: router.RouterOptions)

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-router-function back(options?: RouterOptions): void--><!--Device-router-function back(options?: RouterOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-router-routeroptions-i.md) | No | Description of the target page, where **url** indicates the route address of the target page to return to. If the page with the specified URL does not exist in the page stack, the current back request will not be responded to. If **url** is not set, the previous page is returned, the page will not be rebuilt, and the page in the page stack will not be reclaimed, but will be reclaimed after being popped out of the stack. **back** indicates the back API, and setting **url** to the special value **"/"** does not take effect. If the page is navigated to using a named route, the **url** passed in must be the name of the named route. |

**Examples**

```TypeScript
this.getUIContext().getRouter().back({ url: 'pages/detail' });
```


<a id="back2"></a>

## back

```TypeScript
function back(index: number, params?: Object): void
```

Returns to a specified page, and removes all pages between the current page and the specified page. If [showAlertBeforeBackPage](arkts-arkui-router-showalertbeforebackpage-f.md) has been called to enable the return confirm dialog box, a confirm dialog box will be displayed before the return operation is executed. The return is performed only after the user confirms; if the user cancels, the return is not performed.

> **NOTE:** 
> 
> - Since API version 12, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 12

**Deprecated since:** 18

**Substitutes:** [back](arkts-arkui-arkui-uicontext-router-c.md#back2)(index: number, params?: Object)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-router-function back(index: number, params?: Object): void--><!--Device-router-function back(index: number, params?: Object): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the target page to return to. The value range is [1, Page stack size], and the maximum page stack size is 32. The index starts from 1 from the bottom to the top of the stack. No response is returned if the index does not exist or exceeds the valid range of the page stack. |
| params | Object | No | Parameters carried when returning to the page.<br>**NOTE:** <br>The **params** parameter can only pass serializable parameters. It cannot pass methods or objects returned by system APIs (for example, the **PixelMap** object defined and returned by media APIs). You are advised to extract the basic-type attributes that need to be passed from the objects returned by system APIs, and construct an object-type object for passing. |

**Examples**

```TypeScript
this.getUIContext().getRouter().back(1);
```

```TypeScript
this.getUIContext().getRouter().back(1, { info: 'From Home' }); // Returning with parameters.
```
