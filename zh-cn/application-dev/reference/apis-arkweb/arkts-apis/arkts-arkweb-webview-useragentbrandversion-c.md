# UserAgentBrandVersion

UserAgentBrandVersion是ArkWeb框架中用于配置User-Agent客户端提示信息中品牌名称和版本号的数据类，配合 [UserAgentMetadata](arkts-arkweb-webview-useragentmetadata-c.md)使用。在User-Agent Client Hints机制中，浏览器通过Sec-CH-UA-Full-Version-List 等请求标头向服务器报告品牌和版本信息，UserAgentBrandVersion用于定义其中的单个品牌条目。 UserAgentBrandVersion提供品牌名称和版本号的设置与获取方法：setBrand/getBrand用于设置和获取品牌名称（如“ArkWeb”等），setMajorVersion/getMajorVersion用于设 置和获取主版本号（如“126”），setFullVersion/getFullVersion用于设置和获取完整版本号（如“126.0.0.0”）。应用可通过修改这些值来定制Web组件向服务器报告的浏览器身份信息。

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

获取品牌名称。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentBrandVersion-getBrand(): string--><!--Device-UserAgentBrandVersion-getBrand(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回品牌名称字符串。 |

## getFullVersion

```TypeScript
getFullVersion(): string
```

获取完整版本号。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentBrandVersion-getFullVersion(): string--><!--Device-UserAgentBrandVersion-getFullVersion(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回完整版本号字符串。 |

## getMajorVersion

```TypeScript
getMajorVersion(): string
```

获取主版本号。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentBrandVersion-getMajorVersion(): string--><!--Device-UserAgentBrandVersion-getMajorVersion(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回主版本号字符串。 |

## setBrand

```TypeScript
setBrand(brand: string): void
```

设置品牌名称。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentBrandVersion-setBrand(brand: string): void--><!--Device-UserAgentBrandVersion-setBrand(brand: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brand | string | 是 | 品牌名称，不能为空字符串。 |

## setFullVersion

```TypeScript
setFullVersion(fullVersion: string): void
```

设置完整版本号。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentBrandVersion-setFullVersion(fullVersion: string): void--><!--Device-UserAgentBrandVersion-setFullVersion(fullVersion: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullVersion | string | 是 | 完整版本号，不能为空字符串。 |

## setMajorVersion

```TypeScript
setMajorVersion(majorVersion: string): void
```

设置主版本号。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentBrandVersion-setMajorVersion(majorVersion: string): void--><!--Device-UserAgentBrandVersion-setMajorVersion(majorVersion: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| majorVersion | string | 是 | 主版本号，不能为空字符串。 |

