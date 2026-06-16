# app Object Internal Structure
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=a1815a6960f035b2f960cbb3747e78fb7c1af4a8 translatedAt=2026-06-15T08:05:24.425Z pushedAt=2026-06-16T14:12:46.631Z -->


The app object contains global app configuration information. Its internal structure is as follows:

**Table 1** **app Object Internal Structure Description**

<!--Table: 15%; 60%; 10%; 15%-->
| Attribute Name | Description | Data Type | Nullable |
| -------- | -------- | -------- | -------- |
| bundleName | Identifier for the app's Bundle name, used to uniquely identify the app. The Bundle name is a string composed of letters, digits, underscores (_), and periods (.), and must start with a letter. The supported string length is 7–128 bytes. The Bundle name is generally expressed in reverse domain name format (for example, "com.example.myapplication"). It is recommended that the first level be the domain suffix "com", the second level be the vendor/individual name, and multiple levels may also be used. | String | Required. |
| vendor | Identifier describing the app's development vendor. The string length does not exceed 255 bytes. | String | Optional. Default value: empty. |
|version | Identifier for the app's version information. | Object | Required. |
| apiVersion | Identifier for the operating system API version that the app depends on. | Object | Optional. Default value: empty. |
| smartWindowSize | Identifier for the screen size used when the app runs in the emulator. | String | Optional. Default value: empty. |
| smartWindowDeviceType | Identifier for the devices that can be simulated when the app runs in the emulator. | String array | Optional. Default value: empty. |
| asanEnabled |   Identifier for whether the app enables ASAN detection to help locate crash issues caused by buffer overflows.<br/>-&nbsp;true: ASAN detection is enabled for the current project.<br/>-&nbsp;false: ASAN detection is not enabled for the current project. | Boolean | Optional. Default value: false. |

## version Object Internal Structure

**Table 2** **version object internal structure**

<!--Table: 15%; 60%; 10%; 15%-->
| Name | Description | Type | Mandatory |
| -------- | -------- | -------- | -------- |
| name | Identifier for the app version, presented to end users. The value can be customized and must not exceed 127 bytes. Customization rules are as follows: API 5 and earlier: A three-segment numeric version number is recommended (two-segment version numbers are also compatible), e.g., A.B.C (A.B is also compatible), where A, B, and C are integers within the range of 0–999. Other formats are not supported.<br/>Segment A: Generally indicates the major version.<br/>Segment B: Generally indicates the minor version.<br/>Segment C: Generally indicates the patch version. API 6 and later: A four-segment numeric version number is recommended, e.g., A.B.C.D, where A, B, and C are integers within the range of 0–99, and D is an integer within the range of 0–999.<br/>Segment A: Generally indicates the major version.<br/>Segment B: Generally indicates the minor version.<br/>Segment C: Generally indicates the feature version.<br/>Segment D: Generally indicates the patch version. | String | Required. |
| code | Identifier for the app version, used only by the operating system to manage the app and not presented to end users. Value rules are as follows: API 5 and earlier: A non-negative integer within 32-bit binary, which must be converted from the value of version.name. The conversion rule is: code value = A&nbsp;\*&nbsp;1,000,000&nbsp;+&nbsp;B&nbsp;\*&nbsp;1,000&nbsp;+&nbsp;C. For example, if the version.name field value is 2.2.1, the code value is 2002001. API 6 and later: The code value is not associated with the version.name field value. Developers can customize the code value, which must be a non-negative integer within 2^31. However, the code field value must be updated with each app version update, and the new version code value must be greater than the old version code value. | Number | Required. |
| minCompatibleVersionCode | Identifier for the minimum compatible version of the app, used in cross-device scenarios to determine whether the app version on another device is compatible. The format requirements are the same as those for the version.code field. | Number | Optional. Default value: code tag value. |

## apiVersion internal structure

**Table 3** **apiVersion internal structure**

| Attribute Name | Description | Data Type | Nullable |
| -------- | -------- | -------- | -------- |
| compatible | The minimum API version required to run the app. The value range is 0 to 2147483647. | Number | Configured in build.profile and populated into config.json by DevEco Studio during packaging. |
| target | Identifier for the API version used by the app at runtime. The value range is 0 to 2147483647. | Number | Configured in build.profile and populated into config.json by DevEco Studio during packaging. |
| releaseType | Identifier for the SDK status used by the app at runtime.<br/>canaryN: An early preview version for specific developers. Quality and API stability are not guaranteed. N represents an integer greater than zero, used to distinguish different versions.<br/>betaN: A publicly released Beta version. API stability is not guaranteed in early Beta versions. After several releases, the Beta version is declared an API stability milestone to developers via Release Notes, and the API of subsequent versions is frozen. N represents an integer greater than zero, used to distinguish different versions.<br/>release: An official release version. Quality is guaranteed and the API cannot be changed. When the version is in this state, the Stage field is not displayed in the version number. | String | Configured in build.profile and populated into config.json by DevEco Studio during packaging. |

Example of the app Object

```json
"app": {
    "bundleName": "com.example.myapplication",
    "vendor": "example",
    "version": {
      "code": 8,
      "name": "8.0.1"
    },
    "apiVersion": {
      "compatible": 8,
      "target": 9,
      "releaseType": "Beta1"
    }
  }
```