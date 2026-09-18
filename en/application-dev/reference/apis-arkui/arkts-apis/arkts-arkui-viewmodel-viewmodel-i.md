# ViewModel

View model @interface ViewModel

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## $t

```TypeScript
$t(path: string, param?: object | Array<any>): string
```

Displays content based on the current system language and a path of the language resource key specified through &#36;t.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the language resource key |
| param | object &#124; Array&lt;any&gt; | No | Content used to replace placeholders during runtime. There are two types of placeholders available: 1. Named placeholder, for example, {name}. The actual content must be of the object type, for example, &#36;t('strings.object', {name: 'Hello world'}). 2. Digit placeholder, for example, {0}. The actual content must be of the array type, for example, &#36;t('strings.array', ['Hello world']). |

**Return value:**

| Type | Description |
| --- | --- |
| string | content to display |

## $refs

```TypeScript
$refs: ElementReferences
```

An object that holds all DOM elements and component instances that have been registered with the refs attribute

**Type:** [ElementReferences](arkts-arkui-viewmodel-elementreferences-i.md)

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite
