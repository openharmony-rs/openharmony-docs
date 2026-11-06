# Class (UserAgentBrandVersion)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5bd67952550947311c46c7276be4f0642b76503e translatedAt=2026-08-07T04:45:24.830Z pushedAt=2026-08-07T08:11:25.867Z -->

UserAgentBrandVersion is a data class in the ArkWeb framework used to configure the brand name and version number in User-Agent client hints, and is used together with [UserAgentMetadata](./arkts-apis-webview-UserAgentMetadata.md). In the User-Agent Client Hints mechanism, the browser reports brand and version information to the server through request headers such as Sec-CH-UA-Full-Version-List. UserAgentBrandVersion is used to define a single brand entry in it.

UserAgentBrandVersion provides methods for setting and obtaining the brand name and version number: setBrand/getBrand are used to set and obtain the brand name (for example, "ArkWeb"), setMajorVersion/getMajorVersion are used to set and obtain the major version number (for example, "126"), and setFullVersion/getFullVersion are used to set and obtain the full version number (for example, "126.0.0.0"). An app can customize the browser identity information reported by the Web component to the server by modifying these values.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 24. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 24.
>
> - The sample effect is subject to the actual device.

## setBrand

setBrand(brand: string): void

Sets the brand name.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name             | Type   | Mandatory  |  Description|
| ------------------ | ------- | ---- | ------------- |
| brand | string | Yes  | Brand name, which cannot be an empty string.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getBrand

getBrand(): string

Obtains the brand name.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | Brand name string. |

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## setMajorVersion

setMajorVersion(majorVersion: string): void

Sets the major version number.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name             | Type   | Mandatory  |  Description|
| ------------------ | ------- | ---- | ------------- |
| majorVersion | string | Yes  | Major version number, which cannot be an empty string.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getMajorVersion

getMajorVersion(): string

Obtains the major version number.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | Major version number string. |

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
| fullVersion | string | Yes  | Full version number, which cannot be an empty string.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getFullVersion

getFullVersion(): string

Obtains the full version number.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | Full version number string. |

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).