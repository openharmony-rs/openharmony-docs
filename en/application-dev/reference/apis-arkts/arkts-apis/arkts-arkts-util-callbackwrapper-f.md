# callbackWrapper

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## callbackWrapper

```TypeScript
function callbackWrapper(original: Function): (err: Object, value: Object) => void
```

Calls back an asynchronous function. In the callback, the first parameter indicates the cause of the rejection (the value is **null** if the promise has been resolved), and the second parameter indicates the resolved value.

> **NOTE:** 
> 
> - **original** must be an asynchronous function. If a non-asynchronous function is passed in, the function is not intercepted, but the error message "callbackWrapper: The type of Parameter must be AsyncFunction" is displayed.
> 
> - This API converts an async function that returns a promise into an error-first callback function. The function returned by this API accepts a callback as its second input parameter. When this method is called, the original function is executed first. When the promise of **original** returns **resolve**, the first parameter of the callback function is **null**, and the second parameter is the value of **resolve**. When the promise of
> **original** returns **reject**, the first parameter of the callback function is an error object, and the second
> parameter is **null**. When **original** is a function without input parameters, the first input parameter of the
> function returned by this API must be an invalid placeholder parameter.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| original | Function | Yes | Asynchronous function. |

**Return value:**

| Type | Description |
| --- | --- |
| [function](arkts-arkts-taskpool-task-c.md) | Callback function, in which the first parameter **err** indicates the cause of the rejection (the value is **null** if the promise has been resolved) and the second parameter **value** indicates the resolved value. |

**Examples**

```TypeScript
async function fn(input: string) {
  return input;
}
let cb = util.callbackWrapper(fn);
cb('hello world', (err : Object, ret : string) => {
  if (err) throw new Error;
  console.info(ret);
});
// Output: hello world
```
