# EnterpriseAdminExtensionContext
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->

**EnterpriseAdminExtensionContext** is the context of [EnterpriseAdminExtensionAbility](js-apis-EnterpriseAdminExtensionAbility.md) and inherits from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md).

When an **EnterpriseAdminExtensionAbility** component is instantiated, the system automatically creates the corresponding **EnterpriseAdminExtensionContext**. You can use this **EnterpriseAdminExtensionContext** to obtain the sandbox path of the app and start other components. This context can only be used within the current **EnterpriseAdminExtensionAbility** and cannot be transferred to other components.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - The APIs of this module can be called only by a device administrator application that is enabled. For details, see [MDM Kit Development](../../mdm/mdm-kit-guide.md).

## Modules to Import

```ts
import { common } from '@kit.MDMKit';
```

## EnterpriseAdminExtensionContext

Context of the [EnterpriseAdminExtensionAbility](js-apis-EnterpriseAdminExtensionAbility.md) component. It inherits from [ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md).

### startAbilityByAdmin

startAbilityByAdmin(admin: Want, want: Want): Promise\<void>

Directly starts another component within the [EnterpriseAdminExtensionAbility](js-apis-EnterpriseAdminExtensionAbility.md) component (without pop-up prompts on the page). Currently, [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md) and [AppServiceExtensionAbility](../apis-ability-kit/js-apis-app-ability-appServiceExtensionAbility.md) are supported. This API uses a promise to return the result.

> **NOTE**
>
> - Only third-party app components are supported; system app components are not supported.
> 
> - The component to start must be visible to external parties, that is, the **exported** field in the **module.json5** file must be set to **true**.
> 
> - [Implicit Want launch](../../application-models/ability-terminology.md) is not supported.
> 
> - If the **UIAbility** to start has permission protection, you need to apply for the corresponding permission.

**Required permissions**: ohos.permission.ENTERPRISE_START_ABILITIES

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| admin | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes| EnterpriseAdminExtensionAbility. **Want** must contain the ability name of **EnterpriseAdminExtensionAbility** and the app bundle name.|
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes| Mandatory information for starting a component. The **Want** must contain the ability name of the component to be started and the bundle name of the app where the component is located.|

**Return values**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the component fails to be started, an error object is thrown.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200014  | Failed to start the ability. |
| 9200015  | The ability does not exist. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**
Configure the information of the component to be started in **module.json5**.

```json
"abilities": [
    {
        "name": "MainAbility",
        "srcEntry": "./ets/MainAbility/MainAbility.ts",
        "description": "$string:MainAbility_desc",
        "icon": "$media:icon",
        "label": "$string:MainAbility_label",
        "startWindowIcon": "$media:icon",
        "startWindowBackground": "$color:white",
        "exported": true,
        // Optional field
        "permissions": [
            // Replace with actual values or leave it empty.
            "ohos.permission.START_UI_Ability"
        ]
    }
]
```

The caller app needs to apply for the corresponding permissions in **module.json5**.

```json
"requestPermissions": [
    {
        // When starting a component of another app, the caller app must obtain the permissions required by the component.
        "name": "ohos.permission.START_UI_ABILITY"
    },
    {
        "name": "ohos.permission.ENTERPRISE_START_ABILITIES"
    }
]
```

```ts
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';
import { preferences } from '@kit.ArkData';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

/**
 * EnterpriseAdminExtensionAbility
 */
export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
    onAdminEnabled() {
        // Replace with actual values.
        let admin: Want = {
            bundleName: 'com.example.myapplication',
            abilityName: 'EnterpriseAdminAbility',
        };
        // Replace with actual values.
        let want: Want = {
            bundleName: 'com.example.myotherapplication',
            abilityName: 'MainAbility'
        };
        this.context.startAbilityByAdmin(admin, want).catch((err: BusinessError) => {
            console.error(`Failed to start an ability. Code: ${err.code}, message: ${err.message}`);
        });
    
        // Obtain the app file path through the context.
        let preferencesDir = this.context.preferencesDir;
        console.log(`preferencesDir: ` + preferencesDir);
    
        // Obtain the preferences data through the context.
        let options: preferences.Options = {
        // Replace with actual values.
            name: "key",
        };
        try {
        let preference = preferences.getPreferencesSync(this.context, options);
        // Replace with actual values.
        preference.putSync("key", "value");
        preference.flushSync();
    
        // Replace with actual values.
        let value: string = preference.getSync('key', 'default') as string;
            console.info(`get preferences value: ${value}`);
        } catch (error) {
            console.error('get preference fail');
        }
    }
}
```
