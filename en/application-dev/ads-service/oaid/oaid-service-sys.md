# Resetting OAID Information (for System Applications Only)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->

## When to Use

The OAID changes in the following scenarios:
- A system application configures its `bundleName` in the `etc/advertising/oaid/oaid_service_config.json` file in the device's system directory and calls the `resetOAID()` API to reset the OAID. Note that the bundle name should be appended to the array in the file and separated with others by commas (,).

## Available APIs

| API| Description|
| -------- | -------- |
| [resetOAID()](../../reference/apis-ads-kit/js-apis-oaid-sys.md#identifierresetoaid):&nbsp;void | Resets an OAID. This is a system API.|


## How to Develop

1. In the **module.json5** file of the module, configure the permission [ohos.permission.APP_TRACKING_CONSENT](../../security/AccessToken/permissions-for-all-user.md#ohospermissionapp_tracking_consent). The sample code is as follows:
    ```ts
    {
      "module": {
        "requestPermissions": [
          {
            "name": "ohos.permission.APP_TRACKING_CONSENT",
            "reason": "$string:reason",
            "usedScene": {
              "abilities": [
                "EntryFormAbility"
              ],
              "when": "inuse"
            }
          }
        ]
      }
    }
    ```
    Request authorization from the user in a dialog box when the application is started. For details about how to obtain the context, see [Acquisition of Context](../../application-models/application-context-stage.md#acquisition-of-context). The sample code is as follows:
    ```ts
    import { abilityAccessCtrl, PermissionRequestResult } from '@kit.AbilityKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';

    async function requestAppTrackingConsentPermission(context: Context): Promise<void> {
      let isPermissionGranted: boolean = false;
      try {
        const atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
        const result: PermissionRequestResult =
          await atManager.requestPermissionsFromUser(context, ['ohos.permission.APP_TRACKING_CONSENT']);
        isPermissionGranted = result.authResults[0] === abilityAccessCtrl.GrantStatus.PERMISSION_GRANTED;
      } catch (err) {
        hilog.error(0x0000, 'testTag', `Failed to request permission. Code is ${err.code}, message is ${err.message}`);
      }
      if (isPermissionGranted) {
        hilog.info(0x0000, 'testTag', 'Succeeded in requesting permission');
      } else {
        hilog.error(0x0000, 'testTag', 'Failed to request permission. User rejected');
      }
    }
    ```

2. Call **resetOAID()** to reset the OAID. The sample code is as follows:
    ```ts
    import { identifier } from '@kit.AdsKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';

    try {
      identifier.resetOAID();
    } catch (err) {
      hilog.error(0x0000, 'testTag', `Failed to reset OAID. Code is ${err.code}, message is ${err.message}`);
    }
    ```
