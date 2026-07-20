# UserAgentMetadata

Holds User-Agent metadata information and uses to generate User-Agent client hints.

**起始版本：** 24

<!--Device-webview-class UserAgentMetadata--><!--Device-webview-class UserAgentMetadata-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

<a id="getarchitecture"></a>
## getArchitecture

```TypeScript
getArchitecture(): string
```

Gets the value for sec-ch-ua-architecture.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getArchitecture(): string--><!--Device-UserAgentMetadata-getArchitecture(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - Returns the value for sec-ch-ua-architecture. |

<a id="getbitness"></a>
## getBitness

```TypeScript
getBitness(): string
```

Gets the value for the sec-ch-ua-bitness.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getBitness(): string--><!--Device-UserAgentMetadata-getBitness(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - Returns the value for the sec-ch-ua-bitness. |

<a id="getbrandversionlist"></a>
## getBrandVersionList

```TypeScript
getBrandVersionList(): Array<UserAgentBrandVersion>
```

Returns the current list of UserAgentBrandVersion which are used to generate the User-Agent client hints sec-ch-ua and sec-ch-ua-full-version-list.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getBrandVersionList(): Array<UserAgentBrandVersion>--><!--Device-UserAgentMetadata-getBrandVersionList(): Array<UserAgentBrandVersion>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;UserAgentBrandVersion&gt; | - Returns the current list of UserAgentBrandVersion. |

<a id="getformfactors"></a>
## getFormFactors

```TypeScript
getFormFactors(): Array<UserAgentFormFactor>
```

Gets the value for the sec-ch-ua-form-factors.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getFormFactors(): Array<UserAgentFormFactor>--><!--Device-UserAgentMetadata-getFormFactors(): Array<UserAgentFormFactor>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;UserAgentFormFactor&gt; | - Returns the form factors. |

<a id="getfullversion"></a>
## getFullVersion

```TypeScript
getFullVersion(): string
```

Gets the value for the sec-ch-ua-full-version.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getFullVersion(): string--><!--Device-UserAgentMetadata-getFullVersion(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - Returns the value for the sec-ch-ua-full-version. |

<a id="getmobile"></a>
## getMobile

```TypeScript
getMobile(): boolean
```

Gets the value for the sec-ch-ua-mobile.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getMobile(): boolean--><!--Device-UserAgentMetadata-getMobile(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - Returns the value for the sec-ch-ua-mobile. |

<a id="getmodel"></a>
## getModel

```TypeScript
getModel(): string
```

Gets the value for the sec-ch-ua-model.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getModel(): string--><!--Device-UserAgentMetadata-getModel(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - Returns the value for the sec-ch-ua-model. |

<a id="getplatform"></a>
## getPlatform

```TypeScript
getPlatform(): string
```

Gets the value for the sec-ch-ua-platform.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getPlatform(): string--><!--Device-UserAgentMetadata-getPlatform(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - Returns the value for the sec-ch-ua-platform. |

<a id="getplatformversion"></a>
## getPlatformVersion

```TypeScript
getPlatformVersion(): string
```

Gets the value for the sec-ch-ua-platform-version.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getPlatformVersion(): string--><!--Device-UserAgentMetadata-getPlatformVersion(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - Returns the value for the sec-ch-ua-platform-version. |

<a id="getwow64"></a>
## getWow64

```TypeScript
getWow64(): boolean
```

Gets the value for the sec-ch-ua-wow64.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getWow64(): boolean--><!--Device-UserAgentMetadata-getWow64(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | - Returns the value for the sec-ch-ua-wow64. |

<a id="setarchitecture"></a>
## setArchitecture

```TypeScript
setArchitecture(arch: string): void
```

Sets User-Agent metadata architecture.

<p><strong>API Note</strong>:<br>The default value is empty string which means the system default value will be used.</p>

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setArchitecture(arch: string): void--><!--Device-UserAgentMetadata-setArchitecture(arch: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arch | string | 是 | The arch is used to generate User-Agent client hints sec-ch-ua-architecture. |

<a id="setbitness"></a>
## setBitness

```TypeScript
setBitness(bitness: string): void
```

Sets User-Agent metadata bitness default is "".

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setBitness(bitness: string): void--><!--Device-UserAgentMetadata-setBitness(bitness: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bitness | string | 是 | The bitness is used to generate User-Agent client hints sec-ch-ua-bitness. |

<a id="setbrandversionlist"></a>
## setBrandVersionList

```TypeScript
setBrandVersionList(brandVersionList: Array<UserAgentBrandVersion>): void
```

Sets User-Agent metadata brands and their versions.

<p><strong>API Note</strong>:<br>The default value is an empty list which means the system default User-Agent metadata brands and versions will be used to generate the User-Agent client hints.</p>

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setBrandVersionList(brandVersionList: Array<UserAgentBrandVersion>): void--><!--Device-UserAgentMetadata-setBrandVersionList(brandVersionList: Array<UserAgentBrandVersion>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brandVersionList | Array&lt;UserAgentBrandVersion&gt; | 是 | The brandVersionList is used to generate User-Agent client hints sec-ch-ua-full-version-list. |

<a id="setformfactors"></a>
## setFormFactors

```TypeScript
setFormFactors(formFactors: Array<UserAgentFormFactor>): void
```

Sets User-Agent metadata form factors.

<p><strong>API Note</strong>:<br>The default value is empty list which means the system default value will be used.Form factor value should be one or more of DESKTOP, AUTOMOTIVE, MOBILE, TABLET, XR, EINK, WATCH.</p>

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setFormFactors(formFactors: Array<UserAgentFormFactor>): void--><!--Device-UserAgentMetadata-setFormFactors(formFactors: Array<UserAgentFormFactor>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formFactors | Array&lt;UserAgentFormFactor&gt; | 是 | The formFactors is used to generate User-Agent client hints sec-ch-ua-form-factors. |

<a id="setfullversion"></a>
## setFullVersion

```TypeScript
setFullVersion(fullVersion: string): void
```

Sets User-Agent metadata full version.

<p><strong>API Note</strong>:<br>The default value is empty string which means the system default value will be used.</p>

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setFullVersion(fullVersion: string): void--><!--Device-UserAgentMetadata-setFullVersion(fullVersion: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullVersion | string | 是 | The fullVersion is used to generate User-Agent client hints sec-ch-ua-full-version. |

<a id="setmobile"></a>
## setMobile

```TypeScript
setMobile(isMobile: boolean): void
```

Sets User-Agent metadata mobile, default is true.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setMobile(isMobile: boolean): void--><!--Device-UserAgentMetadata-setMobile(isMobile: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isMobile | boolean | 是 | The isMobile is used to generate User-Agent client hints sec-ch-ua-mobile. |

<a id="setmodel"></a>
## setModel

```TypeScript
setModel(model: string): void
```

Sets User-Agent metadata model.

<p><strong>API Note</strong>:<br>The default value is empty string which means the system default value will be used.</p>

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setModel(model: string): void--><!--Device-UserAgentMetadata-setModel(model: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| model | string | 是 | The model is used to generate User-Agent client hints sec-ch-ua-model. |

<a id="setplatform"></a>
## setPlatform

```TypeScript
setPlatform(platform: string): void
```

Sets User-Agent metadata platform.

<p><strong>API Note</strong>:<br>The default value is empty string which means the system default value will be used.</p>

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setPlatform(platform: string): void--><!--Device-UserAgentMetadata-setPlatform(platform: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| platform | string | 是 | The platform is used to generate User-Agent client hints sec-ch-ua-platform. |

<a id="setplatformversion"></a>
## setPlatformVersion

```TypeScript
setPlatformVersion(platformVersion: string): void
```

Sets User-Agent metadata platform version.

<p><strong>API Note</strong>:<br>The default value is empty string which means the system default value will be used.</p>

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setPlatformVersion(platformVersion: string): void--><!--Device-UserAgentMetadata-setPlatformVersion(platformVersion: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| platformVersion | string | 是 | The platformVersion is used to generate User-Agent client hints sec-ch-ua-platform-version. |

<a id="setwow64"></a>
## setWow64

```TypeScript
setWow64(isWow64: boolean): void
```

Sets User-Agent metadata wow64, default is false.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setWow64(isWow64: boolean): void--><!--Device-UserAgentMetadata-setWow64(isWow64: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isWow64 | boolean | 是 | The wow64 is used to generate User-Agent client hints sec-ch-ua-wow64. |

