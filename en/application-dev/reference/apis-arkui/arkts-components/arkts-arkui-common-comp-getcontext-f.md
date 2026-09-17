# getContext

## getContext

```TypeScript
declare function getContext(component?: Object): Context
```

Obtains the Context object associated with a component on the page.

**Since:** 11

**Deprecated since:** 18

**Substitutes:** [getHostContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#gethostcontext)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| component | Object | No | indicate the component on the page. If no component is passed in or the passed-in parameter type is invalid, the default context is returned. The default context is the context obtained by tracing the call chain of the API. If this API is used in an asynchronous callback or not initially called on the current page, the context of the instance may fail to be traced. In this case, undefined is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [Context](arkts-arkui-context-t.md) | The context type depends on the ability type. For example, if this API is called on a page of the UIAbility, the return value type is UIAbilityContext; if this API is called on a page of the ExtensionAbility, the return value type is ExtensionContext. |
