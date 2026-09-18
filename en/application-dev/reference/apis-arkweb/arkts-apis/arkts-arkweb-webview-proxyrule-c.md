# ProxyRule

ProxyRule is a class for read-only proxy rule information in the ArkWeb framework, obtained through the [getProxyRules](arkts-arkweb-webview-proxyconfig-c.md#getproxyrules) method. When a developer configures proxy rules through ProxyConfig, the configured rule list can be obtained through getProxyRules, with each rule corresponding to a ProxyRule object used to query the detailed information of the rule.

ProxyRule provides two methods: getSchemeFilter is used to obtain the protocol filter corresponding to the proxy rule (such as MATCH_ALL_SCHEMES, MATCH_HTTP, MATCH_HTTPS, etc.), and getUrl is used to obtain the proxy server URL information specified in the proxy rule. The ProxyRule object is read-only, created by the system when configuring proxy rules, and the app can only query its content but cannot modify it.

**Since:** 15

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## getSchemeFilter

```TypeScript
getSchemeFilter(): ProxySchemeFilter
```

Obtains the **ProxySchemeFilter** information in the proxy rule.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ProxySchemeFilter](arkts-arkweb-webview-proxyschemefilter-e.md) | **ProxySchemeFilter** in the proxy rule. |

## getUrl

```TypeScript
getUrl(): string
```

Obtains the URL specified in the proxy rule.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | URL information of the proxy in the proxy rule. |
