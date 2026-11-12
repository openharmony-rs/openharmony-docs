# ValidationCallback

```TypeScript
export type ValidationCallback = (context: ValidationContext) => boolean | Promise<boolean>
```

Defines a custom callback for remote server identity verification. Developers can use this callback to implement custom certificate verification logic, supporting synchronous or asynchronous return of the verification result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-http-export type ValidationCallback = (context: ValidationContext) => boolean | Promise<boolean>--><!--Device-http-export type ValidationCallback = (context: ValidationContext) => boolean | Promise<boolean>-End-->

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [ValidationContext](arkts-network-http-validationcontext-i.md) | Yes | Certificate verification context, which contains information such as the certificate chain, host name, and IP address. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean &#124; Promise&lt;boolean&gt; | Returns a boolean value indicating whether the validation is successful. Promise used to return the result. The value true indicates valid, and false indicates invalid. |
