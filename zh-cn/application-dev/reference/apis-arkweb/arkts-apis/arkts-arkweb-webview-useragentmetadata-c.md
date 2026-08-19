# UserAgentMetadata

UserAgentMetadata是ArkWeb框架中用于配置User-Agent Client Hints（UA客户端提示）完整元数据的类。User-Agent Client Hints是一种现代化的HTTP请求标头机制，通过一 组Sec-CH-UA系列标头向服务器报告客户端信息，替代传统User-Agent字符串实现更安全、更细粒度的浏览器身份标识。通过UserAgentMetadata，应用可以自定义Web组件向服务器报告的所有客户端信息字段。

**起始版本：** 24

<!--Device-webview-class UserAgentMetadata--><!--Device-webview-class UserAgentMetadata-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## getArchitecture

```TypeScript
getArchitecture(): string
```

获取平台的架构类型。不调用对应的[setArchitecture](#setarchitecture)设置时，架构类型默认值：""。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getArchitecture(): string--><!--Device-UserAgentMetadata-getArchitecture(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 平台架构类型。 |

## getBitness

```TypeScript
getBitness(): string
```

获取平台的位数类型。不调用对应的[setBitness](#setbitness)设置时，位数类型默认值：Desktop："64"，其他设备：""。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getBitness(): string--><!--Device-UserAgentMetadata-getBitness(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 平台位数。 |

## getBrandVersionList

```TypeScript
getBrandVersionList(): Array<UserAgentBrandVersion>
```

获取品牌和版本信息列表。不调用对应的[setBrandVersionList](#setbrandversionlist)进行设置时，列表默认值： [{"brand":"Chromium","version":[ChromeCompatibleVersion](../../../web/web-default-userAgent.md#默认user-agent结构)}, {"brand":"ArkWeb","version":[OSVersion](../../../web/web-default-userAgent.md#默认user-agent结构)}]。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getBrandVersionList(): Array<UserAgentBrandVersion>--><!--Device-UserAgentMetadata-getBrandVersionList(): Array<UserAgentBrandVersion>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[UserAgentBrandVersion](arkts-arkweb-webview-useragentbrandversion-c.md)&gt; | 品牌和版本信息列表。 |

## getFormFactors

```TypeScript
getFormFactors(): Array<UserAgentFormFactor>
```

获取设备形态信息，如手机、平板等。不调用对应的[setFormFactors](#setformfactors)进行设置时，形态信息默认值：手机："Mobile"、 手表："Watch"、车机："Automotive"、PC："Desktop"、平板："Tablet"。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getFormFactors(): Array<UserAgentFormFactor>--><!--Device-UserAgentMetadata-getFormFactors(): Array<UserAgentFormFactor>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[UserAgentFormFactor](arkts-arkweb-webview-useragentformfactor-e.md)&gt; | 设备形态信息。 |

## getFullVersion

```TypeScript
getFullVersion(): string
```

获取完整版本号。不调用对应的[setFullVersion](#setfullversion)设置时，版本号默认值：""。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getFullVersion(): string--><!--Device-UserAgentMetadata-getFullVersion(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 完整版本号。 |

## getMobile

```TypeScript
getMobile(): boolean
```

获取是否为移动设备。不调用对应的[setMobile](#setmobile)设置时，默认值：手机: true，手表、车机、平板、大屏: false。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getMobile(): boolean--><!--Device-UserAgentMetadata-getMobile(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否为移动设备，true为移动设备，false为不是移动设备。 |

## getModel

```TypeScript
getModel(): string
```

获取设备型号。不调用对应的[setModel](#setmodel)设置时，型号默认值：手机根据const.product.model取设备型号；手表、大屏、车机、 PC、平板：""。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getModel(): string--><!--Device-UserAgentMetadata-getModel(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 设备型号。 |

## getPlatform

```TypeScript
getPlatform(): string
```

获取操作系统名称。不调用对应的[setPlatform](#setplatform)设置时，名称默认值："OpenHarmony" 。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getPlatform(): string--><!--Device-UserAgentMetadata-getPlatform(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 操作系统名称。 |

## getPlatformVersion

```TypeScript
getPlatformVersion(): string
```

获取操作系统版本号。不调用对应的[setPlatformVersion](#setplatformversion)设置时，版本号默认值：按OpenHarmony平台 版本号规则，同const.product.os.dist.version。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getPlatformVersion(): string--><!--Device-UserAgentMetadata-getPlatformVersion(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 操作系统版本号。 |

## getWow64

```TypeScript
getWow64(): boolean
```

获取二进制文件是否是在64位Windows上以32位模式运行。不调用对应的[setWow64](#setwow64)设置时，默认值为false。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-getWow64(): boolean--><!--Device-UserAgentMetadata-getWow64(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示二进制文件是否在64位Windows上以32位模式运行。true为是，false为不是。 |

## setArchitecture

```TypeScript
setArchitecture(arch: string): void
```

设置平台的架构类型。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setArchitecture(arch: string): void--><!--Device-UserAgentMetadata-setArchitecture(arch: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arch | string | 是 | 对应请求标头的Sec-CH-UA-Arch。空代表使用ArkWeb默认值。 |

## setBitness

```TypeScript
setBitness(bitness: string): void
```

设置平台的位数类型。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setBitness(bitness: string): void--><!--Device-UserAgentMetadata-setBitness(bitness: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bitness | string | 是 | 对应请求标头的Sec-CH-UA-Bitness。空代表使用ArkWeb默认值。 |

## setBrandVersionList

```TypeScript
setBrandVersionList(brandVersionList: Array<UserAgentBrandVersion>): void
```

设置品牌和版本信息。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setBrandVersionList(brandVersionList: Array<UserAgentBrandVersion>): void--><!--Device-UserAgentMetadata-setBrandVersionList(brandVersionList: Array<UserAgentBrandVersion>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brandVersionList | Array&lt;[UserAgentBrandVersion](arkts-arkweb-webview-useragentbrandversion-c.md)&gt; | 是 | 对应请求标头的Sec-CH-UA-Full-Version-List。空代表使用ArkWeb默认值。 |

## setFormFactors

```TypeScript
setFormFactors(formFactors: Array<UserAgentFormFactor>): void
```

设置设备形态信息，如手机、平板等。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setFormFactors(formFactors: Array<UserAgentFormFactor>): void--><!--Device-UserAgentMetadata-setFormFactors(formFactors: Array<UserAgentFormFactor>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formFactors | Array&lt;[UserAgentFormFactor](arkts-arkweb-webview-useragentformfactor-e.md)&gt; | 是 | 对应请求标头的Sec-CH-UA-Form-Factor。空代表使用ArkWeb默认值。 |

## setFullVersion

```TypeScript
setFullVersion(fullVersion: string): void
```

设置完整版本号。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setFullVersion(fullVersion: string): void--><!--Device-UserAgentMetadata-setFullVersion(fullVersion: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullVersion | string | 是 | 对应请求标头的Sec-CH-UA-Full-Version。空代表使用ArkWeb默认值。 |

## setMobile

```TypeScript
setMobile(isMobile: boolean): void
```

设置是否为移动设备。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setMobile(isMobile: boolean): void--><!--Device-UserAgentMetadata-setMobile(isMobile: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isMobile | boolean | 是 | 对应请求标头的Sec-CH-UA-Mobile。表示设备是否为移动设备。true为是移动设备，false为不是移动设备。 |

## setModel

```TypeScript
setModel(model: string): void
```

设置设备型号。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setModel(model: string): void--><!--Device-UserAgentMetadata-setModel(model: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| model | string | 是 | 对应请求标头的Sec-CH-UA-Model。 空代表使用ArkWeb默认值。 |

## setPlatform

```TypeScript
setPlatform(platform: string): void
```

设置操作系统名称。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setPlatform(platform: string): void--><!--Device-UserAgentMetadata-setPlatform(platform: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| platform | string | 是 | 对应请求标头的Sec-CH-UA-Platform。空代表使用ArkWeb默认值。 |

## setPlatformVersion

```TypeScript
setPlatformVersion(platformVersion: string): void
```

设置操作系统版本号。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setPlatformVersion(platformVersion: string): void--><!--Device-UserAgentMetadata-setPlatformVersion(platformVersion: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| platformVersion | string | 是 | 对应请求标头的Sec-CH-UA-Platform-Version。空代表使用ArkWeb默认值。 |

## setWow64

```TypeScript
setWow64(isWow64: boolean): void
```

设置二进制文件是否在64位Windows上以32位模式运行。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UserAgentMetadata-setWow64(isWow64: boolean): void--><!--Device-UserAgentMetadata-setWow64(isWow64: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isWow64 | boolean | 是 | 对应请求标头的Sec-CH-UA-WoW64。表示二进制文件是否在64位Windows上以32位模式运行。true为是，false为不是。 |

