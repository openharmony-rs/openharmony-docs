# parseSendable

## Modules to Import

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## parseSendable

```TypeScript
function parseSendable(text: string, reviver?: SendableTransformer, options?: ParseOptions): ISendable | null
```

Parses a JSON string into a Sendable object graph that can be transferred across concurrent instances (Worker or TaskPool) without copy. When parsed JSON data needs to be shared across threads, use this API instead of [parse](arkts-arkts-json-parse-f.md): the result is created directly in the shared heap and is accessible from all concurrent instances after the call returns.

Usage notes: &lt;ul&gt; &lt;li&gt;Numeric string keys in the range "0" to "4294967294" are stored as element indexes. All keys and values are fully reachable and enumerable regardless of the property count.&lt;/li&gt; &lt;li&gt;For duplicate keys, the last value takes effect, and the enumeration position of the first occurrence is retained.&lt;/li&gt; &lt;li&gt;When options.parseReturnType is [MAP](arkts-arkts-json-parsereturntype-e.md#map), a sendable Map that supports adding and deleting entries of any count is returned; when [OBJECT](arkts-arkts-json-parsereturntype-e.md#object) (default), a non-extensible sendable object is returned, whose existing properties can be updated but cannot be added or deleted.&lt;/li&gt; &lt;/ul&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Valid JSON string. |
| reviver | [SendableTransformer](arkts-arkts-json-sendabletransformer-t.md) | No | A function that transforms the results. Currently only undefined is accepted; providing a function will throw a TypeError (consistent with ASON.parse). The default value is undefined. |
| options | [ParseOptions](arkts-arkts-json-parseoptions-i.md) | No | The parsing options. Any existing ParseOptions object (with only bigIntMode) is also accepted (parseReturnType defaults to OBJECT). The default value is undefined. |

**Return value:**

| Type | Description |
| --- | --- |
| [ISendable](arkts-arkts-json-isendable-t.md) &#124; null | Return a Sendable object graph corresponding to the JSON text; return null if the JSON text is 'null'; return a sendable Map if options.parseReturnType is [MAP](arkts-arkts-json-parsereturntype-e.md#map). |
