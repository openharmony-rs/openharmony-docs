# ScriptItem

Describes the **ScriptItem** object registered with the **Web** component through the [javaScriptOnDocumentStart](arkts-arkweb-web-comp-attribute.md#javascriptondocumentstart) attribute.

@interface ScriptItem [since 11 - 11]

**Since:** 11

**System capability:** SystemCapability.Web.Webview.Core

## script

```TypeScript
script: string
```

JavaScript script to be registered and executed.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## scriptRules

```TypeScript
scriptRules: Array<string>
```

A set of matching rules for allowed sources.

1. To allow URLs from all sources, use the wildcard "*".
2. To perform exact matching, specify the website address, for example, "https://www.example.com".
3. To perform fuzzy matching, use the "*" wildcard, for example, "https://*.example.com".
Patterns such as "x.*.y.com" and "*foobar.com" are not allowed.
4. If the source is an IP address, use rule 2.
5. For protocols other than HTTP/HTTPS (custom protocols), exact matching and fuzzy matching are not supported,
and the rule must end with `://`, for example, "resource://".
6. In a set of scriptRules, if any rule does not meet the above requirements,
the entire set of scriptRules does not take effect.

**Type:** Array&lt;string&gt;

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## urlRegexRules

```TypeScript
urlRegexRules? : Array<UrlRegexRule>
```

Regular expression matching rules for allowed sources. **urlRegexRules** is used for matching only when **scriptRules** is set to **[]**.

**Type:** Array&lt;[UrlRegexRule](arkts-arkweb-urlregexrule-i.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core
