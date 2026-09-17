# promiseWrapper

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## promiseWrapper

```TypeScript
function promiseWrapper(original: (err: Object, value: Object) => void): Object
```

Receives a function that uses the error-first callback mode, that is, uses `(err, value) =&gt; callback` as the last parameter, and uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [promisify](arkts-arkts-util-promisify-f.md)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| original | (err: Object, value: Object) =&gt; void | Yes | Asynchronous function. |

**Return value:**

| Type | Description |
| --- | --- |
| Object | Promise in the error-first style (that is, (err, value) =&gt; ... is called as the last parameter). |
