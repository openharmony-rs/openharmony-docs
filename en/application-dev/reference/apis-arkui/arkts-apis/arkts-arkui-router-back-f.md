# back

## Modules to Import

```TypeScript
import { router } from '@kit.ArkUI';
```

## back

```TypeScript
function back(options?: RouterOptions): void
```

Returns to the previous page or a specified page, which deletes all pages between the current page and the target page.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 8

**Deprecated since:** 18

**Substitutes:** [back](arkts-arkui-arkui-uicontext-router-c.md#back)(options?: router.RouterOptions)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RouterOptions](arkts-arkui-router-routeroptions-i.md) | No | Description of the target page. The **url** parameter indicates the URL of the page to return to. If the specified page does not exist in the navigation stack, no action is taken. If no URL is set, the application returns to the previous page, and the page is not rebuilt. Pages are only reclaimed after being popped from the navigation stack. Setting **url** to the special value **"/"** has no effect. If the named route is used, the provided URL must be the name of the named route. |

**Examples**

```TypeScript
this.getUIContext().getRouter().back({ url: 'pages/detail' });
```

```TypeScript
this.getUIContext().getRouter().back(1);
```

```TypeScript
this.getUIContext().getRouter().back(1, { info: 'From Home' }); // Returning with parameters.
```


## back

```TypeScript
function back(index: number, params?: Object): void
```

Returns to the specified page, which deletes all pages between the current page and the target page.

> **NOTE:** 
> 
> - Since API version 12, you can use the [getRouter](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getrouter) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Router](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 12

**Deprecated since:** 18

**Substitutes:** [back](arkts-arkui-arkui-uicontext-router-c.md#back)(index: number, params?: Object)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the target page to navigate to. The index starts from 1 from the bottom to the top of the stack. |
| params | Object | No | Parameters carried when returning to the page. |

**Examples**

See [back](#back)
