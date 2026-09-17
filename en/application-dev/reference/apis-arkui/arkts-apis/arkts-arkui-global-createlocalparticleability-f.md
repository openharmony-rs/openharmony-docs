# createLocalParticleAbility

## createLocalParticleAbility

```TypeScript
export declare function createLocalParticleAbility(name?: string): any
```

Get the java interface instance. The java instance needs to register, otherwise it cannot be obtained. After obtaining the instance, you can call the function with the same name on the Java side.

**Since:** 5

**Deprecated since:** 8

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | No | Java interface name, including package path, such as com.example.test.timeinterfaceimpl. |

**Return value:**

| Type | Description |
| --- | --- |
| any | A promise object is returned. The resolve callback is the object of PA. The reject callback returns the object containing code and error data. |
