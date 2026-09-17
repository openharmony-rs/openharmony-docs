# isSystemReady (System API)

## Modules to Import

```TypeScript
```

## isSystemReady

```TypeScript
function isSystemReady(callback: AsyncCallback<void>): void
```

Checks whether the system is ready. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isSystemReady](arkts-form-formhost-issystemready-f-sys.md)

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the check is successful, **error** is undefined; otherwise, **error** is an error object. |


## isSystemReady

```TypeScript
function isSystemReady(): Promise<void>
```

Checks whether the system is ready. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isSystemReady](arkts-form-formhost-issystemready-f-sys.md)

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
