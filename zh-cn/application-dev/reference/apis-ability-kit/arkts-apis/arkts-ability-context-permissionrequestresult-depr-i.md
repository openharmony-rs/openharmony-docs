# PermissionRequestResult

授权结果信息。

**起始版本：** 7

<!--Device-unnamed-interface PermissionRequestResult--><!--Device-unnamed-interface PermissionRequestResult-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## authResults

```TypeScript
authResults: Array<number>
```

请求权限的结果。

**类型：** Array&lt;number&gt;

**默认值：** The results for the corresponding request permissions

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-PermissionRequestResult-authResults: Array<number>--><!--Device-PermissionRequestResult-authResults: Array<number>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## permissions

```TypeScript
permissions: Array<string>
```

用户传入的权限。

**类型：** Array&lt;string&gt;

**默认值：** The permissions passed in by the user

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-PermissionRequestResult-permissions: Array<string>--><!--Device-PermissionRequestResult-permissions: Array<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## requestCode

```TypeScript
requestCode: number
```

用户传入的请求代码。

**类型：** number

**默认值：** The request code passed in by the user

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-PermissionRequestResult-requestCode: number--><!--Device-PermissionRequestResult-requestCode: number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

