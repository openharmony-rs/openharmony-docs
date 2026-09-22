# Options

```TypeScript
export interface Options<T extends ViewModel, Data = DefaultData<T>>
```

Options type @interface Options

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## onCreate

```TypeScript
onCreate?(): void
```

Called when the application is created

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## onDestroy

```TypeScript
onDestroy?(): void
```

Called when the application is destroyed or called when the page is redirected to another one (without entering the navigation stack).

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## onHide

```TypeScript
onHide?(): void
```

Listens for page hiding. Called when the page disappears.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## onInit

```TypeScript
onInit?(): void
```

Called when the page is initialized. This function can be called only once in a lifecycle.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## onReady

```TypeScript
onReady?(): void
```

Called when the page is created. This function can be called only once in a lifecycle.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## onRestoreData

```TypeScript
onRestoreData?(data: Object): void
```

Called when the user data need to be restored

**Since:** 10

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Object | Yes | Indicates the user data to restore. |

## onSaveData

```TypeScript
onSaveData?(data: Object): boolean
```

Called when the user data need to be saved

**Since:** 10

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Object | Yes | Indicates the user data to save. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the data is successfully saved; returns `false` otherwise. |

## onShow

```TypeScript
onShow?(): void
```

Called when the page is displayed.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## data

```TypeScript
data?: Data
```

Data model of the page that can be converted into a JSON object. The attribute name cannot start with $ or an underscore (_) or contain the reserved words such as for, if, show, and tid. For a function, the return value must be an object. Set the value of data to the return value of the function during page initialization.

**Type:** Data

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite
