# update

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## update

```TypeScript
function update(handle: number, token?: Uint8Array, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

Updates the key operation data by segment. This API uses an asynchronous callback to return the result.

The **huks.init**, **huks.update**, and **huks.finish** must be used together.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [updateSession](arkts-universalkeystore-huks-updatesession-f.md)( handle: number, options: HuksOptions, token: Uint8Array, callback: AsyncCallback&lt;HuksReturnResult&gt; )

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | number | Yes | Handle of the **update** operation, which is of the uint64 type. |
| token | Uint8Array | No | Token of the **update** operation. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Parameter set used for the **update** operation. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[HuksResult](arkts-universalkeystore-huks-huksresult-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**, and **data** is the obtained **HuksResult**. Otherwise, **err** is an error object. |


<a id="update-1"></a>

## update

```TypeScript
function update(handle: number, token?: Uint8Array, options: HuksOptions): Promise<HuksResult>
```

Updates the key operation data by segment. This API uses a promise to return the result.

The **huks.init**, **huks.update**, and **huks.finish** must be used together.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [updateSession](arkts-universalkeystore-huks-updatesession-f.md)(handle: number, options: HuksOptions, token?: Uint8Array)

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | number | Yes | Handle of the **update** operation, which is of the uint64 type. |
| token | Uint8Array | No | Token of the **update** operation. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Parameter set used for the **update** operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksResult](arkts-universalkeystore-huks-huksresult-i.md)&gt; | Promise that returns **HuksResult**. |
