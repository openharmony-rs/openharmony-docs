# AdsBlockManager

This class is used to set adblock config.

**起始版本：** 12

<!--Device-webview-class AdsBlockManager--><!--Device-webview-class AdsBlockManager-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

<a id="addadsblockallowedlist"></a>
## addAdsBlockAllowedList

```TypeScript
static addAdsBlockAllowedList(domainSuffixes: Array<string>): void
```

向AdsBlockManager的AllowedList中添加一组域名，主要用于重新开启DisallowedList中的部分网站的广告过滤。

> **说明：**  
>  
> 此接口设置的域名不会持久化，应用重启需要重新设置。  
>  
> AllowedList的优先级比DisallowedList高，例如，DisallowedList中配置了['example.com']，禁用了所有example.com域名下的网页，此时如果需要开启'  
> news.example.com'下的广告过滤，可以使用addAdsBlockAllowedList(['news.example.com'])。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdsBlockManager-static addAdsBlockAllowedList(domainSuffixes: Array<string>): void--><!--Device-AdsBlockManager-static addAdsBlockAllowedList(domainSuffixes: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainSuffixes | Array&lt;string&gt; | 是 | 一组域名列表，如果网页URL与列表中的某个条目匹配，则该网页将被允许使用广告拦截功能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

<a id="addadsblockdisallowedlist"></a>
## addAdsBlockDisallowedList

```TypeScript
static addAdsBlockDisallowedList(domainSuffixes: Array<string>): void
```

向AdsBlockManager的DisallowedList中添加一组域名。广告过滤功能开启时，将禁用这些网站的广告过滤功能。

> **说明：**  
>  
> 此接口设置的域名不会持久化，应用重启需要重新设置。  
>  
> 广告过滤特性会使用后缀匹配的方式判断domainSuffix和当前站点的url是否能匹配，例如，当前Web组件打开的网站是https://www.example.com，设置的DisallowedList中有'  
> example.com'或者'www.example.com'，后缀匹配成功，此网站将禁用广告过滤，访问'https://m.example.com'也将禁用广告过滤。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdsBlockManager-static addAdsBlockDisallowedList(domainSuffixes: Array<string>): void--><!--Device-AdsBlockManager-static addAdsBlockDisallowedList(domainSuffixes: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainSuffixes | Array&lt;string&gt; | 是 | 一组域名列表，如果网页URL与列表中的某个域名匹配，则该网页将被禁止使用广告拦截功能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

<a id="clearadsblockallowedlist"></a>
## clearAdsBlockAllowedList

```TypeScript
static clearAdsBlockAllowedList(): void
```

clear Ads Block Allowed list.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdsBlockManager-static clearAdsBlockAllowedList(): void--><!--Device-AdsBlockManager-static clearAdsBlockAllowedList(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

<a id="clearadsblockdisallowedlist"></a>
## clearAdsBlockDisallowedList

```TypeScript
static clearAdsBlockDisallowedList(): void
```

clear Ads Block Disallowed list.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdsBlockManager-static clearAdsBlockDisallowedList(): void--><!--Device-AdsBlockManager-static clearAdsBlockDisallowedList(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

<a id="removeadsblockallowedlist"></a>
## removeAdsBlockAllowedList

```TypeScript
static removeAdsBlockAllowedList(domainSuffixes: Array<string>): void
```

从AdsBlockManager的AllowedList中删除一组域名。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdsBlockManager-static removeAdsBlockAllowedList(domainSuffixes: Array<string>): void--><!--Device-AdsBlockManager-static removeAdsBlockAllowedList(domainSuffixes: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainSuffixes | Array&lt;string&gt; | 是 | 需要从允许列表中移除的域名后缀列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

<a id="removeadsblockdisallowedlist"></a>
## removeAdsBlockDisallowedList

```TypeScript
static removeAdsBlockDisallowedList(domainSuffixes: Array<string>): void
```

从AdsBlockManager的DisallowedList中删除一组域名。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdsBlockManager-static removeAdsBlockDisallowedList(domainSuffixes: Array<string>): void--><!--Device-AdsBlockManager-static removeAdsBlockDisallowedList(domainSuffixes: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| domainSuffixes | Array&lt;string&gt; | 是 | 需要从禁止列表中移除的域名后缀列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

<a id="setadsblockrules"></a>
## setAdsBlockRules

```TypeScript
static setAdsBlockRules(rulesFile: string, replace: boolean): void
```

向Web组件中设置自定义的符合通用easylist语法规则的广告过滤配置文件。

> **说明：**  
>  
> 此接口设置的广告过滤规则，内部解析成功后会持久化存储，应用重启后不需要重复设置。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdsBlockManager-static setAdsBlockRules(rulesFile: string, replace: boolean): void--><!--Device-AdsBlockManager-static setAdsBlockRules(rulesFile: string, replace: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rulesFile | string | 是 | 指定了符合easylist通用语法的规则文件路径，应用需要有此文件的读权限。 |
| replace | boolean | 是 | true表示强制替换掉内置的默认规则，false表示设置的自定义规则将与内置规则共同工作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |

