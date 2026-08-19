# AdsBlockManager

This class is used to set adblock config.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-class AdsBlockManager--><!--Device-webview-class AdsBlockManager-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## addAdsBlockAllowedList

```TypeScript
static addAdsBlockAllowedList(domainSuffixes: Array<string>): void
```

Add items to Ads Block Allow list. By default, ads block is allowed for all pages unless they are added to the disallow list. The priority of allowlist is higher than the disallowlist. It is used to re-enable ads block on the page that matches disallow list.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AdsBlockManager-static addAdsBlockAllowedList(domainSuffixes: Array<string>): void--><!--Device-AdsBlockManager-static addAdsBlockAllowedList(domainSuffixes: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainSuffixes | Array&lt;string&gt; | 是 | list of domain suffix, if web page url matches someone in the list, Ads Block will be allowed for the web page. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## addAdsBlockDisallowedList

```TypeScript
static addAdsBlockDisallowedList(domainSuffixes: Array<string>): void
```

Add items to Ads Block Disallow list.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AdsBlockManager-static addAdsBlockDisallowedList(domainSuffixes: Array<string>): void--><!--Device-AdsBlockManager-static addAdsBlockDisallowedList(domainSuffixes: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainSuffixes | Array&lt;string&gt; | 是 | list of domain suffix, if web page url matches someone in the list, Ads Block will be disallowed for the web page. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## clearAdsBlockAllowedList

```TypeScript
static clearAdsBlockAllowedList(): void
```

clear Ads Block Allowed list.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AdsBlockManager-static clearAdsBlockAllowedList(): void--><!--Device-AdsBlockManager-static clearAdsBlockAllowedList(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## clearAdsBlockDisallowedList

```TypeScript
static clearAdsBlockDisallowedList(): void
```

clear Ads Block Disallowed list.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AdsBlockManager-static clearAdsBlockDisallowedList(): void--><!--Device-AdsBlockManager-static clearAdsBlockDisallowedList(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## removeAdsBlockAllowedList

```TypeScript
static removeAdsBlockAllowedList(domainSuffixes: Array<string>): void
```

remove items from Ads Block Allowed list.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AdsBlockManager-static removeAdsBlockAllowedList(domainSuffixes: Array<string>): void--><!--Device-AdsBlockManager-static removeAdsBlockAllowedList(domainSuffixes: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainSuffixes | Array&lt;string&gt; | 是 | list of domain suffix needed be removed from allow list |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## removeAdsBlockDisallowedList

```TypeScript
static removeAdsBlockDisallowedList(domainSuffixes: Array<string>): void
```

remove items from Ads Block Disallowed list.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AdsBlockManager-static removeAdsBlockDisallowedList(domainSuffixes: Array<string>): void--><!--Device-AdsBlockManager-static removeAdsBlockDisallowedList(domainSuffixes: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainSuffixes | Array&lt;string&gt; | 是 | list of domain suffix needed be removed from disallow list |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

## setAdsBlockRules

```TypeScript
static setAdsBlockRules(rulesFile: string, replace: boolean): void
```

set Ads Block ruleset file, containing easylist rules.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AdsBlockManager-static setAdsBlockRules(rulesFile: string, replace: boolean): void--><!--Device-AdsBlockManager-static setAdsBlockRules(rulesFile: string, replace: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rulesFile | string | 是 | absolute file path contains app customized ads block rules. |
| replace | boolean | 是 | (@code true)replace internal rules;(@code false) add to internal rules. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

