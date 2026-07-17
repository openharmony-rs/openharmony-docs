# UserAgentBrandVersion

Class that holds brand name, major version and full version. Brand name and major version used to generated User-Agent client hints sec-cu-ua. Brand name and full version used to generated user-agent client hint sec-ch-ua-full-version-list.

**起始版本：** 24

<!--Device-webview-class UserAgentBrandVersion--><!--Device-webview-class UserAgentBrandVersion-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## getBrand

```TypeScript
getBrand(): string
```

Get the brand info.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentBrandVersion-getBrand(): string--><!--Device-UserAgentBrandVersion-getBrand(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - Returns brand info of UserAgentBrandVersion. |

## getFullVersion

```TypeScript
getFullVersion(): string
```

Get the full version.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentBrandVersion-getFullVersion(): string--><!--Device-UserAgentBrandVersion-getFullVersion(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - Returns full version of UserAgentBrandVersion. |

## getMajorVersion

```TypeScript
getMajorVersion(): string
```

Get the major version.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentBrandVersion-getMajorVersion(): string--><!--Device-UserAgentBrandVersion-getMajorVersion(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | - Returns major version of UserAgentBrandVersion. |

## setBrand

```TypeScript
setBrand(brand: string): void
```

Sets the brand. Should not be blank.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentBrandVersion-setBrand(brand: string): void--><!--Device-UserAgentBrandVersion-setBrand(brand: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brand | string | 是 | The brand. |

## setFullVersion

```TypeScript
setFullVersion(fullVersion: string): void
```

Sets the full version. Should not be blank.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentBrandVersion-setFullVersion(fullVersion: string): void--><!--Device-UserAgentBrandVersion-setFullVersion(fullVersion: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullVersion | string | 是 | The full version. |

## setMajorVersion

```TypeScript
setMajorVersion(majorVersion: string): void
```

Sets the major version. Should not be blank.

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentBrandVersion-setMajorVersion(majorVersion: string): void--><!--Device-UserAgentBrandVersion-setMajorVersion(majorVersion: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| majorVersion | string | 是 | The major version. |

