# Class (UserAgentBrandVersion)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

This class provides APIs for configuring **UserAgentBrandVersion**.

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
| string | Brand name.|

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
| string | Major version number.|

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
| string | Full version number.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).
