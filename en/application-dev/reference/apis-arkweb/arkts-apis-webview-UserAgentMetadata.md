# Class (UserAgentMetadata)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=c3549f5fc26f86afdb3e7a215c50ff6d6d5cab0c translatedAt=2026-08-07T04:47:00.586Z pushedAt=2026-08-07T08:11:27.837Z -->

UserAgentMetadata is a class in the ArkWeb framework used to configure the complete metadata for User-Agent Client Hints. User-Agent Client Hints is a modern HTTP request header mechanism that reports client information to the server through a set of Sec-CH-UA series headers, replacing the traditional User-Agent string to achieve more secure and more granular browser identity identification. Through UserAgentMetadata, apps can customize all client information fields reported by the Web component to the server.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 24. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 24.
>
> - The sample effect is subject to the actual device.

## setBrandVersionList

setBrandVersionList(brandVersionList: Array\<UserAgentBrandVersion>): void

Sets the brand and version information.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name             | Type   | Mandatory  |  Description|
| ------------------ | ------- | ---- | ------------- |
| brandVersionList | Array\<[UserAgentBrandVersion](./arkts-apis-webview-UserAgentBrandVersion.md)> | Yes  | **Sec-CH-UA-Full-Version-List** of the request header. If this parameter is left empty, the default ArkWeb value is used.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getBrandVersionList

getBrandVersionList(): Array\<UserAgentBrandVersion>

Obtains the brand and version information list. If the corresponding [setBrandVersionList](#setbrandversionlist) is not called for configuration, the default value of the list is: [{"brand":"Chromium","version":[ChromeCompatibleVersion](../../web/web-default-userAgent.md#default-user-agent-structure)}, {"brand":"ArkWeb","version":[OSVersion](../../web/web-default-userAgent.md#default-user-agent-structure)}].

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| Array\<[UserAgentBrandVersion](./arkts-apis-webview-UserAgentBrandVersion.md)> | Brand and version information list.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## setArchitecture

setArchitecture(arch: string): void

Sets the architecture type of the platform.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name             | Type   | Mandatory  |  Description|
| ------------------ | ------- | ---- | ------------- |
| arch | string | Yes  | **Sec-CH-UA-Arch** of the request header. If this parameter is left empty, the default ArkWeb value is used.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getArchitecture

getArchitecture(): string

Obtains the architecture type of the platform. If the corresponding [setArchitecture](#setarchitecture) is not called for configuration, the default value of the architecture type is: "".

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | Platform architecture type.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## setBitness

setBitness(bitness: string): void

Sets the bitness type of the platform.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name             | Type   | Mandatory  |  Description|
| ------------------ | ------- | ---- | ------------- |
| bitness | string | Yes | Corresponds to the Sec-CH-UA-Bitness request header. If empty, the default value of ArkWeb is used. |

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getBitness

getBitness(): string

Obtains the bitness type of the platform. If the corresponding [setBitness](#setbitness) is not called for configuration, the default value of the bitness type is: Desktop: "64", other devices: "".

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | Bitness type of the platform.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## setFormFactors

setFormFactors(formFactors: Array\<UserAgentFormFactor>): void

Sets the device form, such as the mobile phone or tablet.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name             | Type   | Mandatory  |  Description|
| ------------------ | ------- | ---- | ------------- |
| formFactors | Array\<[UserAgentFormFactor](./arkts-apis-webview-e.md#useragentformfactor24)> | Yes  | **Sec-CH-UA-Form-Factor** of the request header. If this parameter is left empty, the default ArkWeb value is used.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getFormFactors

getFormFactors(): Array\<UserAgentFormFactor>

Obtains the device form factor information, such as phone and tablet. If the corresponding [setFormFactors](#setformfactors) is not called for configuration, the default value of the form factor information is: Phone: "Mobile", Watch: "Watch", Automotive: "Automotive", PC: "Desktop", Tablet: "Tablet".

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| Array\<[UserAgentFormFactor](./arkts-apis-webview-e.md#useragentformfactor24)> | Device form information.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## setFullVersion

setFullVersion(fullVersion: string): void

Sets the full version number.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name             | Type   | Mandatory  |  Description|
| ------------------ | ------- | ---- | ------------- |
| fullVersion | string | Yes  | **Sec-CH-UA-Full-Version** of the request header. If this parameter is left empty, the default ArkWeb value is used.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getFullVersion

getFullVersion(): string

Obtains the full version number. If the corresponding [setFullVersion](#setfullversion) is not called for configuration, the default value of the version number is: "".

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | Full version number.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## setMobile

setMobile(isMobile: boolean): void

Sets whether the device is a mobile device.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name             | Type   | Mandatory  |  Description|
| ------------------ | ------- | ---- | ------------- |
| isMobile | boolean | Yes | Whether the device is a mobile device. Corresponds to the Sec-CH-UA-Mobile request header. The value true means the device is a mobile device, and false means the opposite. |

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getMobile

getMobile(): boolean

Obtains whether the device is a mobile device. If the corresponding [setMobile](#setmobile) is not called for configuration, the default value is: Phone: true, Watch, Automotive, Tablet, Large screen: false.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| boolean | Whether the device is a mobile device. **true** means yes; **false** otherwise.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## setModel

setModel(model: string): void

Sets the device model.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name             | Type   | Mandatory  |  Description|
| ------------------ | ------- | ---- | ------------- |
| model | string | Yes  | Value of the Sec-CH-UA-Model request header. If empty, the default value of ArkWeb is used. |

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getModel

getModel(): string

Obtains the device model. If the corresponding [setModel](#setmodel) is not called for configuration, the default value of the model is: Phone: obtains the device model based on const.product.model; Watch, Large screen, Automotive, PC, Tablet: "".

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | Device model.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## setPlatform

setPlatform(platform: string): void

Sets the OS name.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name             | Type   | Mandatory  |  Description|
| ------------------ | ------- | ---- | ------------- |
| platform | string | Yes  | **Sec-CH-UA-Platform** of the request header. If this parameter is left empty, the default ArkWeb value is used.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getPlatform

getPlatform(): string

Obtains the operating system name. If the corresponding [setPlatform](#setplatform) is not called for configuration, the default value of the name is: "OpenHarmony".

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | OS name.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## setPlatformVersion

setPlatformVersion(platformVersion: string): void

Sets the OS version.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name             | Type   | Mandatory  |  Description|
| ------------------ | ------- | ---- | ------------- |
| platformVersion | string | Yes  | **Sec-CH-UA-Platform-Version** of the request header. If this parameter is left empty, the default ArkWeb value is used.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getPlatformVersion

getPlatformVersion(): string

Obtains the operating system version number. If the corresponding [setPlatformVersion](#setplatformversion) is not called for configuration, the default value of the version number is: follows the OpenHarmony platform version number rules, same as const.product.os.dist.version.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | OS version.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## setWow64

setWow64(isWow64: boolean): void

Sets whether the binary file runs in 32-bit mode on a 64-bit Windows.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name             | Type   | Mandatory  |  Description|
| ------------------ | ------- | ---- | ------------- |
| isWow64 | boolean | Yes   | Corresponds to the Sec-CH-UA-WoW64 request header. Whether the binary file is running in 32-bit mode on 64-bit Windows. The value **true** means yes, and **false** means no. |

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getWow64

getWow64(): boolean

Obtains whether the binary file is running in 32-bit mode on 64-bit Windows. If the corresponding [setWow64](#setwow64) is not called for configuration, the default value is false.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| boolean | Whether the binary file runs in 32-bit mode on a 64-bit Windows. **true** means yes; **false** otherwise.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).