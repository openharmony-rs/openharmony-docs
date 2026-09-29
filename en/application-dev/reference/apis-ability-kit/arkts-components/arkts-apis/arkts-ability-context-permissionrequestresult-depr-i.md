# PermissionRequestResult

```TypeScript
interface PermissionRequestResult
```

**Since:** 7

<!--Device-unnamed-interface PermissionRequestResult--><!--Device-unnamed-interface PermissionRequestResult-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## authResults

```TypeScript
authResults: Array<number>
```

Permission request result.

**Type:** Array&lt;number&gt;

**Default:** The results for the corresponding request permissions

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-PermissionRequestResult-authResults: Array<number>--><!--Device-PermissionRequestResult-authResults: Array<number>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## permissions

```TypeScript
permissions: Array<string>
```

Permissions requested.

**Type:** Array&lt;string&gt;

**Default:** The permissions passed in by the user

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-PermissionRequestResult-permissions: Array<string>--><!--Device-PermissionRequestResult-permissions: Array<string>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## requestCode

```TypeScript
requestCode: number
```

Request code passed.

**Type:** number

**Default:** The request code passed in by the user

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-PermissionRequestResult-requestCode: number--><!--Device-PermissionRequestResult-requestCode: number-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
