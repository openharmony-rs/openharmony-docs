# Class (UserAgentMetadata)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

This class provides APIs for configuring **UserAgentMetadata**.

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

Obtains the brand and version information list.

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

Obtains the architecture type of the platform.

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
| arch | string | Yes  | **Sec-CH-UA-Bitness** of the request header. If this parameter is left empty, the default ArkWeb value is used.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getBitness

getBitness(): string

Obtains the bitness type of the platform.

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

Obtains the device form, such as the mobile phone or tablet.

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

Obtains the full version number.

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
| isMobile | boolean | Yes  | **Sec-CH-UA-Mobile** of the request header. It indicates whether the device is a mobile device. **true** means yes; **false** otherwise. Default value: **true**.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getMobile

getMobile(): boolean

Obtains whether the device is a mobile device.

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
| model | string | Yes  | **Sec-CH-UA-Mobile** of the request header. If this parameter is left empty, the default ArkWeb value is used.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getModel

getModel(): string

It is used to obtain the device model.

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

Obtains the OS name.

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

Obtains the OS version.

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
| isWow64 | boolean | Yes  | **Sec-CH-UA-WoW64** of the request header. Whether the binary file runs in 32-bit mode on a 64-bit Windows. **true** means yes; **false** otherwise. The default value is **false**.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).

## getWow64

getWow64(): boolean

Checks whether the binary file runs in 32-bit mode on a 64-bit Windows.

**System capability**: SystemCapability.Web.Webview.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| boolean | Whether the binary file runs in 32-bit mode on a 64-bit Windows. **true** means yes; **false** otherwise.|

**Example**

For details about the sample code, see [setUserAgentClientHintsEnabled](./arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24).
