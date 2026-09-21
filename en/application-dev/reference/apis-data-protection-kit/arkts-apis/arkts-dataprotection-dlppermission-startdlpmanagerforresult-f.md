# startDLPManagerForResult

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## startDLPManagerForResult

```TypeScript
function startDLPManagerForResult(context: common.UIAbilityContext, want: Want): Promise<DLPManagerResult>
```

Starts the DLP manager application on the current [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md) page in borderless mode. This API uses a promise to return the result.

This API starts the DLP manager application to configure file permissions and return the user operation result to the caller.

> **NOTE:** 
> 
> This API can be called only by domain accounts.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [common.UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) | Yes | [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md) context. |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Request object, which must contain the **uri** and **displayName** fields. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DLPManagerResult](arkts-dataprotection-dlppermission-dlpmanagerresult-i.md)&gt; | Promise used to return the **DLPManagerResult** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.0.1 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |
| [19100016](../errorcode-dlp.md#19100016-uri-missing-in-want) | The uri field is missing in the want parameter. |
| [19100017](../errorcode-dlp.md#19100017-displayname-missing-in-parameters-of-want) | The displayName field is missing in the want parameter. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { common, Want } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

let context = new UIContext().getHostContext() as common.UIAbilityContext; // Obtain the current UIAbilityContext.
if (context !== undefined) {
    let want: Want = {
        "uri": "file://docs/storage/Users/currentUser/Desktop/1.txt",
        "parameters": {
        "displayName": "1.txt"
        }
    }; // Construct request parameters, which must include uri and displayName.
    dlpPermission.startDLPManagerForResult(context, want).then((res) => {
        console.info('res.resultCode', res.resultCode);
        console.info('res.want', JSON.stringify(res.want));
    }); // Start the DLP manager application.
}
```


<a id="startdlpmanagerforresult-1"></a>

## startDLPManagerForResult

```TypeScript
function startDLPManagerForResult(context: common.Context, want: Want, window: window.Window): Promise<DLPManagerResult>
```

Starts the DLP manager application in a specified window in borderless mode. This API uses a promise to return the result.

This API starts the DLP manager application to configure file permissions and return the user operation result to the caller.

> **NOTE:** 
> 
> This API can be called only by domain accounts.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [common.Context](../../apis-ability-kit/arkts-apis/arkts-ability-common-context-t.md) | Yes | Ability context information. |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Request object, which must contain the **uri** and **displayName** fields. |
| window | [window.Window](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md) | Yes | Window object used to start the DLP manager application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DLPManagerResult](arkts-dataprotection-dlppermission-dlpmanagerresult-i.md)&gt; | Promise used to return the **DLPManagerResult** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature. |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |
| [19100016](../errorcode-dlp.md#19100016-uri-missing-in-want) | The uri field is missing in the want parameter. |
| [19100017](../errorcode-dlp.md#19100017-displayname-missing-in-parameters-of-want) | The displayName field is missing in the want parameter. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { common, Want } from '@kit.AbilityKit';
import { UIContext, window } from '@kit.ArkUI';

let config: window.Configuration = {
  name: "dlp_test_window",
  windowType: window.WindowType.TYPE_FLOAT,
  ctx: new UIContext().getHostContext() as common.Context
};
window.createWindow(config).then((windowClass) => {
  windowClass.setUIContent('pages/index/BlankPage');
  windowClass.setWindowFocusable(true);
  windowClass.setWindowBackgroundColor("#00000000");

  let context = new UIContext().getHostContext() as common.Context; // Obtain the current context.
  if (context !== undefined) {
    let want: Want = {
      "uri": "file://docs/storage/Users/currentUser/Desktop/1.txt",
      "parameters": {
        "displayName": "1.txt"
      }
    }; // Construct request parameters, which must include uri and displayName.
    dlpPermission.startDLPManagerForResult(context, want, windowClass).then((res) => {
      console.info('res.resultCode', res.resultCode);
      console.info('res.want', JSON.stringify(res.want));
      windowClass.destroyWindow();
    }); // Start the DLP manager application.
  }
});
```
