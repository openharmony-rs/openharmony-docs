# finish

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## finish

```TypeScript
function finish(handle: number, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

Finishes the key operation. This API uses an asynchronous callback to return the result.

The **huks.init**, **huks.update**, and **huks.finish** must be used together.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [finishSession](arkts-universalkeystore-huks-finishsession-f.md)(handle: number, options: HuksOptions, callback: AsyncCallback&lt;HuksReturnResult&gt;)

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | number | Yes | Handle of the **finish** operation, which is of the uint64 type. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Parameter set used for the **finish** operation. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[HuksResult](arkts-universalkeystore-huks-huksresult-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **data** is the obtained **HuksResult**. Otherwise, **err** is an error object. |


## finish

```TypeScript
function finish(handle: number, options: HuksOptions): Promise<HuksResult>
```

Finishes the key operation. This API uses a promise to return the result.

The **huks.init**, **huks.update**, and **huks.finish** must be used together.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [finishSession](arkts-universalkeystore-huks-finishsession-f.md)( handle: number, options: HuksOptions, token: Uint8Array, callback: AsyncCallback&lt;HuksReturnResult&gt; )

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | number | Yes | Handle of the **finish** operation, which is of the uint64 type. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Parameter set used for the **finish** operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksResult](arkts-universalkeystore-huks-huksresult-i.md)&gt; | Promise that returns **HuksResult**. |
