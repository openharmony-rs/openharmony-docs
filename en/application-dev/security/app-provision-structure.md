#  HarmonyAppProvision Configuration File
<!-- md-trans-meta sourceCommit=8aa79cb65a7095bb971dc0b556db7006504fdaf2 translatedAt=2026-10-31T02:56:52.957Z pushedAt=2026-10-31T06:11:15.374Z nl=2 -->

The **HarmonyAppProvision** configuration file (also called profile) is a file where you declare permission and signature information for your application.

## Configuration File Structure
The **HarmonyAppProvision** file consists of several parts, which are described in the table below.

| Name     | Description                                                                                     | Data Type | Mandatory | Optional |
| ----------- | ---------------------------------------------------------------------------------------- | -------- | -------- | -------- |
| version-code | Indicates the version number of the HarmonyAppProvision file format. The value is a positive integer within 32 bits in binary. | Number   | Yes | Mandatory                 |
| version-name     | Indicates the text description of the version number. A three-segment numeric version number, such as A.B.C, is recommended.        | String   | Yes | Mandatory |
| uuid    | Indicates the unique ID of the file, used by OEM vendors to identify the HarmonyAppProvision file. This attribute is not mandatory in the open-source community version.                       | String     | Yes | Mandatory |
| type | Indicates the type of the HarmonyAppProvision file. The system predefined file types include debug (for application debugging scenarios) and release (for application release scenarios). In the open-source community version, the value of this attribute is recommended to be debug. | String     | Yes | Mandatory |
| app-distribution-type | Indicates the distribution type of the application. The distribution types include: <li>app_gallery: applications distributed through the app gallery. <li> enterprise: enterprise applications that can be installed on personal devices.<li> enterprise_mdm: enterprise MDM applications that can be installed only on enterprise devices. They require device management privileges, such as remote locking and installing normal enterprise applications. <li>enterprise_normal: normal enterprise applications that can be installed on enterprise devices only through enterprise MDM applications. They do not require device management privileges.<li>os_integration: system preinstalled applications.<li>crowdtesting: crowdsourced testing applications.<li>internaltesting: applications under internal testing in the app gallery.<li>none: others. | String | Yes | Mandatory |
| issuer | Indicates the issuer of the HarmonyAppProvision file.        | String     | Yes | Mandatory |
| validity    | Indicates the validity information of the HarmonyAppProvision file. For details, see [validity](#validity).  | Objects     | Yes | Mandatory  |
| bundle-info | Indicates the information about the application package and the developer. For details, see [bundle-info](#bundle-info).         | Objects     | Yes | Mandatory  |
| acls        | Indicates the authorized ACL permission information. For details, see [acls](#acls).                           | Objects     | Optional | Optional    |
| permissions | Indicates the restricted sensitive permission information that is allowed to be used. For details, see [permissions](#permissions).      | Objects     | Optional | Optional    |
| debug-info  | Indicates the additional information in application debugging scenarios. For details, see [debug-info](#debug-info).          | Objects     | Optional | Optional         |
| app-privilege-capabilities | Indicates the privilege information required by the application package. For details, see [Application Privilege Configuration Guide](../../device-dev/subsystems/subsys-app-privilege-config-guide.md).   | String array | Optional | Optional         |

An example of the **HarmonyAppProvision** file is as follows:
```json
{
    "version-code": 1,
    "version-name": "1.0.0",
	"uuid": "string",
	"type": "debug",
	"app-distribution-type": "os_integration",
	"validity": {
		"not-before": 1586422743,
		"not-after": 1617958743
	},
	"bundle-info" : {
		"developer-id": "OpenHarmony",
		"development-certificate": "Base64 string",
		"distribution-certificate": "Base64 string",
		"bundle-name": "com.OpenHarmony.app.test",
		"apl": "normal",
		"app-feature": "hos_normal_app",
		"data-group-ids": [
			"testGroupId1",
			"testGroupId2"
		]
	},
	"acls": {
		"allowed-acls": ["string"]
    },
	"permissions": {
		"restricted-permissions": ["string"]
    },
    "debug-info" : {
	    "device-id-type": "udid",
	    "device-ids": ["string"]
    },
    "app-privilege-capabilities":["AllowAppUsePrivilegeExtension"],
    "issuer": "OpenHarmony"
}

```

### validity

| Name   | Description                           | Data Type| Mandatory| Initial Value Allowed|
| ---------- | ------------------------------- | ------- | ------- | --------- |
| not-before | Start time of the file validity period. The value is a Unix timestamp, which is a non-negative integer.| Number   | Yes| No  |
| not-after  | End time of the file validity period. The value is a Unix timestamp, which is a non-negative integer.| Number   | Yes| No  |

### bundle-info

Note: The value of **bundle-name** in the **bundle-info** object in the HarmonyAppProvision file must be the same as the value of **bundleName** (in **config.json** or **module.json5**) of the signed application. To prevent a HarmonyAppProvision file from being used for signatures of different applications, the system checks whether the value of **bundleName** in the HAP signature is the same as that in the HAP configuration file during application installation. If they are different, the HAP cannot be installed.

| Name                 | Description                           | Data Type| Mandatory| Initial Value Allowed|
| ------------------------ | ------------------------------- | ------- | -------- | --------- |
| developer-id | Unique ID of the developer.| String   | Yes| No  |
| development-certificate  | Information about the [debug certificate](hapsigntool-guidelines.md).| Number   | Yes if **type** is set to **debug** and no otherwise  | No  |
| distribution-certificate  | Information about the [release certificate](hapsigntool-guidelines.md).| Number   | Yes if **type** is set to **release** and no otherwise| No  |
| bundle-name  | Bundle name of the application.| String   | Yes| No  |
| apl  | [Ability Privilege Level (APL)](AccessToken/access-token-overview.md) of the application. The predefined APLs includes normal, system_basic, and system_core.| String   | Yes| No  |
| app-feature  | Type of your application. The value can be **hos_system_app** (system application) or **hos_normal_app** (normal application). Only system applications are allowed to call system APIs. If a normal application calls a system API, the call cannot be successful or the application may run abnormally.| String   | Yes| No  |
| data-group-ids  | IDs of application data groups. When an application is installed, a directory is generated for each data group ID. If two applications or an ExtensionAbility and its application have the same data group ID in **data-group-ids**, they can share the data in the directory corresponding to the same data group ID. An ExtensionAbility declares the data group IDs in the **dataGroupIds** field in the [module.json5](../quick-start/module-configuration-file.md#extensionabilities) file.| String array   | No| Yes (initial value: left empty)  |
| app-identifier | Unique ID of the application, which is allocated by the cloud. This ID does not change along the application lifecycle, including version updates, certificate changes, public and private key changes, and application transfers.| String array   | No| Yes (initial value: left empty)  |


### acls
The **acls** object contains the [permissions authorized via the ACL](AccessToken/permissions-for-system-apps.md). It should be noted that you still need to fill the ACL information in the **requestPermissions** attribute in the application bundle configuration file.

| Name                 | Description                           | Data Type| Mandatory| Initial Value Allowed|
| ------------------------ | ------------------------------- | ------- | ------- | --------- |
| allowed-acls | [Permissions authorized via the ACL](AccessToken/permissions-for-system-apps.md).| String array   | No| No  |

### permissions
The **permissions** object contains restricted permissions required for your application. Different from the ACLs set in the **acls** object, these permissions need user authorization during the running of your application. It should be noted that you still need to fill the permission information in the **requestPermissions** attribute in the application bundle configuration file.

| Name                 | Description                           | Data Type| Mandatory| Initial Value Allowed|
| ------------------------ | ------------------------------- | ------- | ------- | --------- |
| restricted-permissions | Restricted sensitive permissions allowed. For details, see [Restricted Permissions](AccessToken/restricted-permissions.md).| String array   | No| No  |

### debug-info
The **debug-info** object contains debugging information of your application, mainly device management and control information.

| Name                 | Description                           | Data Type| Mandatory| Initial Value Allowed|
| ------------------------ | ------------------------------- | ------- | ------- | --------- |
| device-id-type | Type of the device ID. Currently, only the udid type is supported.| String   | No| No  |
| device-ids | IDs of devices on which your application can be debugged.| String array   | No| No  |

## Modifying the HarmonyAppProvision Configuration File

When a development project is created, the default application type is **hos_normal_app** and the default APL level is **normal**.

To enable the application to use system APIs, you need to change the **app-feature** field to **hos_system_app** (system application). To request high-level permissions, you need to modify fields such as **apl** and **acl**. For details, see [Access Control Overview](AccessToken/access-token-overview.md).


To modify the HarmonyAppProvision configuration file, perform the following steps:

1. Open the directory where the OpenHarmony SDK is located. (You can view it by clicking **File** > **Settings** > **OpenHarmony SDK** in the menu bar of DevEco Studio.)
2. In the SDK directory, go to the `Toolchains` > `{Version}` > `lib` folder and open the `UnsgnedReleasedProfileTemplate.json` file.
3. Modify the related fields as required.

After modifying the configuration file, [sign the app](hapsigntool-guidelines.md).

<!--no_check-->