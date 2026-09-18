# UserAgentBrandVersion

UserAgentBrandVersion is a data class in the ArkWeb framework used to configure the brand name and version number in User-Agent client hints, and is used together with [UserAgentMetadata](arkts-arkweb-webview-useragentmetadata-c.md). In the User-Agent Client Hints mechanism, the browser reports brand and version information to the server through request headers such as Sec-CH-UA-Full-Version-List. UserAgentBrandVersion is used to define a single brand entry in it.

UserAgentBrandVersion provides methods for setting and obtaining the brand name and version number: setBrand/ getBrand are used to set and obtain the brand name (for example, "ArkWeb"), setMajorVersion/getMajorVersion are used to set and obtain the major version number (for example, "126"), and setFullVersion/getFullVersion are used to set and obtain the full version number (for example, "126.0.0.0"). An app can customize the browser identity information reported by the Web component to the server by modifying these values.

**Since:** 24

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## getBrand

```TypeScript
getBrand(): string
```

Obtains the brand name.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Brand name string. |

## getFullVersion

```TypeScript
getFullVersion(): string
```

Obtains the full version number.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Full version number string. |

## getMajorVersion

```TypeScript
getMajorVersion(): string
```

Obtains the major version number.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Major version number string. |

## setBrand

```TypeScript
setBrand(brand: string): void
```

Sets the brand name.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| brand | string | Yes | Brand name, which cannot be an empty string. |

## setFullVersion

```TypeScript
setFullVersion(fullVersion: string): void
```

Sets the full version number.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fullVersion | string | Yes | Full version number, which cannot be an empty string. |

## setMajorVersion

```TypeScript
setMajorVersion(majorVersion: string): void
```

Sets the major version number.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| majorVersion | string | Yes | Major version number, which cannot be an empty string. |
