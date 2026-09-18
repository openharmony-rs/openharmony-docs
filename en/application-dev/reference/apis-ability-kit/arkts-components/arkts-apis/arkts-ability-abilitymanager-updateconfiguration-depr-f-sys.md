# updateConfiguration (System API)

## Modules to Import

```TypeScript
```

## updateConfiguration

```TypeScript
function updateConfiguration(config: Configuration, callback: AsyncCallback<void>): void
```

Updates the configuration. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [updateConfiguration](arkts-ability-abilitymanager-updateconfiguration-f-sys.md)

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [Configuration](arkts-ability-application-configuration-configuration-depr-i.md) | Yes | New configuration. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the configuration is updated, **err** is undefined; otherwise, **err** is an error object. |


## updateConfiguration

```TypeScript
function updateConfiguration(config: Configuration): Promise<void>
```

Updates the configuration. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [updateConfiguration](arkts-ability-abilitymanager-updateconfiguration-f-sys.md)

**Required permissions:** ohos.permission.UPDATE_CONFIGURATION

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [Configuration](arkts-ability-application-configuration-configuration-depr-i.md) | Yes | New configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
