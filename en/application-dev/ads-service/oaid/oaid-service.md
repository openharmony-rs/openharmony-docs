# OAID Service

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->

## Obtaining an OAID


### When to Use

An Open Anonymous Device Identifier (OAID) is a non-permanent device identifier. It allows personalized ads to be provided to users while ensuring the protection of their personal data privacy. Additionally, it allows third-party tracking platforms to offer conversion attribution analysis to advertisers.

No matter whether you are running a media application, an ad platform, or a tracking platform, you can obtain OAID information from devices. The OAID information can be used to recommend personalized ads to users and attribute ad conversions.

An OAID is a 32-bit Universally Unique Identifier (UUID) generated using a Huawei algorithm. The format is xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.

The OAID has the following features:
- The OAID is device specific. Different applications on the same device obtain the same OAID.
- The OAID obtained depends on the switch of the ohos.permission.APP_TRACKING_CONSENT permission. When the switch is enabled, the application obtains a valid OAID that is not all zeros. When the switch is disabled, the application obtains an all-zero OAID.
- An OAID is generated when any application on the device enables the ohos.permission.APP_TRACKING_CONSENT permission for the first time.

The OAID changes in the following scenarios:
- A user restores the device to factory settings.
- A user resets the OAID.

### Available APIs

| API| Description|
| -------- | -------- |
| <!--Del-->[<!--DelEnd-->getOAID<!--Del-->](../../reference/apis-ads-kit/js-apis-oaid.md#identifiergetoaid)<!--DelEnd-->(): Promise&lt;string&gt; | Obtains an OAID. This API uses a promise to return the result.|
| <!--Del-->[<!--DelEnd-->getOAID<!--Del-->](../../reference/apis-ads-kit/js-apis-oaid.md#identifiergetoaid-1)<!--DelEnd-->(callback:&nbsp;AsyncCallback&lt;string&gt;):&nbsp; void | Obtains an OAID. This API uses an asynchronous callback to return the result.|

> **NOTE**
> To call **getOAID()**, an application must request the permission ohos.permission.APP_TRACKING_CONSENT and obtain user authorization. The following three scenarios are involved:<br>
> 1. If the application has configured the permission ohos.permission.APP_TRACKING_CONSENT and the permission is allowed, the OAID is returned.<br>
> 2. If the application has configured the permission ohos.permission.APP_TRACKING_CONSENT and the permission is disallowed, 00000000-0000-0000-0000-000000000000 is returned.<br>
> 3. If the application has not configured the permission ohos.permission.APP_TRACKING_CONSENT, 00000000-0000-0000-0000-000000000000 is returned.


### How to Develop
1. In the **module.json5** file of the module, configure the permission [ohos.permission.APP_TRACKING_CONSENT](../../security/AccessToken/permissions-for-all-user.md#ohospermissionapp_tracking_consent), which is a user_grant permission. In this case, the **reason** and **abilities** fields are mandatory. For details about the configuration, see [Declaring Permissions in the Configuration File](../../security/AccessToken/declare-permissions.md#declaring-permissions-in-the-configuration-file). The sample code is as follows:
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

2. To obtain the OAID, the application must call **requestPermissionFromUser** to obtain the corresponding permission. For details about how to obtain the context, see [Acquisition of Context](../../application-models/application-context-stage.md#acquisition-of-context). The sample code is as follows:
    ```ts
    import { abilityAccessCtrl, PermissionRequestResult } from '@kit.AbilityKit';
    import { identifier } from '@kit.AdsKit';
    import { hilog } from '@kit.PerformanceAnalysisKit';

    async function requestOAID(context: Context): Promise<string | undefined> {
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
        try {
          const oaid = await identifier.getOAID();
          hilog.info(0x0000, 'testTag', 'Succeeded in getting OAID');
          return oaid;
        } catch (err) {
          hilog.error(0x0000, 'testTag', `Failed to get OAID. Code is ${err.code}, message is ${err.message}`);
        }
      } else {
        hilog.error(0x0000, 'testTag', 'Failed to request permission. User rejected');
      }
      return undefined;
    }
    ```
